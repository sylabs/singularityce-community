# SingularityCE Community Meetings

[![hackmd-github-sync-badge](https://hackmd.io/eEFaLVlbRK2_ZHP9yLz5pA/badge)](https://hackmd.io/eEFaLVlbRK2_ZHP9yLz5pA)

## 2021-01-06 12 noon EDT

Zoom: https://zoom.us/j/98830550629?pwd=ZENYK0hUUlBoSGZlTUl2WEdEa1FDUT09

**This meeting will be recorded**

1. **Show and Tell** - Running MPI applications with SingularityCE.
2. Library API open-sourcing (Adam Hughes)
3. SingularityCE / Apptainer expected compatibility
4. SingularityCE 3.10 roadmap review
5. Any other business / questions

### Recording

https://youtu.be/jl2cT9gkxwo

### Links

* Gist with MPI examples - https://gist.github.com/dtrudg/a38aaa2396774a5ed82a6d06949625e9
* Library API release - https://github.com/singularityhub/library-api/pull/2 / https://github.com/sylabs/scs-library-client/blob/master/api/server/openapi.yml
* SingularityCE Roadmap - https://github.com/sylabs/singularityce-community/blob/main/roadmap.md

-----

## 2021-12-02 12 noon EDT

Zoom: https://zoom.us/j/98830550629?pwd=ZENYK0hUUlBoSGZlTUl2WEdEa1FDUT09

**This meeting will be recorded**

### Agenda

1. **Show and Tell** - Working across architectures with SingularityCE and binfmt_misc. Will demonstrate building and running ARM64 containers on an AMD64 machine and vice versa.
2. SingularityCE 3.9 release recap
3. SingularityCE community pacakages for EL & Ubuntu
4. Apptainer announcement
5. Any other business / questions

### Recording

https://youtu.be/dDQqkNdvfLo

### Links

* Setup Qemu user-mode emulation with a container - https://github.com/multiarch/qemu-user-static
* Setup Qemu user-mode emulation on Debian - https://wiki.debian.org/QemuUserEmulation
* SingularityCE 3.9.1 with EL & Ubuntu packages - https://github.com/sylabs/singularity/releases/tag/v3.9.1

----

## 2021-11-04 12 noon EDT

*Note time change to 12 noon ET, first Thursday of each month*

Zoom: https://zoom.us/j/98830550629?pwd=ZENYK0hUUlBoSGZlTUl2WEdEa1FDUT09

**This meeting will be recorded**

### Agenda

1. ~~**Show and Tell**~~ - _resuming next month_
2. SingularityCE 3.9 release candidates - Updates on progress toward stable release. Appeal for testing.
3. Roadmap review - 3.10 vs 4.0 for the next release.
4. Any other business / questions

### Recording

https://youtu.be/sVfXbynD81o

### Links

* Changelog for items during RC: https://github.com/sylabs/singularity/blob/master/CHANGELOG.md
* 3.9.0 release milestone: https://github.com/sylabs/singularity/milestone/2

-----

## 2021-10-07 5pm EDT

Zoom: https://zoom.us/j/98830550629?pwd=ZENYK0hUUlBoSGZlTUl2WEdEa1FDUT09

**This meeting will be recorded**

### Agenda

1. **Show and Tell** (Dave Trudgian) - New features coming to SingularityCE 3.9 <https://github.com/sylabs/singularity/blob/master/CHANGELOG.md>.
2. Go version support (Adam Hughes) - Impact of Go release lifecycle on dependencies, and compatibility with distribution Go packages.
3. SIF v2 (Adam Hughes) - Reproducible builds.
4. Roadmap review / development updates.
5. Any other business / questions

### Recording

https://youtu.be/8e4exA_D8Zc

### Links

* Upcoming 3.9 changes: https://github.com/sylabs/singularity/blob/master/CHANGELOG.md
* Userdocs current master: https://315-364269136-gh.circle-artifacts.com/0/html/index.html
* Admindocs current master: https://231-364269222-gh.circle-artifacts.com/0/html/index.html
* Go version support issue: https://github.com/sylabs/singularity/issues/345
* Named volumes issue: https://github.com/sylabs/singularity/issues/353 
* Roadmap document: https://github.com/sylabs/singularityce-community/blob/main/roadmap.md

## 2021-09-02 9am EDT

Zoom: https://zoom.us/j/98830550629?pwd=ZENYK0hUUlBoSGZlTUl2WEdEa1FDUT09

**This meeting will be recorded**

### Agenda

1. **Show and Tell** (Heinz Axelsson-Ekker) - Demonstration of Hinkskalle, an open-source SIF container registry that implements the library:// protocol. <https://github.com/csf-ngs/hinkskalle>.
2. SingularityCE development update (Dave Trudgian) - Report back on 3.8.2 release. Update on development progress towards 3.9.
3. SIF v2 (Adam Hughes) - Report back on SIF v2.0.0 and integration with SingularityCE.
4. Any other business / questions

### Recording

https://youtu.be/otmrUFSBI9I


### Links

* Hinkskalle: https://github.com/csf-ngs/hinkskalle
* SingularityCE 3.9.0 Milestone: https://github.com/sylabs/singularity/milestone/2

-----

## 2021-08-05 5pm EDT

Zoom: https://zoom.us/j/98830550629?pwd=ZENYK0hUUlBoSGZlTUl2WEdEa1FDUT09

**This meeting will be recorded**

### Agenda

1. **Show and Tell** (David Trudgian) - Demonstration of a simple tool to scan SIF containers with the Clair container vulnerability scanner. (github.com/dtrudg/clair-singularity).
2. Singularity CE development update (Dave Trudgian) - Report back on 3.8.1 release. Update on recent development work.
3. SIF v2 (Adam Hughes, written report) - Summary of ongoing work on the sylabs/sif package, toward a tidier v2 API, and integration for Singularity 3.9.
4. Any other business / questions

### Recording

https://youtu.be/YbMlfqSK02Q

### Links

* Clair container scanner: https://github.com/quay/clair
* clair-singularity: https://github.com/dtrudg/clair-singularity
* SingularityCE 3.9.0 Milestone: https://github.com/sylabs/singularity/milestone/2

### SIF Report (Adam Hughes)

Work on the SIF v2 API continues. Last week, several alpha releases were published as the version 2 API started to stabilize. The API has now stabilized to the point that the first beta release has been cut. From here on, major API changes are not expected, but are still possible. 

The v2 API removes an unmaintained dependency that could not be removed from the v1 API without a breaking change. In addition, the new API is much simpler and flexible, and will form an extensible base for future functionality in Singularity and related projects.

It’s expected that the first stable release of the v2 API will be released in August, and will be incorporated into the Singularity 3.9 release.

The v1 API will continue to see bug fixes and security updates applied for the foreseeable future. New features will be added to the V2 API, and all users are encouraged to upgrade once the first stable release is available.

-----

## 2021-07-01 9am EDT

Zoom: https://zoom.us/j/98830550629?pwd=ZENYK0hUUlBoSGZlTUl2WEdEa1FDUT09

**This meeting will be recorded**

### Agenda

1. **Show and tell** (Adrian Wobito) - Adrian will present a remote builder VSCode extension, that provides def file validation, submission and monitoring of remote builds.
2. SingularityCE development update (Dave Trudgian) - Update r.e. recent development work and status of 3.8 and master branch. Report back on the 3.7.4 security release. 
3. SIF v2 (Adam Hughes) - Summary of ongoing work toward a v2 version of the SIF (Singularity Image Format) package, to present a tidier API and allow for further feature development.
4. SingularityCE roadmap (All) - Review the SingularityCE roadmap and discuss priorities, with a view to assigning tasks for the next two milestones.
5. Any other business / questions.

### Recording

https://youtu.be/2s9M8wdAYrg

----

## 2021-05-13 5pm EDT

Zoom: https://zoom.us/j/98151144639?pwd=MENmeXkrWkx0RGdnVHJDU2dtZkZtZz09

**This meeting will be recorded**

### Agenda

1. Welcome / Background (*Jason Tuschen*)
  What's happened, where next?
2. Community Introductions (*All*)
  Quick chance for people  to introduce themselves, and their use of / involvement in Singularity. (Dependent on number of attendees).
3. Questions about SingularityCE (All)
  Opportunity for open questions about the fork, project, etc.
4. Release 3.8 (*David Trudgian*)
  Update on progress toward the SingularityCE 3.8 release.
5. Roadmap & Appeal for Ideas!

-----

### Recording

YouTube: https://youtu.be/Uq0xz-0C6kE

### In Attendance

* David Trudgian
* Jason Tuschen
* Adam Hughes
* Adreain Wobito
* Edward Kornkven
* jason
* JG
* Justin
* Mike Frisch
* Nathan Weeks
* Vanessa Sochat

### Summary / Minutes

#### 1. Welcome / Background (*Jason Tuschen*)

Video - 00:30

Jason is Sylabs CEO since April 2020. Gave an introduction to himself, and his naval and tech background, and the nature of the fork to SingularityCE. 

Emphasis that the fork is based on a firm belief that progress happens with very open communication and fresh perspectives. It's not a battle between two companies, and there isn't ill-will. There is a difference between the broad focus of HPCng and the specific focus of Sylabs on SingularityCE. We remain committed to doing the day-to-day work to minimize disruption, keep things stable, while trying to engage more people in the project.


#### 2. Community Introductions (*All*)

Video - 09:30

Brief introductions were given by people who had joined the call.

#### 3. Questions about SingularityCE (All)

*This is a brief summarization... please see the video for more detail*

Video - 18:45

VS asked how users know which one to install now there are two versions of singularity each side of the fork?

DT mentioned there are naming concerns and technical / compatibility concerns that have been raised. With regard to the name, SingularityCE - we are differentiating with the suffix and it's important to note that SingularityCE is a runtime that runs Singularity containers, in the Singularity Image Format. The code has not diverged, 3.8.0 RC is out, and release comes shortly. We expect a 3.8.0 from HPCng to come out, and be entirely compatible. Not our intention to make large incompatible changes etc. that force people to 'pick a side' quickly. With the established release schedule that would likely mean there are 6 months where people can use the release from either side of the fork without issue. Our commercial product also based around long term support / compatibility. Onus is on us (Sylabs) to engage with people and decide with the community what makes sense in future versions.

EK asked about release schedule, when to expect new versions.

DT mentioned that we have recently stuck to twice a year releases, May & November. Expect to follow this. 3.8 release shortly. 3.9 release in November. Further 3.x or 4.0 release depends on features developed, which we want to decide in conjunction with user community. Compatibility needs more thought toward a 4.0 major versions.

VS asked about how Sylabs has been engaging with what it considers the user base over these past couple of years, who they are, how we re-engage etc.

DT discussed that we talk to both customers of our PRO product and open source users. The mix of users is similar - academic, national labs, large HPC centers. We've probably spoken more directly to our PRO customers, and the outcome hasn't been visible enough. As project has matured and satisfies more needs it can be more difficult to get input around next broadly useful features. We want to make the roadmap etc. more open, reach more open source users and ask for help in finding places to engage.

VS suggested outreach is essential, users may have lost trust and might not come back into discussion themselves. People have a lot to say when asked, but don't jump onto the mailing list, Slack etc. Alternatives e.g. podman are attractive to large centers. OCI is important.

AH talked about how the people writing the code have been less engaged with the community. Sylabs is making a firm commitment to get back to being more engaged with the userbase. It's essential to us as a company with a commercial product based on the open source project. OCI has gotten more important, more complex landscape for containers in HPC. Hoping this is the first step to re-build engagement, charting path for Singularity in an OCI world.

VS raised that when the project was more vibrant there wasn't as much structure, no community call etc. Currently more top down approaches trying to bring back what was present when the project was bottom up. Used to be really fun, which is missed and an important incentive to be involved.

DT talked about spaces of projects that Singularity is often used with (package managers, workflow tools), and wondered about joining these, and how to become involved. Asked for ideas.

VS emphasized showing up to OCI / standards calls etc.




#### 4. Release 3.8 (*David Trudgian*)

Release candidate SingularityCE 3.8.0 RC1 has been released. The stable release is anticipated May 25th.

#### 5. Roadmap & Appeal for Ideas

A roadmap document has been made available at: https://hackmd.io/STKv0EPDRHSHEgFSZe9fxw

Sylabs has put various wish list items into broad categories to start discussion. We want people to comment, and add their own feature requests and ideas. Noted that VS had already contributed some thoughts on docker/OCI compat.

The 3.x items are not yet assigned to specific versions. 3.9 in 6 months is expected, but further 3.x or a jump to 4.0 depends on nature of features, and how the forks develop.


### Actions

* Outreach to standards groups and communities who use Singularity. Suggested examples included OCI, Spack, Easybuild, SnakeMake, Nextflow, and similar.