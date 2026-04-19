---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: default
title: Patrick Klose
---

# Professional Self-Assessment

## Introduction

My name is Patrick Klose, and while I am a recent graduate of the Computer Science program at SNHU, the formal academic portion of my journey in the world of software engineering and solutions architecture is only a recent chapter of a story that has spanned 16 years (and counting).
I entered the SNHU CS program in 2022, at which point I had already attained a journeyman certification with national endorsement in the field of instrumentation and controls from the governments of Alberta and Canada, and had spent the preceding 5 years as an on-site embedded systems programmer for the industrial sector.
This gave me a real-world contextual understanding of the importance of concepts that would be expanded on through my formal education: from high-level architectural paradigms like separation of concerns to low-level technical concepts like operational complexity.

As I have progressed through my courses at SNHU, my career progressed in parallel, and at the time of writing this self-assessment, roughly 2 weeks before I will walk the stage in New Hampshire to accept my degree, I currently work as a SCADA Architect, designing, troubleshooting, and guiding the implementation of distributed control and data acquisition systems for a wide variety of clients in diverse economic sectors.
This parallel progression allowed my professional experience to supplement my educational development while my academic growth informed my professional decision-making.
My education and career have not been two isolated parallel timelines but rather have formed a feedback loop of experiential and educational development, with the current product being the version of me that will be walking across the stage.

The specific area where the two intersect most directly is distributed systems architecture.
My professional work in SCADA is, at its core, designing systems where dozens or hundreds of devices spread across wide geographic areas need to talk to each other reliably, even when the infrastructure between them isn't reliable.
My academic work gave me the formal grounding behind why those systems work the way they do and where they break: how you maintain data integrity across distributed state, how you decompose a system into manageable services, how you handle throughput when everything is competing for the same bandwidth, and what happens from a security perspective when all of those components are networked together.
This is the direction my career is pointed, and the artifacts and experiences described in this portfolio reflect that focus.

## Collaborating in a Team Environment

My coursework in software reverse engineering provided an unexpected but foundational perspective on collaboration.
The core exercise of decompiling compiled programs to their assembly-level instructions, reconstructing the original logic, and assessing it for vulnerabilities is fundamentally an exercise in reading and reasoning about another person's work, understanding their intent from their implementation and identifying what they missed.
This is a skill that extends well beyond the academic exercise: in my professional role as a SCADA architect, I routinely inherit systems designed and configured by other engineers, and my ability to trace decisions through an unfamiliar implementation, assess their soundness, and build on or correct them is central to the work.
Collaboration in this context is not limited to co-authoring code on a shared repository: it is the ability to engage productively with work you did not create, in systems you did not design, alongside people whose assumptions you need to reconstruct before you can contribute meaningfully.

## Communicating with Stakeholders

System Analysis and Design was one of the courses that most directly mirrored my professional responsibilities.
The discipline of eliciting requirements from stakeholders, modeling system behavior, and translating between business needs and technical specifications is effectively what I do every day as a SCADA architect.
Clients describe operational problems in their own terms, and my role is to analyze the underlying system, design a solution within the constraints they may not even be aware of, and communicate that design back in language they can act on.
One professional example that illustrates this clearly: I identified a situation where a prospective client's engineering team was using an AI model to compute process setpoints and push them directly to field controllers with no formal development lifecycle, no CVE tracking, and no awareness of IEC 62443 compliance requirements.
Recognizing both the technical risk and my company's potential third-party liability, I had to communicate that concern through the appropriate channel and frame it in terms of business exposure rather than purely technical deficiency.

## Data Structures and Algorithms

The Data Structures and Algorithms course gave me the formal analytical framework for decisions I had previously been making on intuition and platform familiarity.
Complexity analysis, tree traversals, hash structures, and queue implementations became tools I could reason about rather than just use.
This foundation directly informed the design decisions in my capstone project, where I implemented a Merkle tree for data integrity validation and built an in-memory queue spooler to handle throughput constraints.
Both were deliberate structural choices made with an understanding of their computational tradeoffs, not defaults inherited from a framework.
In my professional work, these concepts surface constantly: SCADA systems are fundamentally data flow problems, and every decision about polling intervals, historian storage, or alarm priority handling is a data structures question whether it gets called one or not.

## Software Engineering and Database

