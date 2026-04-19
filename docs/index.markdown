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

