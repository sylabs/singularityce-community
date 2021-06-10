# SingularityCE Community Meetings

[![hackmd-github-sync-badge](https://hackmd.io/eEFaLVlbRK2_ZHP9yLz5pA/badge)](https://hackmd.io/eEFaLVlbRK2_ZHP9yLz5pA)

## 2021-05-13 4pm CDT

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