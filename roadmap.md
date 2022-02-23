# SingularityCE Roadmap

[![hackmd-github-sync-badge](https://hackmd.io/STKv0EPDRHSHEgFSZe9fxw/badge)](https://hackmd.io/STKv0EPDRHSHEgFSZe9fxw)

- [Introduction](#Introduction)
- [Development Cycle](#Development-Cycle)
- [3.10 Features](#3.10-Features)
- [3.11 Features](#3.11-Features)
- [4.0 Features](#4.0-Features)
- [Under Consideration](#Under-Consideration) 
- [Archived Roadmap](#Archived-Roadmap)

## Introduction

This is the roadmap document for SingularityCE (https://github.com/sylabs/singularity). 

SingularityCE was created in May 2021 as a fork from the (then) hpcng/singularity repository, which has in turn forked to become Apptainer. SingularityCE remains an open source project under the BSD license. [Sylabs](https://sylabs.io/singularity) continues to carry out the majority of Singularity development work and acts as project maintainer, with a strong committment to involving and growing the community of open source users and contributors.

The first SingularityCE release was 3.8.0, on May 26th 2021.

The current SingularityCE release is 3.9.5, on Feb 4th 2021.

This roadmap is regularly curated by Sylabs, but is open for edits by anyone! You can [create feature request issues](https://https://github.com/sylabs/singularity/issues/new?assignees=&labels=enhancement&template=feature_request.md&title=) on the GitHub repository, or comment/edit the document here (use the HackMD button).

When feature requests are fleshed out, and it's agreed which version is a good target, we'll make sure this document matches up with GitHub milestones that help to track the development process.

Please aim for around a paragraph per feature if you add things here. Enough detail to understand what the item is, and how it'd be useful. Longer form discussion and work-up should be on GitHub issues, which can be linked here.

## Development Cycle

SingularityCE continues to use a 6-month release cycle for minor/major version bumps. We aim to release in *May* and *November*.

**Sylabs disclosure** - Sylabs takes each November release of SingularityCE as the basis of a commercial long-term supported SingularityPRO release. This does have some impact on decisions around the SingularityCE release timelines, but we hope that you will agree that it allows us to sustainably make valuable contributions to the project. Also, any fixes resulting from QA performed as part of this work are incoporated into SingularityCE for the benefit of the open source community.

# Background Information / References

Background information covering the OCI / SIF work in SingularityCE 3.10 -> 4.0 was posted to the SingularityCE Google Group, and at <https://sylabs.io/2022/02/singularityce-4-0-and-beyond>.

## 3.10 Features

SingularityCE 3.10 is under development for release in May 2022. The following roadmap items are currently scheduled to be included.

* ~~**SystemD as cgroups manager**~~
https://github.com/sylabs/singularity/issues/299
~~systemd is the default init for all of our target distributions, and with cgroups v2 it would be useful to use it for cgroups management. This would allow cgroups applied to containers to fit neatly into the user slice / session scopes in the systemd managed v2 hierarchy.~~ Support merged.

* **Rootless cgroups v2 resource limits**
https://github.com/sylabs/singularity/issues/300
The cgroups v2 hierarchy supports delegation, and management via systemd. This can be used to implement cgroups resource limits without root permissions being required. Will benefit use of Singularity outside of a traditional batch scheduler. E.g. workflow software will be able to enforce limits directly for singularity execution of containers.

* **Replace OCI engine with runc**
Retire SingularityCE's own OCI runtime implementation, and incorporate `runc`. Initially wire up `runc` for relevant `singularity oci` commands only. Essentially, SingularityCE will perform a mount from SIF and initial spec (config.json) creating. Other portions of the oci lifecycle will then be implemented via runc. 

  This is the first step of the work discussed in the [SingularityCE 4.0 and Beyond article].

* **Correct cgroup namespace support for OCI commangs**
https://github.com/sylabs/singularity/issues/298
Fix creation of the cgroup namespace that is permitted via OCI config in the OCI runtime. This will now be achieved via OCI runtime replacement.

* **Begin Removal of Code Supporting Legacy Distros**
https://github.com/sylabs/singularity/issues/82
SingulartyCE contains various workarounds for the RHEL6 / 2.6 kernel, old versions of invoked external programs etc. Special cases supporting these distributions can be removed gradually through 3.10 and beyond. This will reduce code and testing complexity.

* **Fully OCI/Docker compatible arg and env handling - optional config**
https://github.com/sylabs/singularity/issues/487
Due to legacy design and implementation choices dating to Singularity 2.x, SingularityCE interprets arguments to `singularity run` differently from docker and other runtimes, performing a single level of shell evaluation. This causes some compatibility issues. In addition, environment variables perform evaluation.

  We cannot modify this behaviour trivially to match docker, as various users exploit the current situation to blur the lines between host and container environments. We should implement a new mode that can be explicitly enabled to match the Docker / OCI behaviour exactly. This may then become the default in future versions.
  
* **Rework fakeroot engine for nvccli compatibility**
The hybrid fakeroot workflow creates / enters namespaces and performs container setup in an order that is not compatible with using the `nvidia-container-cli` binary for NVIDIA GPU setup. Rework the engine to permit this. May include removing Singularity's own subuid/gid mapping setup, to depend on the standard `newuidmap` / `newgidmap` tooling employed by other rootless runtimes, and SingularityCE in no-setuid mode.


## 3.11 Features

SingularityCE 3.11 is targeted for release in November 2022.

* **Monitor CDI / Intermediate nvidia library GPU setup support**
NVIDIA's GPU library support for containers is moving toward the upcoming CDI (container device interface) standard. There may be an intermediate strategy with a revised `nvidia-container-cli`. Track these changes to support current generations of NVIDIA container setup libraries / utilities.

* **Continue Removal of Code Supporting Legacy Distros**
https://github.com/sylabs/singularity/issues/82
SingulartyCE contains various workarounds for RHEL6 / 2.6 kernel, old versions of invoked external programs etc. Special cases supporting these distributions can be removed gradually through 3.10 and beyond. This will reduce code and testing complexity.

* **Support for Dockerfile USER**
https://github.com/sylabs/singularity/issues/77
SingularityCE has a 'fakeroot engine' that is able to configure a container run so that subuid/subgid configuration is used. This type of functionality opens the possibiity of carrying through `USER` specifications from Docker containers, so that their payload can run as the expected username.

  *Updated* - this will now be addressed via native OCI image execution.

* **Experimental support for run/shell/exec of native OCI containers via OCI engine**
Support execution of OCI images, in OCI native on-disk format, via runc OCI engine - but with the familiar Singularity CLI.

  Target support for the following subset of options/flags in 3.11.
  * `--fakeroot`
  * Bind mounts
  * Namespace requests
  * `--env / --envfile / SINGULARITYENV_`
  * `--apply-cgroups`
  * `--rocm / --nv` (binding method)

  No handling of `--network`, `--security` options etc.

* **Unprivileged SquashFS mount from SIF**
Mount of singularity SquashFS SIF containers should be possible without privilige.

## 4.0 Features

SingularityCE 4.0 is targeted for release in November 2022.

* **SIF Encapsulated OCI Images**
Support encapsulation of native OCI data and configs in SIF. This will permit native OCI containers (not a translation to singularity images) to benefit from the performance (metadata) and portability advantages of the SIF single file format.
  * Pull from OCI sources into OCI-SIF.
  * Push / Pull of these OCI-SIFs for library and oras destinations.
  * Execution of OCI-SIFs with OCI engine.

* **Mainstream execution of native singularity images through OCI runtime**
Cover remaining `run/shell/exec` flags/features that would make it practical for majority of users to switch between singularity's native runtime, and the OCI runtime, for execution of native singularity images (not encapsulated OCI).

* **Consider Reworking the `remote` Command**
https://github.com/sylabs/singularity/issues/78
The `remote` command configures access to Sylabs cloud services, alternative keyservers, and OCI registries. It is complex as there is overlap between these targets, a concept of priorities and global/exclusive keyservers etc. This is likely a good area for a comprehensive rework.

* **Consider Overhaul of the `key` command**
https://github.com/sylabs/singularity/issues/79
The implementation of the `key` command has some significant technical debt, with portions of code at a different level than they should be. In addition, management of keys is not trivial for those not clear about the public/private nature, fingerprints etc. of GPG. More expressive CLI output, and re-examining of the verbs and flags would be useful.

* **Complete Removal of Code Supporting Legacy Distros**
https://github.com/sylabs/singularity/issues/82
SingulartyCE contains various workarounds for RHEL6 / 2.6 kernel, old versions of invoked external programs etc. Special cases supporting these distributions can be removed gradually through 3.10 and beyond. This will reduce code and testing complexity.

* **internal vs pkg**
https://github.com/sylabs/singularity/issues/80
Various portions of code in public `pkg/` areas still use `internal/` packages. This should be worked out so that it is possible to have...

* **Go Module Conformance**
https://github.com/sylabs/singularity/issues/81
A major version offers an opportunity to revise the versioning approach, so that SingularityCE `pkg/` code can be called from other projects as expected of a go module.

* **Transition to `nvidia-container-cli` as preferred GPU setup method**
Perform GPU setup in containers using the `--nvccli` approach by default, if `nvidia-container-cli ` is available, using legacy binding as a fall-back or explicit config option. Requires fakeroot support above.

  This task was previously assigned for 3.10, but has been postponed to allow tracking changes to NVIDIA's projects, and adoption of CDI (container device interface). We will monitor the situation and time the transition in order that we can capture benefits, without repeated disruptive behavior / configuration changes.

## Under Consideration

These are features that might be nice to have, but perhaps aren't urgent to assign to the roadmap. Perhaps more investigation is needed, or it's not known whether there is a broad need for them yet.

* **SR-IOV Networking Support**
https://github.com/sylabs/singularity/issues/83
Common server Ethernet and IB cards support SR-IOV, where they can present multiple 'PCIe virtual functions' that act as independent network devices but share the same hardware. E.g. my Mellanox ConnectX3-PRO can be configured so that it presents as 16 network devices per port. This is often used to share a card between multiple VMs. Containers may also benefit from networking being shared at this layer, for general performance reasons and container-specific native IB support. See https://github.com/Mellanox/docker-sriov-plugin and subsequent CNI direction.

* **Build from Dockerfile**
https://github.com/sylabs/singularity/issues/84
To go along with the "Docker-like" mode above, I've (@vsoch) received a lot of feedback that "Docker" (or more formally, OCI) is the standard, and Singularity is hard to use because it doesn't make it easy to follow that. E.g., what about Singularity being able to build from a Dockerfile (with a limited subset of functionality for anything in a Singularity recipe that doesn't map to a Docker directive) so the user doesn't need to re-write recipes? 

* **Better / emphasize ORAS support**
*@dtrudg note - haven't transferred this to an issue yet, as I think some of the HPC-Containers OCI discussion might help scope it a bit more first?*
People have also expressed liking layers, but I (@vsoch) don't personally think this maps well to Singularity - the single SIF binary is really beneficial in many cases and part of the Singularity design. But in terms of registries, I think more work should be done to make it easy to push a Singularity container to say, an OCI registry. E.g., if/when OCI can add additional content types via the image manifest or artifacts spec, this could be a possibility. It would be really nice to have an OCI registry that can have Singularity containers, however we get there. I don't think Singularity (long term) can be competitive with new technologies like Podman if it's always implementing it's own formats, etc.

* **Expose cgroups namespace as an option for native singularity runtimes**
The cgroups namespace will be addressed for the OCI runtime in 3.10. Consider allowing it to be requested for the native singularity runtime.

* **Non-root / Default Security Profiles**
https://github.com/sylabs/singularity/issues/74
SingularityCE can apply security restrictions, such as `selinux` rules, `seccomp` filters via a `--security` flag. However, this only works for `root`. Since SingularityCE focuses on non-root execution, it would be useful for optional/mandatory profiles to be applied to container runs for non-root users. This would allow security restrictions beyond the usual POSIX permissions to be mandated for container execution. Consider:
  * Selinux
  * Apparmor
  * Seccomp

  *Note* - this is distinct from rootless cgroups v2 limits. The default profiles would be put in place by privileged code, in the same manner as 'blessed' CNI configurations.

  This may be re-scoped to part of the OCI runtime integration for native / SIF encapsulated OCI containers. It is questinable how many people will make use of it with the native singularity runtime engine.

* **Mellanox IB/OFED Library Discovery & Binding**
https://github.com/sylabs/singularity/issues/76
When running a multi-node application that uses Infiniband networking, the user is currently responsible for making sure that required libraries are present in the container, or bound in from the host. We should be able to discover the required libraries on the host, for automatic bind-in when the container distribution is compatible. *Not yet assigned to a release milestone*

## Archived Roadmap

Features implemented in previous releases.

### 3.9 Features

SingularityCE 3.9 was released in November 2021. The historic roadmap items that were included in 3.9 are below. Other smaller changes are reflected in the [CHANGELOG.md](https://github.com/sylabs/singularity/blob/master/CHANGELOG.md) for the project

* ~~**NVIDIA GPU / CUDA support via upstream tooling**
https://github.com/sylabs/singularity/issues/73
SingularityCE uses its own code to bind basic NVIDIA driver/CUDA libraries into a running container. This works well, but does not support features such as GPU masking, MIG awareness, that users of docker and the nvidia docker runtime have become accustomed to. It's proposed to switch to libnvidia-container for GPU setup to support these features, with the existing pathway as a fall-back.~~ *Experimental addition for 3.9 merged to master.*


* ~~**'Docker-like' mode**
https://github.com/sylabs/singularity/issues/75
By default, SingularityCE runs containers far less isolated from the host than Docker - relying on system restrictions on the user. This is very convenient for traditional HPC-like jobs, but some Docker containers can have conflicts with files and other things that enter the container from the host. We have a number of flags such as `--contain` to work around this, but it's often unclear which are needed. A shortcut to apply the most 'docker-like', but practical configuration would be useful.~~ *`--compat` flag merged to master for 3.9*


* ~~**`--mount` Option (Initial Bind Support)**
https://github.com/sylabs/singularity/issues/118
It is not possible to use a ':' or ',' in a bind path via `-B` etc. Providing an escaping mechanism is a work-around. However, implementing a long-form `--mount` syntax, which is how Docker handles the issue, has compatibility and clarity benefits.~~ *Included for 3.9*

* ~~**Unify external binary finding**
https://github.com/sylabs/singularity/issues/178
We use various external binaries, and it's not always obvious how we find then. Some can be explicitly specified in `singularity.conf`, some cannot. This causes special problems for systems managed with a minimal base, and even common tools provided through module / Nix / Guix / Conda environments. System administrators in restrictive environment may also want to ensure *every* host binary called by SingularityCE can be enforced to be a specified exectuable.~~ *Merged to master for 3.9*

* ~~**cgroups v2 support**
https://github.com/sylabs/singularity/issues/60
Provide initial support for cgroups v2 unified hierarchy.~~