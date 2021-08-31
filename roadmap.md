# SingularityCE Roadmap

[![hackmd-github-sync-badge](https://hackmd.io/STKv0EPDRHSHEgFSZe9fxw/badge)](https://hackmd.io/STKv0EPDRHSHEgFSZe9fxw)


This is the roadmap document for SingularityCE (https://github.com/sylabs/singularity). SingularityCE was created in May 2021 as a fork. The first SingularityCE release was 3.8.0, on May 26th 2021.

As of May 12th Sylabs has filled in some of our wishlist items for the next versions of SingularityCE, but we need your input. We'd like more of this document to have been written by you, than us!

You can [create feature request issues](https://https://github.com/sylabs/singularity/issues/new?assignees=&labels=enhancement&template=feature_request.md&title=) on the GitHub repository, or comment/edit here.

When feature requests are fleshed out, and it's agreed which version is a good target, we'll make sure this document matches up with GitHub milestones that help to track the development process.

Please aim for around a paragraph per feature if you add things here. Enough detail to understand what the item is, and how it'd be useful. Longer form discussion and work-up should be on GitHub issues, which can be linked here.

## Development Cycle

At least in the near future, SingularityCE will continue to have a 6-month release cycle for minor/major version bumps. We aim to release in May and November.

*Sylabs disclosure* - Sylabs sells a long term supported commercial version, SingularityPRO, which is released annually from every other version of SingularityCE. This does have some impact on decisions around the SingularityCE release timelines, but we hope that you will agree that it allows us to sustainably make valuable contributions to the project.

## 3.x Features

The following features *would be suitable* for a future 3.x minor version of SingularityCE. These are not yet assigned to specific versions. We'd like your thoughts on how these might fit into a 3.9 / 3.10.... etc. They could also move to a 4.0 or later.

We're thinking that a 3.9 release in November 2021 is definite, but a 3.10 might be contigent on what's planned for 4.0.

* ~~**NVIDIA GPU / CUDA support via upstream tooling**
https://github.com/sylabs/singularity/issues/73
SingularityCE uses its own code to bind basic NVIDIA driver/CUDA libraries into a running container. This works well, but does not support features such as GPU masking, MIG awareness, that users of docker and the nvidia docker runtime have become accustomed to. It's proposed to switch to libnvidia-container for GPU setup to support these features, with the existing pathway as a fall-back.~~ *Experimental addition for 3.9 merged to master.*

* **Non-root / Default Security Profiles**
https://github.com/sylabs/singularity/issues/74
SingularityCE can apply security restrictions, such as `selinux` rules, `seccomp` filters via a `--security` flag. However, this only works for `root`. Since SingularityCE focuse on non-root execution, it would be useful for optional/mandatory profiles to be applied to container runs for non-root users. This would allow security restrictions beyond the usual POSIX permissions to be mandated for container execution. Consider:
  * Selinux
  * Apparmor
  * Seccomp

* ~~**'Docker-like' mode**
https://github.com/sylabs/singularity/issues/75
By default, SingularityCE runs containers far less isolated from the host than Docker - relying on system restrictions on the user. This is very convenient for traditional HPC-like jobs, but some Docker containers can have conflicts with files and other things that enter the container from the host. We have a number of flags such as `--contain` to work around this, but it's often unclear which are needed. A shortcut to apply the most 'docker-like', but practical configuration would be useful.~~ *`--compat` flag merged to master for 3.9*

* **Mellanox IB/OFED Library Discovery & Binding**
https://github.com/sylabs/singularity/issues/76
When running a multi-node application that uses Infiniband networking, the user is currently responsible for making sure that required libraries are present in the container, or bound in from the host. We should be able to discover the required libraries on the host, for automatic bind-in when the container distribution is compatible.

* **Completely unprivileged mode with unprivileged fuse mounts**
Modern linux kernels allow unprivileged fuse mounts and we should take advantage of that to avoid the need for setuid-root when possible.  In particular, the privileged mount of SIF images has long been challenged as being potentially insecure. Use squashfuse for that when possible (while allowing a system adminstrator to switch back to setuid-root mount via configuration).  In addition, use fuse-overlayfs for features such as ``--overlay`` that require overlayfs, when possible. 

* **`--mount` Option (Initial Bind Support)**
https://github.com/sylabs/singularity/issues/118
It is not possible to use a ':' or ',' in a bind path via `-B` etc. Providing an escaping mechanism is a work-around. However, implementing a long-form `--mount` syntax, which is how Docker handles the issue, has compatibility and clarity benefits.

* ~~**Unify external binary finding**
https://github.com/sylabs/singularity/issues/178
We use various external binaries, and it's not always obvious how we find then. Some can be explicitly specified in `singularity.conf`, some cannot. This causes special problems for systems managed with a minimal base, and even common tools provided through module / Nix / Guix / Conda environments. System administrators in restrictive environment may also want to ensure *every* host binary called by SingularityCE can be enforced to be a specified exectuable.~~ *Merged to master for 3.9*


## 4.0 Features

Singularity 4.0 is the place for any features that would need a modified/new image format, where there would be unavoidable changes to the CLI etc., or that have a broad scope.

* **Support for Dockerfile USER**
https://github.com/sylabs/singularity/issues/77
SingularityCE has a 'fakeroot engine' that is able to configure a container run so that subuid/subgid configuration is used. This type of functionality opens the possibiity of carrying through `USER` specifications from Docker containers, so that their payload can run as the expected username.

* **Consider Reworking the `remote` Command**
https://github.com/sylabs/singularity/issues/78
The `remote` command configures access to Sylabs cloud services, alternative keyservers, and OCI registries. It is complex as there is overlap between these targets, a concept of priorities and global/exclusive keyservers etc. This is likely a good area for a comprehensive rework.

* **Overhaul `key` command**
https://github.com/sylabs/singularity/issues/79
The implementation of the `key` command has some significant technical debt, with portions of code at a different level than they should be. In addition, management of keys is not trivial for those not clear about the public/private nature, fingerprints etc. of GPG. More expressive CLI output, and re-examining of the verbs and flags would be useful.

* **internal vs pkg**
https://github.com/sylabs/singularity/issues/80
Various portions of code in public `pkg/` areas still use `internal/` packages. This should be worked out so that it is possible to have...

* **Go Module Conformance**
https://github.com/sylabs/singularity/issues/81
A major version offers an opportunity to revise the versioning approach, so that SingularityCE `pkg/` code can be called from other projects as expected of a go module.

* **Removal of Code Supporting Legacy Distros**
https://github.com/sylabs/singularity/issues/82
SingulartyCE contains various workarounds for RHEL6 / 2.6 kernel, old versions of invoked external programs etc. Special cases supporting these distributions can be removed gradually, but 4.0 is a good target to have removed all to simplify maintenance.

## Maybe Nice to Have?

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