CS-250 and DAD-220 covered the two disciplines that most directly map to my capstone work.
CS-250 introduced the formal structure of the software development lifecycle, from requirements gathering through iterative development and testing.
DAD-220 provided the database fundamentals that informed how I think about data persistence and schema design.
In the capstone, the two combined in how I took a monolithic Dash application and decomposed it into containerized services through a deliberate, iterative process, making specific architectural decisions at each stage rather than refactoring all at once.
The existing stack included MongoDB as its persistence layer, and my enhancements built on top of that foundation, adding Nginx as a reverse proxy and Redis for caching and spooler migration, layering infrastructure around the database rather than replacing it.
Professionally, this mirrors how I operate daily, as I am rarely writing code in isolation: I am scoping solutions, designing system architectures, selecting platforms, and in many cases handing off implementation details to other engineers while retaining ownership of the design.

## Security

CS-405 provided the technical foundation for secure coding practices: input validation, buffer overflow prevention, encryption implementation, and the discipline of treating security as a design constraint rather than an afterthought.
CS-370 expanded that perspective to emerging technologies, particularly the integration of AI and machine learning into systems where the consequences of failure are not limited to data loss or downtime.
The client situation described in the stakeholder communication section is equally a security example, and it was the foundation from these two courses that allowed me to recognize it as such.
In SCADA, security is not an abstract concern, as a vulnerability in an industrial control system can mean environmental releases, equipment destruction, or threats to human safety, and that reality has shaped how I evaluate every system I design or assess.


## Artifact Summary

The artifacts in this portfolio are derived from a single system that was enhanced iteratively across three capstone milestones, with each enhancement building on the previous one.
The decision to use one artifact across all three enhancements was intentional: rather than presenting disconnected projects that each demonstrate a skill in isolation, I wanted to show a phased approach to architectural revision and functionality expansion.
This more closely represents the way systems actually evolve in production environments, as the reality of such projects is that they hardly ever take place in ideal conditions and often involve considerations for maintaining live system uptime in conjunction with the implementation of the project.
The portfolio demonstrates how a monolithic application grew into a distributed, multi-tenant, integrity-validated platform through deliberate, additive design decisions.

### Software Engineering and Design

The original application was a monolithic Dash application built during my CS-340 course.
For this enhancement, I decomposed it into a module-based design with clear service boundaries and restructured the deployment from a single machine to a multi-node architecture with services partitioned across independent compute instances.
Security was addressed by design through Nginx for rate limiting, dash-auth for authentication, and Redis to short-circuit attempted IO spiking of MongoDB by caching frequently executed queries.
The deployment target was Oracle Cloud's free tier, which introduced its own set of challenges: missing iptables entries in Canonical's Ubuntu Minimal images, absent troubleshooting tools in the minimal OS, and the platform's behavior of spinning down inactive VMs to reclaim resources.
The largest takeaway from this enhancement was the importance of communication between entities in a distributed system and having the diagnostic tooling available to troubleshoot when that communication breaks down.

### Data Structures and Algorithms

The second enhancement focused on the implementation of a Merkle tree data structure and comparison engine for data integrity validation.
The choice of a Merkle tree was not arbitrary or academic: it was informed by several months of independent research I had been conducting on the topic for a real-world distributed systems project in my professional work.
The capstone gave me an environment to implement and demonstrate the concept independently of that project.
This is one of the clearest examples in the portfolio of the feedback loop between my education and career as research I was doing professionally drove the design of an academic artifact, and the implementation work I did academically deepened my understanding of how the structure would perform in production.
The enhancement also includes a demonstration dashboard that provides a visual walkthrough of the validation process, and the security implications are worth noting: an air-gapped known-good copy of a production database's Merkle tree enables efficient detection of unauthorized data manipulation, similar in concept to MD5 file integrity checks but applied at a much finer resolution to data at rest.

### Databases

The third enhancement added a REST API with multi-tenant MongoDB support.
Each external organization that submits data is isolated to its own database within the MongoDB instance, with API keys mapped to each tenant to enforce that separation.
This enhancement is also where some of the more satisfying debugging happened: the API demo was rejecting valid API keys, and after significant troubleshooting I discovered that BasicAuth was rejecting the request before it ever reached the API key validator, a sequencing issue that was invisible until I traced the request lifecycle through each layer.
I also addressed the Oracle Cloud free-tier VM spin-down problem by adding a system health API endpoint and configuring a cron job on the database VM to hit that endpoint every five minutes, which routes through Nginx and keeps all three VMs active. A little brute-force-y, but effective.

### Summary

Together, these three artifacts trace the evolution of a system from a single-machine monolith to a distributed, secured, integrity-validated, multi-tenant platform.
Each enhancement layered new capability onto the previous one, and each required solving problems that don't show up in a textbook but define what it actually means to build and operate distributed systems.