<!-- image -->

CyberThreatScenari oEnumerati onModel

Speci alSecti onCommemorati ngAPL' s80thAnni versary

<!-- image -->

<!-- image -->

<!-- image -->

<!-- image -->

The Johns Hopkins APL Technical Digest is an unclassified, online technical journal published quarterly by APL. The objective of the publication is to communicate the work performed at the Laboratory to its sponsors and to the scientific and engineering communities, defense establishment, academia, and industry.

## EDITORIAL BOARD

Harry K. Charles Jr., Chair and Editor-in-Chief

Ariel M. Greenberg, Assistant Editor-in-Chief

Miquel D. Antoine

Ra'id S. Awadallah

Benjamin H. Barnum

Joshua B. Broadwater

Constantine (Dean) K. Demetropoulos

David O. Harper

Zaruhi R. Mnatsakanyan

Neil F. Palumbo

Peter P. Pandolfini

William K. Peter

Valoris R. (Reid) Smith

James C. Spall

Robin M. Vaughan

Scott E. Wunsch

## EX OFFICIO

Erin M. Richardson

The Johns Hopkins APL Technical Digest (ISSN 1930-0530) is published quarterly under the auspices of the Johns Hopkins University Applied Physics Laboratory (APL), 11100 Johns Hopkins Road, Laurel, MD 20723-6099.

Requests to be added to the email distribution list announcing each issue should be submitted to TechnicalDigest@jhuapl.edu. Permission to reprint text and/or figures should be requested at http://bit.ly/apl-3sxU2bS.

The following abstracting services currently cover the Johns Hopkins APL Technical Digest : Chemical Abstracts; Current Contents; Science Citation Index; Engineering Village; and the following CSA abstracts: Aerospace and High Technology Database; Aquatic Sciences and Fisheries Abstracts; Computer and Information Systems Abstracts; Electronics and Communications Abstracts; Mechanical and Transportation Engineering Abstracts; Meteorological and Geoastrophysical Abstracts; and Oceanic Abstracts.

Distribution Statement A: Approved for public release; distribution is unlimited.

© 2023 The Johns Hopkins University Applied Physics Laboratory LLC. All Rights Reserved.

## STAFF

Managing Editor: Erin M. Richardson Editorial Support: Christy Malecki and Mark A. Mercready Illustration Support: Gloria J. Crites, Claire E. DeSmit, Brooke R. Hammack, and Robin A. Walker Front Cover Art: Claire E. DeSmit Inside Back Cover Art: Gloria J. Crites Web Publisher: Anne J. Reed Photographers: Craig S. Weiman and Edward G. Whitman Clearance Coordinator: Chad Sillery Production Assistant: SiRod A. Foster

Johns Hopkins APL

## TECHNICAL DIGEST

Volume 37, Number 2

## APL Research and Development

- 134 H4H: An Open Framework for Rapid Human-Machine Teaming Prototype Integration Edgar F. Martinez, Rebecca M. Crockett, and Ian A. Grissom
- 139 A Multidimensional Cyber Threat Scenario Enumeration Model for Resilience Engineering Anurag Dwivedi

## APL 80TH ANNIVERSARY COMMEMORATIVE ARTICLES

- 150 Preface: APL 80th Anniversary Commemorative Articles Jerry A. Krill
- 151 APL's Systems Approach to Becoming a Strategy-Driven Organization

Ronald R. Luman, Timothy J. Galpin, and Jerry A. Krill

- 170 "APL in the Twenty-First Century": A Retrospective on the 1983 Report to the Director Harry K. Charles Jr.
- 180 Technology Visions for APL's Centennial

Akinwale A. Akinpelu, David W. Blodgett, Glenn E. Mitzel, Morgana M. Trexler, Kaushik A. Iyer, William G. Bath, Lynn M. Reggia, David B. Helmer, Ashutosh Dutta, Nancy F. Andersen, and Jerry A. Krill

- 199 APL Identifies Two New Defining Innovations

APL Staff Writers

- 201 APL Achievement Awards and Prizes:The Lab's Top Inventions, Discoveries, and Accomplishments in 2022

APL Staff Writers

E. F. Martinez, R. M. Crockett, and I. A. Grissom

## H4H: An Open Framework for Rapid Human-Machine Teaming Prototype Integration

Edgar F. Martinez, Rebecca M. Crockett, and Ian A. Grissom

## ABSTRACT

Effective human-machine teaming systems are becoming critical to the success of the modern warfighter. However, these systems are traditionally costly to develop because of the complex integration of hardware and software components from disparate organizations and vendors. In response to this challenge, Johns Hopkins University Applied Physics Laboratory (APL) researchers developed the Human-Machine Interfaces for Human-Machine Teaming (H4H) architecture, a platform that simplifies this complex integration. By modularizing components and simplifying interfaces, H4H aims to reduce the overall cost to establish an initial prototype of a system while enabling reuse of the system's components.

## INTRODUCTION

APL develops and evaluates new human-machine teaming (HMT) technologies to augment the modern warfighter and to enable the United States to hold a competitive edge over current and future adversaries. HMT refers to collaboration between humans and complex technologies to achieve a specific goal, and it relies on three equally important elements: the human, the machine, and the interactions between them. Because HMT innovations are often a novel combination of existing technologies, components are frequently rapidly prototyped and integrated so that new ideas can be evaluated before too much time or money is invested in creating a final design. However, improvements to current HMT prototyping practices could lead to even more savings.

In general, developing prototypes reduces costs because there is no concern with future modifications, extensions, or reuse when integrating components. Although this practice makes sense for most

proof-of-concept efforts, HMT prototypes could benefit from these characteristics since many HMT concepts of operations share hardware and software components. Making these components modular and reusable could save costs across multiple prototyping efforts.

Consider the following small-scale concept of operations: a warfighter and an unmanned ground vehicle (UGV), where the vehicle acts as scout that reports nearby threats. The warfighter is equipped with an augmented-reality (AR) display that visualizes the threats detected by the UGV. Today, most prototype development teams would purchase an AR display and a viable UGV after a brief market survey and then integrate these products. However, the initial system components selected may need to be changed. For example, the warfighter's environment may change to terrain that would require using an unmanned aerial vehicle (UAV) instead of a UGV, or perhaps the development team is

asked to switch AR display vendors. In most cases, shortterm time and cost savings will discourage the team from considering these scenarios. As a result, the initial system implementation will be tightly integrated, and any changes will incur reintegration costs.

To avoid these common pitfalls of prototyping, the Human-Machine Interfaces for Human-Machine Teaming (H4H) architecture facilitates component substitution and reuse while adding minimal design and implementation overhead. H4H's ultimate goal is to lower the time and cost required to integrate, modify, and extend HMT prototypes.

## H4H OVERVIEW

H4H prototypes are built as a collection of small components serving distinct purposes. H4H's overall design goals are to ensure that these components can be replaced or updated as needed, to simplify or abstract the interfaces between them, and to enable reliable or semi-reliable transport of data across them. To achieve these goals, H4H uses an open microservices architecture and a publish-subscribe messaging framework built for distributed components communicating over User Datagram Protocol (UDP). The following subsections summarize the concepts and the reasoning behind the decisions that led to the final H4H design.

## Open versus Closed Architectures

System architectures are categorized as open or closed. In a closed system architecture, components are predefined, and their interactions consist of proprietary protocols tailored to those specific components. Designing the interactions between specific components, however, usually leads to a tight coupling between components and makes the system hard to modify or extend. In contrast, open architectures are designed with consideration that existing components will possibly be replaced or new ones introduced in the future. Instead of using proprietary protocols and knowledge of the implementation details of other components, the interactions between an initial set of components in an open architecture will take place through abstract interfaces and standardized protocols. Designing interactions this way enables components to remain loosely coupled and modular. Since HMT technologies are constantly evolving, it is impossible to predefine all the desired components in an HMT system. Therefore, when considering rapid prototypes in the field of human-machine systems, it is essential to consider the use an open architecture to facilitate integration while maintaining modularity for future development.

## Microservices

With modular components, the functionality of one component does not depend on the implementation

details of another component. This separation of logic is the main idea behind the widespread use of microservices architectures. In a microservices architecture, software applications can be decomposed into several loosely coupled single-function components referred to as services. This functional organization enables each individual service to be highly maintainable and easily testable. Additionally, services can be tailored to specific capabilities and to be owned by independent development teams.$^{1}$ Since HMT prototypes often use components developed by different groups, H4H's microservices architecture has the potential to increase the development speed of HMT prototypes. Instead of dwelling on implementation and delivery details, teams will need to agree only on the inputs and outputs of their services. Then, they can work in parallel with minimal interdependencies across components.

## Publish-Subscribe Messaging

Data exchange in HMT systems tends to be event driven. For this reason, H4H uses the publish-subscribe messaging model to create abstract interfaces between components. Publish-subscribe messaging involves channels in which one or more publishers can publish information about an event. When information is published to a channel, all of the channel's subscribers receive the information. In H4H, channels have predefined data types to serve as an abstract interface through which any number of publishers and subscribers (i.e., components) can simultaneously interact. This quality makes extensibility easier because new components need only adhere to the data type of each channel to interact with other components.

## H4H Architecture Applied

As an example, H4H is applied to the concept of operations of the warfighter with an AR headset and a UGV (Figure 1). An adapter service is created and deployed for each external hardware component (UGV and AR display). In this context, an adapter service is essentially software that acts as an interface between an external component and an internal data channel. Adapter services are therefore tightly coupled to their respective hardware but not to any other service. The threat detection service is also decoupled from all hardware. It consumes the data from the UGV adapter through the sensor data channel and provides the AR display service with data through the threat alert channel. As a result, if the UGV needed to be swapped for a UAV, then a UAV adapter would replace the UGV adapter and no other services would need to be modified. Similarly, if the AR display's vendor changed, then only the AR display adapter would need to be changed. This approach isolates the impact of changes to a single cohesive module, which simplifies the development and

expedites the integration of a new component. The use of publish-subscribe channels also adds the ability to seamlessly scale the system, meaning adapter services developed for different external hardware components, such as two different AR displays, could be simultaneously deployed with significant ease. Ultimately, it provides prototyping teams with the ability to quickly test and evaluate alternatives or vendor products.

## IMPLEMENTATION

To meet the aforementioned design goals, the H4H team selected open-source and commercial off-the-shelf technologies. These technologies have large user communities and are more likely to have existing support or publicly available documentation that facilitates integration with our platform.

Many kinds of services could be introduced into the architecture. Some examples are a database, a machine learning model, or an adapter for a new hardware component. Regardless of the functionality they provide, all services are essentially software that any prototyping team using H4H should be able to deploy. For this reason, H4H uses Docker, a containerization platform for packaging applications into standardized executable components called containers.$^{2}$ Docker enables service functionality to be wholly contained within a modular, shareable package in a way that is largely independent

of the compute environment. If the packaged application works on one machine with Docker Engine, it should work on any other machine with a matching version of Docker Engine and the same CPU architecture (e.g., x86, ARM64). Packaged applications ready for execution, referred to as container images, can be shared in a repository and downloaded on demand. Docker enables a long-term solution for creating, managing, and storing versiontracked capabilities across efforts and projects.

Complementing the ability to containerize each service for easy execution, Kubernetes$^{3}$ provides a suite of powerful tools for managing the networking, monitoring service health, or creating the support infrastructure for the deployed containers. Kubernetes uses a series of resource files to define how a container is deployed and how its life cycle is managed thereafter. The Kubernetes

Control Plane implements this functionality through a set of core services that respond to cluster events. A Kubernetes cluster is composed of one or more worker machines, referred to as nodes, that can share the workload. H4H deployments will run a single cluster in a single edge-compute device. When edge-devices are networked together, communications are managed as cluster-to-cluster, rather than node-to-node. This design choice is necessary to enable the Kubernetes Control Plane, which manages the service deployments, to run independently on each device. The streamline installation and setup, Canonical, the maintainers of Ubuntu, created MicroK8s.$^{4}$ MicroK8s is a powerful, lightweight, production-ready Kubernetes distribution. As a whole, it has been designed with edge-computing in mind and has a small disk and memory footprint. H4H currently supports simple and easy-to-use installation scripts built on MicroK8s.

HMT capabilities are expected to be deployed as a collection of services (Figure 1) using Kubernetes resource files. For larger projects integrating multiple capabilities, resource files can become unwieldy. This is amplified in a highly modular HMT system where varying configurations of several or individual services are possible depending on the operational need. To streamline this process, H4H uses Helm, a Kubernetes package manager.$^{5}$ Helm users create "chart" files that allow a collection of Kubernetes resources to be packaged together for

Figure 1. H4H architecture. Services in the architecture interact through publish-subscribe channels with predefined abstract data types, allowing services to remain decoupled. Replacing a service requires only that the replacement adhere to the predefined abstract data type of the channels it will interact with.

<!-- image -->

Figure 2. The multiple layers of configuration provide Docker and Kubernetes the instructions to build, execute, monitor, and manage applications. Once a capability is wrapped in a Helm chart, it can be shared and reused across projects with little to no effort.

<!-- image -->

easy deployment. Charts offer two key features: version tracking and templating. Version tracking enables capabilities to be incrementally versioned as changes are made, while templating enables users to supply a single "values" file containing deployment-specific settings to base templates of Kubernetes resource files. Templating is a key feature H4H uses to deploy applications across different systems. Figure 2 shows how Docker, Kubernetes, and Helm wrap an application. Each layer provides some abstraction or control over the layers beneath it.

All these tools function together to provide a method for deploying modular service elements. Meanwhile, the Robot Operating System 2 (ROS 2) provides the framework for communication between services.$^{6}$ By default, ROS 2 uses the Data Distribution Service standard for messaging. DDS is standard backed by the Object Management Group that aims to enable dependable, highperformance, scalable data exchange over UDP. ROS 2 allows developers to define message types, which can be shared and versioned similarly to packaged applications, as well as to create publish-subscribe channels, named Topics, among many other things. H4H uses this functionality to define the abstract interface through which services communicate. A message type defines the data structure, while the Topic provides the medium. In the UGV example, the Threat Alert and Sensor Data Topics would have different message types (Figure 1). If each service were developed by a different team, the teams would need to be aware of only the message types they will produce or consume to integrate with other teams.

## CONCLUSION

H4H provides a framework that expedites the integration of HMT prototypes. Specifically, it uses a micro-

services approach to separate components and provides methods for abstracting component interfaces. These features enable modularity. As a result, adding, upgrading, replacing, and reusing hardware and software components is more efficient. Although still in its early development stages, H4H has already shown promising results on an initial test bed integrating AR displays, UGVs, UAVs, gesture controllers, and more. The H4H team plans to continue refining the H4H framework and expanding its set of tools and features in further pursuit of the end goal of augmenting tomorrow's warfighter capabilities.

ACKNOWLEDGMENTS:

This

paper

was written in 2021, and H4H has grown since that time. Matthew Breiner (matthew.breiner@jhuapl.edu) or Brandon Filo (brandon.filo@jhuapl.edu) can be contacted for updates.

## REFERENCES

- $^{ 1}$P. Richardson. "What are microservices?" microservices.io. https:// microservices.io/ (accessed Nov. 22, 2021).
- $^{ 2}$"Empowering app development for developers." Docker. Docker, Inc. https://www.docker.com/ (accessed Nov. 22, 2021).
- $^{ 3}$"Production-grade container orchestration." Kubernetes. https:// kubernetes.io/ (accessed Oct. 7, 2021).
- $^{ 4}$"MicroK8s-Zero-ops Kubernetes for developers, Edge and IOT: MicroK8s." microk8s.io. Canonical Ltd. https://microk8s.io/ (accessed Nov. 22, 2021).
- $^{ 5}$"The package manager for Kubernetes." Helm. https://helm.sh/ (accessed Nov. 22, 2021).
- $^{ 6}$"ROS documentation." Open Robotics. https://docs.ros.org/ (accessed Sep. 28, 2021).

<!-- image -->

Edgar F. Martinez, Research and Exploratory Development Department, Johns Hopkins University Applied Physics Laboratory, Laurel, MD

Edgar F. Martinez is a software engineer in APL's Research and Exploratory Development Department. He holds a BS in computer science with

minors in cybersecurity and astrophysics from Texas A&M University. As part of the rotational Discovery Program, he has rotated through multiple teams at APL and contributed to projects related to full-stack web development, modeling and simulation, and data visualization. During his rotational assignment with the Cyber-Physical Systems Development Group, he developed introspections tools and services to facilitate test and evaluation efforts for the H4H project. His email address is edgar.martinez@jhuapl.edu.

<!-- image -->

Rebecca M. Crockett, Asymmetric Operations Sector, Johns Hopkins University Applied Physics Laboratory, Laurel, MD

Rebecca M. Crockett was a process engineer in APL's Asymmetric Operations Sector. She holds a BS in chemical engineering with a concentration in cybersecurity from the University of Tulsa. During

her time at APL, Rebecca contributed to a wide variety of projects with focuses ranging from sensor fusion to robotics to human-machine teaming and augmented reality. Rebecca was the assistant program manager on the H4H effort.

## Ian A. Grissom, Asymmetric Operations Sector, Johns Hopkins University Applied Physics Laboratory, Laurel, MD

Ian A. Grissom was a software engineer in APL's Asymmetric Operations Sector. He holds a BS in electrical engineering from the University of Maryland, College Park and an MS in electrical and computer engineering from Johns Hopkins University. During his time at APL, Ian contributed to a wide variety of projects with focuses ranging from safety critical embedded software development to robotics to software architecture building and software reverse engineering. Ian was the project manager and a technical contributor on the H4H effort.

Multidimensional Cyber Threat Scenario Enumeration Model for Resilience Engineering

## A Multidimensional Cyber Threat Scenario Enumeration Model for Resilience Engineering

Anurag Dwivedi

## ABSTRACT

Many frameworks have been proposed for analyzing and enhancing the cyber resilience of systems and missions. Most focus on conducting risk or gap analyses before suggesting mitigations. To apply those frameworks, it is essential to gain knowledge about the threat scenarios against which the risk or resilience is being evaluated. Common approaches to threat enumeration include leveraging threat intelligence or identifying sequential actions from threat models that are mainly developed from databases of past threat events. Such approaches either lack comprehensiveness or are too granular to produce a manageable scale of threat action combinatorics when identifying potential cyber threat scenarios for engineering a resilient mission or system. This article suggests a threat scenario characterization and enumeration approach that does not rely on intelligence or past threat databases and allows for tailored abstraction of threat scenarios to inform mitigation strategy decisions and facilitate cybersecurity and resilience engineering.

## INTRODUCTION

Although a standardized definition of cyber resilience is still under development, we realized about a decade ago$^{1,2}$ that any expression of "resilience" must include (1) a subject with a defined mission or goal (with an identified minimum acceptable performance level to be maintained during a specific period in both normal and stressed operational scenarios) for which the resilience is being described; and (2) a threat or external force against which the resilience is being described. As shown in Figure 1, the subject could be a mission, a system, a subsystem, a device, or a component whose purpose and performance thresholds are well defined. The threat against which the subject's resilience is being explored could be kinetic, natural, nuclear, cyber, or climate related. Resilience can be designed for target threat(s) of a specified type and intensity.

The subject's performance may degrade because of the effects of a threat event, and depending on the resilience mitigations in place, the subject's performance may be fully restored after a period of time. This performance degradation may constitute a failure of the subject unless either the degree of degradation is greater than a unique minimum acceptable performance level or the subject remains in the degraded state for a duration that is shorter than a temporal threshold. Thus, to assess the subject's resilience, one has to know the maximum tolerable bounds for achieving various grades or levels of successes for the subject. For example, a mission may fully succeed, partially succeed if degradation or duration remains within certain bounds, or fail if the performance remains at a certain unacceptable degraded state beyond a threshold tolerance period.

"Resilience of

Examples:

- · Mission
- · System
- · Subsystem
- · Device
- · Component

Examples:

- · Kinetic
- · Natural disaster
- · Nuclear
- · Cyber
- · Electromagnetic pulse

Figure 1. Subject and threat enumeration to properly describe resilience. Any expression of "resilience" must include a subject with a defined mission or goal (and its minimum acceptable performance level over a specified duration) for which the resilience is being described and a threat or external force against which the resilience is being described. This figure illustrates example subjects and threats and their relationship.

Engineering the resilience of a subject thus requires (1) the knowledge of detailed dependencies within the elements of the threat surface of subject; (2) enumeration of relevant threat scenarios at an actionable abstraction; (3) a model for performance degradation (and duration) resulting from compromises caused by the threat; and (4) acceptable performance and duration thresholds for various grades or levels of successes. Obtaining each of these resilience engineering components comes with respective challenges.

This article discusses the challenges associated with identifying relevant threat scenarios and proposes a threat scenario enumeration model (T-SEM) for use in resilience engineering. The T-SEM is abstract enough to cover a comprehensive threat scope and granular enough to inform resilience analysis and mitigation strategy development. Because the threat scenarios capture a full spectrum of threats relevant to resilience engineering and designs, there is no need to enumerate each possible attack vector in extreme detail in early phases of resilience engineering. This limits the enumeration of threat scenarios to a practical scale, ensures that the model is comprehensive and complete in its breadth, and allows for the selection of needed mitigation strategies and approaches starting from early phases of a system's resilience engineering and design life cycle.

## RELATED WORK

The term threat , in this article, is not defined based on the geography or the threat tier level. Neither is it characterized based on adversary intent, which is generally political, sociocultural, or financial. Rather, the definition of threat scenarios is abstracted to include the attack, target, and access types; the phase of the development cycle; and the broad types of defender's security capabilities targeted by the adversary.

Cyber threat models identify the specific actions that an adversary can take to succeed at each stage toward achieving an offensive malicious goal. The enumeration of threat actions in these models is based on past observations of threat events. However, threat enumeration

based on past reported or known incidents does not make up the whole population of relevant threats.

Further, intelligence-based threat forecasts only offer a limited view into future attacks. Factors that can limit these forecasts include intelligence quality, forecast time frame, the intelligence analyst's skill level, reduced visibility into past incidents and future threats,

and partial information about adversaries' current or developmental capabilities and intents. As a result, intelligence-centric threat analyses cannot provide a comprehensive cyber threat picture for missions and systems that must be designed to persist for a long lifetime. Resilience designs will likely be insufficient against future threats if they are designed to mitigate only historical threats. Another major challenge in this regard is that the specific start-to-end threat action combinations are too numerous to be practical for individual consideration in resilience engineering and design.

Several threat databases are available, such as MITRE's Common Vulnerabilities and Exposures (CVE),$^{3}$ the National Institute of Standards and Technology (NIST) National Vulnerability Database (NVD),$^{4}$ the Common Configuration Enumeration (CCE) List (developed by MITRE and transitioned to NIST),$^{5}$ MITRE's Common Weakness Enumeration (CWE),$^{6}$ and MITRE's Common Attack Pattern Enumeration and Classification (CAPEC). 7

Threat-based mitigation models include the National Security Agency (NSA)/Central Security Service (CSS) Technical Cyber Threat Framework (NTCTF),$^{8}$ the Department of Defense Cybersecurity Analysis and Review (DoDCAR),$^{9}$ and MITRE's ATT&CK.$^{10}$ Commercial tools can scan a network, network appliance, or element for weaknesses, susceptibilities, or vulnerabilities.$^{11,12}$ All of these models depend on databases of vulnerabilities already found or observed in the system and known attack vectors from past incidents.

## DEFINING CYBER THREATS AND EXAMPLES OF MITIGATIONS

Security designs based solely on historical incidents are inherently reactive. Since the T-SEM approach discussed in this article does not rely on past events or known vulnerabilities, it captures a comprehensive set of broad threat scenarios for use in security design and mitigation strategy decisions. The T-SEM is based on predefined dimensions of the cyber threats. These include the system's life-cycle phase when threat scenarios and

against

threat/event"

Figure 2. Multidimensional cyber T-SEM. All dimensions must be considered at each stage of the mission and the system development life cycle to enumerate a comprehensive set of threat scenarios. This spider chart provides only a taxonomy and structure to the threat scenario dimensions and its elements and is not intended to provide a scale along each of its six dimensions.

<!-- image -->

mitigations are considered, access mode, attack path complexity, compromise or cyber effect type, resilience capability to be exploited, and attack surface node type and data exposure modes. All of these dimensions must be considered at each stage of the mission and the system development life cycle to enumerate a comprehensive set of threat scenarios. These dimensions are displayed in a spider chart in Figure 2, and each is defined later in this section. The spider chart provides only a structure and taxonomy for the threat scenario dimensions and its elements and is not intended to provide a scale along each of its six dimensions.

Five of these dimensions have three elements each, whereas the attack surface target dimension has five elements since the technology element is further divided into those related to data in use (DIU), data in transit

(DIT), and data at rest (DAR) sub-elements (discussed in more detail in the section on attack surface nodes). While a maximum of 1,215 combinatorial threat scenarios are possible in this model, not all will be relevant for resilience design for a system supporting a mission in a specific operational environment. The elimination of irrelevant threat scenarios is discussed in the Threat Scenario Enumeration section.

## Life-Cycle Phases

Life-cycle phase is a significant dimension to consider from two perspectives: (1) to characterize phase-relevant threat scenarios and (2) to develop phase-specific mitigations for all threat scenarios irrespective of the phase where a threat is invoked. A cyberattack can be planted or launched at any phase of the system development life cycle, including early stages when a mission concept of operations is initially developed. In Figure 3, the system life cycle is characterized by three major phases: pre-acquisition, acquisition, and post-acquisition. To characterize the threat scenario along this dimension, a security engineer would consider only the threats that are relevant and could materialize during any of these three major phases of the system life cycle.$^{12}$ Scenarios in the pre-acquisition phase include activities such as

Figure 3. Life-cycle phases, shown in the systems engineering V , where a threat can materialize. Characterization of the threat scenario would consider only relevant threats that could materialize during any of these three major phases. However, mitigations considered in early phases are not limited only to the threats relevant to those early phases but also apply to threats that are planted early but may affect the system or mission in later stages.

<!-- image -->

development of the mission operational concept. Compromises at this early stage of a program can affect mission operational concepts, weakening resilience, cyber policy, funding for cybersecurity, and the ability to incorporate cyber resilience from the very beginning of the acquisition cycle. Mitigations considered in early phases are not limited only to the threats relevant to those early phases but also apply to those threats that are planted early but may affect the system or mission in later life-cycle stages.

Attacks can be planned, planted, and executed during the acquisition phase and can include compromising not only the systems being acquired but also the acquisition program itself, as well as the infrastructure, processes, and ecosystem used by the program. Affected elements include, but are not limited to, the program protection plan; processes such as requests for information, proposals, or quotations; critical program information; critical technology; supply chain; and other program-originated security and sustainability requirements.

Cyberattacks can happen in the post-acquisition phase during the operational, sustainment, upgrades, maintenance, and end-of-life phases. New susceptibilities can be introduced during maintenance; technology upgrades; improper patches; imperfect operational tactics, techniques, and procedures; or suboptimal implementations of cyber solutions. Because a system's susceptibilities to attack can be exploited during any phase of the life cycle, robust and continuous processes for monitoring, auditing, assessing, and remediating must be required. At the end of its life, a system must be disposed of properly to ensure the confidentiality of sensitive information, technology, vulnerabilities, and processes.

It is worth noting again that the mitigations identified at a particular life-cycle stage are not specific only to the threats relevant to that stage. Mitigations for cyber risks at different stages of the life cycle are unique, justifying the life cycle as an important dimension for characterizing cyber threat scenarios.

## Access Mode

An adversary uses three primary modes of access to affect data availability, inject malicious or rogue code, or steal or exfiltrate data or information: (1) external connections to the system via wireless, wired, or other transmission means; (2) rogue code or firmware implanted in the supply chain; and (3) physical access to a cyber system by a human or a robot-for example, when using external media through a USB interface; input/output (I/O) interfaces connecting devices such as a keyboard, video monitor, or mouse (KVM); or a KVM switch. An advanced adversary can gain access by other means, such as modulating a power, acoustic, or laser/optical signal through external I/O interfaces.

The mitigations for each of these three access modes are drastically different. For example, for connected systems, intrusion detection, access control, identity and authorization management, encryption, hashing, allowlist implementation, moving target defenses, and honeypots may be considered. For mitigating supply chain risks, the defender may depend on a trusted supplier or foundry, ensure trusted chain of custody at all times, verify code and validate I/O, implement an allowlist, mandate vendor hash, or use fuzzing-based testing, among other techniques. To mitigate against unauthorized malicious physical access, a defender may control physical and virtual access, protect against burglary, employ hashing, disable unused ports, train users, establish trust, and monitor human behavior and activity trends.

Since the mitigations for safeguarding against these access modes are different, access mode is a justified dimension for characterizing cyber threat scenarios.

## Attack Path Type and Complexity

After accessing a system, the adversary can take one of several paths to attack, each with a different level of complexity. The adversary may target a node directly. If direct access is not possible, the adversary may have to traverse through the attack surface topology to access the target. In the latter case, the adversary may have to traverse within a single security enclave or cross security boundaries of multiple enclaves (Figure 4). A directly accessible target may be easier to discover and compromise. Traversal through the attack surface topology nodes may increase the adversary's cost and level of effort. If it is necessary to traverse through multiple security boundaries or enclaves, the adversary's effort, time, and cost may further be elevated.

Mitigations for these three attack scenario elements require astute architecture and design. Critical assets should be behind multiple security boundaries or defenses to limit an adversary's reach and to enhance the defender's ability to detect and respond. The heterogeneity of technology at various nodes along the traversed path will make traversal difficult. Moving target defenses will make the traversal path uncertain for the adversary. A segmentation strategy with multiple enclaves may be employed where enclaves are architected so that critical nodes are not aggregated in a single enclave but rather are distributed over multiple enclaves. A segmentation strategy may enable employment of zero trust security concepts. Additionally, basic protection, detection, preplanned response, and recovery will provide needed cyber hygiene for secure operations.

## Compromise Type and Cyber Effect

The type of compromise is another key threat dimension. Cyber compromises manifest themselves in three

Figure 4. Three types of attack paths to reach the desired targets. Path A is direct access, path B requires intra-enclave traversal, and path C requires inter-enclave traversal. Each path has different costs to the adversary; path C may be the most costly in terms of time and effort.

<!-- image -->

major ways: confidentiality, integrity, and availability. Confidentiality attacks result in unauthorized exposure or exfiltration of data or information, generally for malicious purposes. Integrity attacks compromise the integrity of data or information. They may result in corrupted data, decreased defender trust in the systems or codes being used, or flawed or degraded system performance. Availability attacks are intended to make data, information, or services unavailable. Examples include disrupting power, creating cyber-physical effects, and denying service.

As illustrated in Figure 5, availability and integrity attacks generally cause more severe tactical loss than confidentiality attacks, whereas confidentiality attacks are responsible for more severe strategic loss. Also, as the figure shows, one type of attack can enable an attacker to succeed subsequently in launching another type. A skillful adversary may use a series of confidentiality attacks during the planning, discovery, or reconnaissance phases of a well-orchestrated cyberattack, with the goal of eventually launching an availability or integrity attack.

It is important to understand the effects of different types of compromises since they will have varying degrees of impact to an organization's, or mission's, tactical and strategic goals. Resilience

against these three types of compromises may depend on the nature of the organization's or mission's goals. For example, financial institutions may be able to quantify the impact of a confidentiality attack more readily than the defense sector can, where the loss may be strategic and harder to quantify. Integrity attacks may be more serious for tactical defense missions than confidentiality attacks. Accordingly, mission owners and organizations may prioritize mitigations according to the consequences they may suffer from such compromises.

## Primary consequence

Figure 5. Confidentiality, integrity, and availability compromises with tactical and strategic consequences. While availability and integrity attacks generally cause more severe tactical loss, confidentiality attacks are responsible for more severe strategic loss. Also, one type of attack can enable an attacker to successfully launch another type.

<!-- image -->

Increasing degree of tactical loss (easier to quantify)

Increasing degree of strategic loss (harder to quantify)

Mitigations for confidentiality compromises are primarily obfuscation, strong encryption, and access control. Integrity can be detected using hash comparison and I/O verification and can be prevented by limiting read/write access and implementing redundancy combined with voting schemes. Availability attacks can be countered with preprovisioned redundancy when supported by heterogeneous technologies and security architectures. 13-17

Since these compromises require different types of mitigations and have varying degrees of impact to an organization or mission, the compromise type and effect is an important dimension for cyber threat scenario characterization.

## Targeted Security and Resilience Aspects

The NIST cybersecurity framework$^{17}$ identifies five core functions of cybersecurity: identify, protect, detect, respond, and recover. These map well to the Cyber Survivability Endorsement framework,$^{18}$ which describes all these functions using only three survivability aspects: prevent, mitigate, and recover. No matter which framework is used, these functions are essential cybersecurity and resilience design elements, and an adversary may target any of them. In addition to protecting basic functionality, a good cybersecurity and resilience practice is to implement appropriate detection/response and recovery methods. This dimension of threat scenario assumes two security postures: (1) the defender has not properly implemented prevention, detection/response, and recovery defensive controls, and adversary methods simply exploit their absence; and (2) such measures are in place, but adversaries are able to degrade or defeat them to achieve their goals.

Compromising the ability to protect the system may degrade its (or its elements') functionality and may have cascading effects that propagate eventually to affect the mission. An adversary may realize such effects by compromising physical or logical access controls, compromising obfuscation techniques such as encryption, or bypassing allowlists.

An adversary may choose to attack the detectability of malicious activities and anomalous behavior in a cyber system. If the system is designed to sense, detect, alarm, log, and alert to any intrusions, anomalies, or unexpected performance, compromises to these capabilities may have serious consequences or allow an adversary to hide moves or progress the attack along the intended attack vector. Common mitigations against compromises to detection capability are to implement a separate out-of-band, actively monitored detection system with a separate security enclave and to institute privilege access or escalation processes.

Response and recovery capabilities are tightly coupled with detection capabilities. Anomaly detection

could trigger an automated or operator-assisted response. This response may be tactical remediation within mission-relevant time frames, even if it degrades system performance. If the tactical remedial response is not sufficient to achieve tactical goals, restoration and recovery may be necessary. Restoration and recovery may or may not be completed in the mission-relevant or desired time frame. Response and restoration capabilities may be protected by frequent checks and audits to ensure that all enabling elements, particularly those providing a backup or redundant capability to a primary means, are in working order and will function as expected when needed.

Mitigations for protection or prevention, detection/ response, and recovery capabilities are distinct and may affect the resilience of the mission. For these reasons, adversarial compromise of these resilience measures is a unique and essential dimension of cyber threat scenario characterization.

## Attack Surface Node Type and Data Exposure Mode

Cyberattack surface can include people, processes, and technology elements that can be identified from a comprehensively described system model. While the system model may contain many systems, subsystems, components, interfaces, data and service flows, operators, processes, and procedures, the cyberattack surface may comprise only a small subset of those entities. Cyberattack surface constitutes only a subset of the complete system model and includes only those elements that are cyber relevant. Cyberattack surface enumeration, however, must consider both the internal and external cyber-relevant entities if they have common service interfaces. In this article, the elements of the cyberattack surface are called the nodes of the attack surface graph. The number of nodes scales consistently with the abstraction level of the attack surface description or topology. 19

A threat can target a people node, a process node, a technology node, or a combination$^{2,19}$ to eventually compromise data or services. Depending on the relationships between the attack surface nodes and subject performance, analysis can assess the impact$^{19}$ of a compromise. Also, depending on the node's contribution to the subject's performance, with or without response and restoration, its criticality$^{20}$ can be determined. Criticality analysis does not require knowledge of a detailed attack vector since it considers the mission impact if (and not how ) a node is compromised to achieve an intended cyber effect. In one use case, criticality analysis can prioritize the application of mitigations among the attack surface nodes based on their relative criticalities. This may limit the complexity and cost of applying appropriate mitigations, while meeting resilience design goals.

Mitigations for people, process, and technology nodes may be different, justifying the need for identifying the

attack surface node type as a dimension to characterize the threat scenario. Mitigations for people and process nodes can be envisioned to be governance centric, zero trust, and implementing dynamic access policies based on continuous advanced analytics such as behavioral factors, machine learning, and artificial intelligence.

Technology nodes include three primary modes$^{2}$ in which data can be exposed: DIU, DIT, and DAR. Data processed by a computing device are referred to as DIU. In most applications, even if the data are transported and stored encrypted, they are decrypted for computational processing. Thus, DIU is a critical exposure mode available to a cyber adversary. Research on and early applications of homomorphic encryption may alleviate or obviate the need to decrypt while processing. However, several currently available homomorphic encryption solutions require significant computational resources, which may negatively affect system performance. While these technologies continue to mature, mitigations for DIU compromise remain indirect, such as those enabled through access control.

Data stored on disks, on removable media, and in databases are referred to as DAR and provide another exposure mode to cyber adversaries. Mitigations such as heterogeneous redundancy, full-disk encryption, and access control protect DAR against confidentiality, availability, and integrity attacks.

Data transmission within a system or between systems using local or wide area networks or direct (wired or wireless) communications links provides another exposure mode to the cyber adversary. The complex layering and protocols involved in data transport present numerous opportunities for a cyber adversary to com-

against all exposures for multi-layered, multi-protocol, multi-encapsulated transmission. Improperly secured transmission may allow attacks such as man-in-the-middle and replay, among other malicious activities.

Mitigation strategies for each of these three exposure modes may differ significantly, justifying the DIU, DAR, and DIT exposure modes as unique sub-elements of technology nodes as a threat scenario attack surface target element.

## THREAT SCENARIO ENUMERATION

Adversarial threat action paths along the cyber kill sequence can be determined by granular threat models such as ATT&CK. Representing all combinations of threat actions in the ATT&CK model would result in many billions of combinations, making development of a mitigation strategy extremely challenging because of the sheer scale of attack scenarios requiring mitigations. Security engineers use multiple approaches to suppress this prolific set of attack path scenarios, such as random selection, Monte Carlo-assisted selection, selection of a subset of threat path scenarios, or use of intelligence information to identify the most likely threat path scenarios.

While any of these approaches may produce a smaller and more manageable threat path set, they are all insufficient for risk assessment and resilience engineering. If mitigations are implemented for a randomly selected small subset of threats, adversaries will identify a nonmitigated path in the early reconnaissance phase of the cyber kill sequence. Monte Carlo selection will not

Figure 6. Suppression of enumerated threat scenarios. Rather than relying on Monte Carlo selection or intelligence-based selection, the T-SEM abstracts threat scenario enumeration by looking at six distinct dimensions. Elements that are not relevant can then be eliminated, and remaining elements can be further decomposed and then prioritized based on, for example, threat intelligence or threat criticality.

<!-- image -->

promise DIT. For example, protocols at each Open Systems Interconnection (OSI) layer, encapsulations, and tunneling may provide multiple levels of exposure and compromise opportunities. Encrypted data may have to be decrypted at the transit nodes. In some cases, only the header, and not the payload, needs to be decrypted to facilitate transport and routing. Both the header and payload may be allowed to be encrypted for encapsulated and tunneled data for a specific application. Because of the complexities involved in end-to-end secure data transmission, defense-in-depth must be carefully applied to protect

result in selection of the most likely or critical threat paths to be mitigated because cyberattacks are deliberate, and not proven to be random or stochastic. As with random selection, if a small subset of threats is chosen, adversaries will identify a nonmitigated path. Threat intelligence is usually more useful for short-term tactical response and defensive posture. While it may be useful for short-term prioritization of threats to mitigate, short-term threat intelligence should not be used for long-term resilience design.

The T-SEM approach suggested in this article is an abstracted threat scenario enumeration that covers a large threat space with six distinct dimensions. Each dimension has three elements (except for the attack surface component, which effectively has five elements, namely people; process; and DIT, DIU, and DAR technology targets). This yields a total combinatorics of 1,215 threat scenarios, which is many orders of magnitude smaller than the ~10$^{18}$ threat path scenarios computed from a more granular ATT&CK model. The T-SEM threat scenarios of interest, however, can be further reduced by eliminating dimensional elements that are not relevant to the mission, system, or operating environment, as illustrated in Figure 6. Remaining threat dimensional elements or scenarios can be prioritized using criteria including, but not limited to, threat intelligence.

Identification of relevant dimensions and threat taxonomy for characterizing cyber threats allows enumeration of the relevant threat scenarios. The proposed multidimensional model shown in Figure 2 provides a basis for enumerating threat events at an abstraction level sufficient to identify and mitigate gaps in the early concepts of operation, architecture, governance, security policy, and high-level design. Threat scenario enumeration is also helpful in facilitating mitigation trade space and decision analyses. The abstracted threat scenarios ensure completeness of threat coverage while managing the scale and size of threat scenario enumeration.

Figure 7 illustrates an example of suppressing threat scenarios for a specific mission, system, and operational environment. The system is in its operational and sustainment phase of the life cycle, where an adversary can access the system only through its connections with a larger network and supply chain (and cannot gain physical access) because physical interfaces are either removed or robustly protected. This system has only a single security enclave, and critical nodes are behind a gateway requiring an intra-enclave traversal to reach the targeted critical system nodes. Because of the nature of the mission and its dependence on the system, the mission owner is only concerned about availability attacks. The defender wants to consider proper prevention, detection/response, and recovery aspects to achieve the desired resilience but

reduced to 12 from the T-SEM's 1,215. One of these 12 threat

Figure 7. example system is in its operational and sustainment phase,

<!-- image -->

is not sure whether these resilience aspects are properly implemented. Also, the defender is particularly concerned about DIU and DIT; since there are no critical data stored for accomplishing the mission, DAR is not relevant in this example. People and processes are trusted and are not considered key targets in relevant threat scenarios.

In the figure, the irrelevant threat dimensional elements are marked with an X. Threat scenarios are thus reduced to 12 from the T-SEM's 1,215. One of these 12 threat scenarios is expressed in a single sentence suitable for use in a mitigation requirements description. For such a system, if there are N critical nodes to be targeted, there are 12 N potential threat scenarios. This example demonstrates that while a comprehensive threat scenario-based analysis may be perceived to be difficult, it is well within the realm of practical implementation of deterministic risk analysis and mitigation strategy. Mission resilience against each of these threat scenarios can be analyzed and a mitigation strategy can be developed.

Once this enumeration of relevant threat scenarios is complete, the list can further be reduced or prioritized by applying the information specific to the operating environment or if definitive likelihoods or prioritization criteria are known from threat intelligence. Specific attack vectors for relevant T-SEM threat scenarios can be developed using more granular cyber kill sequence models such as ATT&CK to support the identification of specific cyber solutions aligned with the mitigation strategy.

## APPLICATION OF T-SEM TO RESILIENCE ENGINEERING

Key applications of threat scenarios are in assessing, engineering, designing, and enhancing cyber resilience and ensuring mission survivability. While the intent of this article is not to discuss exhaustive use cases of threat characterization and enumeration, an example use case, a simple process for resilience evaluation, engineering, and design, is illustrated in Figure 8.

In this example, a description of cyber-relevant system nodes (e.g., through the cyberattack surface enumeration process$^{19}$) is needed, along with a description of the data or services provided by those nodes as well as activities relevant to other system nodes or supporting essential mission process steps. The dependencies between system nodes and mission functions allow an assessment of mission performance or impact degradation when a specific threat scenario, involving a specific cyber compromise at a specific system node, materializes. Proper mission engineering builds mission resilience through contingencies at the operational level to guard against system function degradations or failures. A key step in the development of a prioritized mitigation strategy is identifying (1) specific threats-a combination of node(s) and compromise(s)-that are capable of degrading mission performance below its tolerance threshold and (2) whether response or restoration can revert the system to an acceptable level of mission performance

Figure 8. Role of threat scenario enumeration in resilience design. In this example, a description of cyber-relevant system nodes is needed, along with a description of the data or services provided by those nodes as well as intra-node activities that provide services to other system nodes or to essential mission functions or process steps. The dependencies between system nodes and mission functions allow an assessment of performance when a specific threat scenario materializes. If the resilience is not sufficient, mitigation approaches need to be identified and implemented, and the analysis can be repeated to assess whether the enhancements are sufficient. The process can be iterated until the desired resilience is achieved against the design threat scenarios and threat intensities.

<!-- image -->

within mission-relevant time frames. Detailed criticality analysis methodology is published elsewhere. 20

If the resilience of the starting system architecture or design is not sufficient, mitigation approaches need to be identified and implemented.$^{2,19-21}$ The analysis shown in Figure 8 can be repeated after considering new mitigations to assess whether the resilience enhancements meet the challenges of relevant threat scenarios. The process can be iterated until the desired resilience is achieved against the design threat scenarios and threat intensities.

As a defender, a consequence-aware mitigation strategy can be used for security and resilience engineering and design processes. This will allow the defender to understand what nodes or combination of nodes need to be hardened against which type of cyber compromises to achieve the desired level of resilience, without requiring the defender to apply all mitigations uniformly to all nodes. 20

Figure 9a displays the entire threat scenario space from the T-SEM schematically. Not all of these 1,215 scenarios are relevant for every system, mission, and operational environment, so applicable node-specific threat scenarios need to be identified as a reduced set, as shown in Figure 9b, for a specific node of the system.

Once the critical nodes and respective most critical threat scenarios (those that have the potential for the most severe mission impact) are identified, mitigation strategies for each of the threat scenarios associated with each critical node can be astutely determined by cybersecurity subject-matter experts. When developing mitigation strategies, these experts would consider threat coverage, mitigation effectiveness, affordability, feasibility, and practicality, among other factors. Mitigation approaches identified for each of the threat scenarios can be added to a mitigation database as a resilience design utility for future use. If the mitigations applied to each node against each threat dimensional element are added to a database, post-mitigation threat

Figure 9. Visualizing relevant threat scenarios, and their coverage by mitigations, to assist resilience engineering. (a) The entire threat scenario space from the T-SEM includes 1,215 possibilities. (b) Applicable node-specific threat scenarios need to be identified as a reduced set for a specific node of the system. (c) Mitigation approaches identified for each of the threat elements or scenarios can be added to a database, and post-mitigation threat coverage can be visualized using a visualization tool.

<!-- image -->

coverage (Figure 9c) can be visualized using a suitable visualization tool.

Mitigation approaches can be categorized as architecture (mission, system, and security), technology (cyber solutions), and governance approaches.$^{2}$ A structured approach to identifying and prioritizing mitigations is essential for resilience design and engineering (Figure 9c) for any system but is outside the scope of this article. Mitigation approaches and their implementation must be affordable and feasible, considering the system, application, use case, and constraints of the operating environment. Optimizing any mitigation strategy requires knowledge of critical combinations of threats and system nodes, which is where the abstracted T-SEM-based thread enumeration is useful. This approach comprehensively identifies critical areas by abstracting and then enables identification of specific cyber solutions by drilling down on specific critical areas.

## KEY CHALLENGES AND FUTURE WORK

While this article presents a comprehensive and manageable T-SEM, mitigation strategy development for each of the threat scenarios is not within its scope. When suppression of threat scenarios is considered, some of the combinations may not make sense for any system, mission, or operational environment. These are generally related to the combinatorics of people and process nodes with typical cyber threat elements. A follow-on effort could identify those combinations and eliminate them from the maximum possible 1,215 threat scenarios. An optimal set of global or node- or element-specific mitigations will obviate the need for mitigating each and every element of a six-layer T-SEM individually. These advanced, structured, and efficient mitigation identification, prioritization, and validation schemes could be developed for implementing efficient and affordable resilience engineering. Finally, follow-on work could more fully validate the hypothesis that the T-SEM offers a comprehensive description of all applicable threat scenarios and offers value and effectiveness in resilience engineering.

## REFERENCES

$^{ 1}$A. Dwivedi, "Quantifying resilience," tutorial presented at the 5th Ann. Workshop on Cyber Resilience by MITRE, May 20-21, 2015. $^{ 2}$A. Dwivedi, "Designing for resilience," Proc. SPIE 9097 , Cyber Sensing 2014, 90970C-9, Jun. 18, 2014, https://doi.org/10.1117/12.2054389. $^{ 3}$CVE (Common Vulnerabilities and Exposure), MITRE, https://cve. mitre.org (accessed Dec. 29, 2022). $^{ 4}$NVD (National Vulnerability Database), NIST, https://nvd.nist.gov (accessed Dec. 29, 2022).

- $^{ 5}$CCE (Common Configuration Enumeration). MITRE,. https://cce. mitre.org (accessed Dec. 29, 2022).
- $^{ 6}$CWE (Common Weakness Enumeration). MITRE. https://cwe.mitre. org (accessed Dec. 29, 2022).
- $^{ 7}$CAPEC (Common Attack Pattern Enumeration and Classification). MITRE. https://capec.mitre.org (accessed Dec. 29, 2022).

$^{ 8}$NSA Cybersecurity Operations, "The Cybersecurity Products and Sharing Division, "NSA/CSS Technical Cyber Threat Framework v2," Nov 29, 2018, https://media.defense.gov/2019/Jul/16/2002158108/1/-1/0/CTR\_NSA-CSS-TECHNICAL-CYBER-THREAT-FRAME-WORK\_V2.PDF.

$^{ 9}$P. Dinsmore, "DoDCAR/.govCAR," presented at the Software and Supply Chain Assurance Forum (SSCA), McLean, VA, Sep. 26-27, 2018, https://csrc.nist.gov/CSRC/media/Projects/cyber -supply-chain-risk-management/documents/SSCA/Fall\_2018/ WedPM2.2-STARCAR%20SCRM%20FINAL%20508.pdf.

$^{10}$ATT&CK. MITRE. https://attack.mitre.org (accessed Dec. 29, 2022). $^{11}$OWASP. "Vulnerability scanning tools." https://owasp.org/wwwcommunity/Vulnerability\_Scanning\_Tools (accessed Dec. 29, 2022). $^{12}$Department of Defense, "DoD Program Manager's Guidebook for Integrating the Cybersecurity Risk Management Framework (RMF) into the System Acquisition Lifecycle," Ver. 1.0, Sep. 2015, https://www. dau.edu/tools/t/DoD-Program-Manager-Guidebook-for-Integratingthe-Cybersecurity-Risk-Management-Framework-(RMF)-into-theSystem-Acquisition-Lifecycle.

$^{13}$"NIST Risk Management Framework." NIST. https://csrc.nist.gov/ projects/risk-management/risk-management-framework-(RMF)-Overview (accessed Dec. 29, 2022).

$^{14}$NIST, "Security and privacy controls for federal information systems and organizations," NIST Special Publication 800-53, Rev. 5, https:// csrc.nist.gov/publications/detail/sp/800-53/rev-5/final.

$^{15}$M. Reed, "Vulnerability analysis techniques to support trusted systems and networks (TSN) analysis," presented at the 17th Ann. NDIA Sys. Eng. Conf., Springfield, VA, Oct. 29, 2014, https://ndiastorage.blob. core.usgovcloudapi.net/ndia/2014/system/16997WedTrack1Reed.pdf.

$^{16}$D. J. Bodeau and R. Graubart. "Cyber Resiliency Engineering Framework," MITRE Tech. Rep. MTR110237, Sep. 2011, https://www.mitre. org/news-insights/publication/cyber-resiliency-engineering-framework.

$^{17}$NIST, "Framework for improving critical infrastructure cybersecurity," ver. 1.1, NIST, Apr. 16, 2018, https://nvlpubs.nist.gov/nistpubs/ CSWP/NIST.CSWP.04162018.pdf.

$^{18}$D. Clothier, "New DoD approaches on cyber survivability of weapon systems," presented at the AFCEA Chapter Event (Alamo ACE) 2016, San Antonio, TX, Dec. 5-8, 2016, http://www.alamoace.org/ resource/resmgr/2016\_ace/2016\_speakers/doc\_clothier\_dean.pdf.

$^{19}$A. Dwivedi, "Implementing cyber resilient designs through graph analytics assisted model based systems engineering," in Proc. IEEE Int. Conf. on Softw. Qual. Rel. and Secur. Companion (QRS-C) , 2018, pp. 607-616, https://doi.org/10.1109/QRS-C.2018.00106.

$^{20}$A. Dwivedi and D. Tebben, "Cyber situational awareness and differential hardening," in Proc. SPIE. 8408, Cyber Sensing 2012 , 840803, 2012, https://doi.org/10.1117/12.915642.

- $^{21}$A. Dwivedi, D. Tebben, and P. Harshavardhana, "Characterizing cyber-resiliency," Proc. 2010 Mil. Commun. Conf. (MILCOM) , 2010, pp. 1304-1309, https://doi.org/10.1109/MILCOM.2010.5680128.

<!-- image -->

Anurag Dwivedi, Asymmetric Operations Sector, Johns Hopkins University Applied Physics Laboratory, Laurel, MD

Anurag Dwivedi is a cyber systems security engineer in APL's Asymmetric Operations Sector. He has a BS in materials engineering from the Insti-

tute of Technology, Varanasi, India, an MS and a PhD in materials science and engineering from Alfred University, and an MS in information systems from Johns Hopkins University. Anurag has a 30 years of experience in research, project management, and modeling and simulation, as well as technical leadership, supervision, training, and coaching. He is a recognized expert in cyber and critical infrastructure resilience and security, systems engineering of enterprise and embedded tactical systems, model-based and secure cyber systems engineering, zero trust, and cloud and information security. He has extensive knowledge of standards, Risk Management Framework and conformance, graph-based cyber resilience analytics, cyber network planning and design, communications traffic estimation and forecasting, network applications, airborne networks, optical fiber, fiber and free-space optic systems, and directional mobile ad hoc network (MANET). Anurag has published and presented extensively on these topics. His email address is anurag.dwivedi@jhuapl.edu.

A. B. Author, B. C. Author, and D. E. Author Jr.

## Preface: APL 80th Anniversary Commemorative Articles

<!-- image -->

Jerry A. Krill

"APL Identifies Two New Defining Innovations." APL has made thousands of critical contributions to national security and space exploration over its 80-year history. Among them are a number of defining innovations: game-changing breakthroughs in technology that have created inflection points in history.$^{2}$ These revolutionary advances have ignited new engineering accomplishments globally, saved lives, and secured the United States against threats at home and abroad. On the occasion of its 80th anniversary, APL named two new defining innovations, its 10th and 11th. This article briefly describes these two breakthroughs.

"APL Achievement Awards and Prizes: The Lab's Top Inventions, Discoveries, and Accomplishments in 2022." For almost forty years, the Lab has honored its staff members' greatest accomplishments with an annual awards program.$^{3}$ The final article in this special series summarizes the APL Achievement Awards for accomplishments during 2022. These achievements represent a snapshot of the highly innovative activities underway at APL as of its anniversary year.

## REFERENCES

$^{ 1}$R. R. Luman, T. J. Galpin, and J. A. Krill, "Becoming a strategydriven technology organization-A case study," IEEE Eng. Manage. Rev. , vol. 51, no. 2, pp. 104-119, 2023, https://doi.org/10.1109/ EMR.2023.3246431.

$^{ 2}$R. D. Semmel, "Defining innovations," Johns Hopkins APL Tech. Dig. , vol. 34, no. 2, pp. 107-113, 2018, https://secwww.jhuapl.edu/techdigest/ Content/techdigest/pdf/V34-N02/34-02-Semmel.pdf.

$^{ 3}$E. M. Richardson and K. K. Livieratos, "APL Achievement Awards and Prizes," Johns Hopkins APL Tech. Dig. , vol. 34, no. 2, pp. 306-325, 2018, https://secwww.jhuapl.edu/techdigest/Content/techdigest/pdf/V34 -N02/34-02-Richardson.pdf.

March 10, 2023, marked the end of APL's yearlong 80th anniversary celebration. In honor of the occasion, the Johns Hopkins APL Technical Digest dedicates the following section of this issue to articles commemorating the anniversary.

"APL's Systems Approach to Becoming a Strategy-Driven Organization." APL has long had strategic intent. But during the past decade, a multistep integrated strategy has guided the Lab to a new level of capabilities and contributions. This article, an expanded and updated version of an article published in the IEEE Engineering Management Review ,$^{1}$ tells the story of how APL adopted a systems approach to become a truly strategy-driven organization.

"APL in the Twenty-First Century: A Retrospective on the 1983 Report to the Director." In 1982, APL's 40th anniversary year, a senior group called the APL senior fellows was asked to project what the state of science and technology and the environment surrounding APL might be like at the turn of the century, about 20 years into their future. Their projections were published in a 1983 report. Forty years later, at the end of APL's 80th anniversary year, Harry Charles looks back at the senior fellows' predictions.

"Technology Visions for APL's Centennial." As was done at the Lab's 40th anniversary, for the 80th anniversary, we asked a senior group-the Centennial Task Force, composed of technical society fellows and APL Master Inventors-to predict the major technology trends APL might encounter or influence by its centennial anniversary in 2042. This article details their collective response.

APL's Systems Approach to Becoming a Strategy-Driven Organization

## APL's Systems Approach to Becoming a Strategy-Driven Organization

<!-- image -->

Ronald R. Luman, Timothy J. Galpin, and Jerry A. Krill

## ABSTRACT

The Johns Hopkins Applied Physics Laboratory (APL) developed an integrated systems approach to strategy beginning in 2011. The approach has resulted in a vision and strategy framework that is built for the long term and has proven itself in execution during a turbulent decade marked by changing national security priorities, economic uncertainty, and transformative technological advances in areas such as artificial intelligence, hypersonics, and cyber. This article describes how articulating a bold vision and strategy, coupled with an innovative and lasting implementation plan, enabled APL to achieve a new level of national impact by becoming truly and overtly strategy driven. It did so by introducing, in stages, a system composed of six strategic planning methods that are often implemented separately or partially: a classic vision framework; a one-page strategy articulation adapted from industry; a continuous decision-making process; a strict alignment of resources to strategic priorities; regular accountability reviews; and a genuine engagement of the entire staff in fostering innovation aligned with the vision and strategy. The narrative includes expository descriptions of each system element and hard-won lessons learned during implementation. This can give the practitioner confidence that vision and strategy need not end up sitting on the shelf, but rather can be successfully applied to drive the organization forward through turbulent times.

## INTRODUCTION

Founded on March 10, 1942-just 3 months after the United States entered World War II-APL, sprung from a federal government effort to mobilize the nation's scientific resources to address wartime challenges. The effort was sponsored by the Office of Scientific Research

and Development, led by Dr. Vannevar Bush$^{2}$ and reporting to President Franklin Roosevelt.

Secretly tucked into an old used car garage in suburban Maryland, APL was tasked to find a better way for Allied ships to defend themselves against air attacks.

This article is an expanded and updated version of "Becoming a Strategy-Driven Technology Organization-A Case Study," previously published in IEEE Engineering Management Review . 1

The Laboratory designed, prototyped, and tested a radio proximity fuze (known as the VT fuze; VT stood for "variable time" to avoid the then-classified and more accurate "radio proximity" technology descriptor) that significantly improved the performance of antiaircraft shells in the Pacific-and, later, ground artillery during the invasion of Europe. Historians later judged this product of APL's intense work, along with the atomic bomb and radar, one of the three most valuable technology developments of the war. 3

From that successful collaboration, the US Navy, Johns Hopkins University (JHU), and APL committed to continuing their strategic relationship after the war. The Laboratory quickly became a major contributor to advances in guided missiles and submarine technologies, and today, more than eight decades later, APL's numerous and diverse achievements continue to strengthen our nation. 4

APL's work is sorted by 12 mission areas (i.e., thematic program portfolios), each of which taps the diverse skills and expertise of more than 8,000 staff members. Together, these mission areas encompass more than 1,500 ongoing research and development (R&D) projects for a variety of government sponsors, including all military services and agencies, NASA, and the Intelligence Community, with a total annual revenue of slightly more than $2 billion.

Long evolved from the strict focus of its founding project, APL relentlessly pursues a core purpose: to make critical contributions to critical challenges for our nation . But as the 21st century dawned, it became clear that this core purpose and the Cold War-original culture that grew around it were not enough to maintain pace with rapid technology developments and emerging threats confronting the nation. Adapting the Laboratory to meet this acceleration and globalization of critical technical challenges required a strategy to achieve a new level of innovation that the entire staff could embrace and sustain.

That included a look back to identify a set of innovations that went well past the level of critical contributions to truly revolutionary advances that provided a game-changing advantage for the nation. Indeed, defining innovations (a term coined for APL's 75th anniversary) such as the radio proximity fuze, surface-to-air guided missiles, satellite-based navigation, advanced sonar systems, ballistic missile defense from the sea, and planetary defense, among others, are evident throughout the Laboratory's history and exemplify APL's significance. 5

The APL Executive Council (EC), which consists of the director, chief of staff, assistant directors, general counsel, and sector and department heads, also looked ahead, forging a vision and strategy that would inspire and engage all staff members in the pursuit of new defining innovations that would ensure the nation's continued preeminence in the 21st century.

This case study demonstrates how articulating a bold vision and strategy, coupled with an innovative and lasting implementation plan, helped a historically successful organization achieve a new level of national impact by becoming truly and overtly strategy driven. It did not happen all at once, nor by adopting one particular best practice. Instead, APL wove a system composed of six strategic planning elements that are often implemented separately or partially: a classic vision framework; a one-page strategy articulation adapted from industry; a continuous decision-making process; a strict alignment of resources to strategic priorities; regular accountability reviews; and a genuinely inclusive engagement of the entire staff in fostering innovation aligned with planning, experimenting, and executing the strategy.

## THE FIRST FIVE DECADES: WORLD WAR II THROUGH THE COLD WAR (1942-1991)

Over its first 50 years, APL enjoyed a relatively stable working and financial relationship with its primary sponsor, the US Navy, and focused to a great extent on the steadily advancing naval and strategic threat posed by the nation's principal adversary, the Soviet Union.

As mentioned, APL was founded with the unitary mission to develop and operationalize an advanced munitions fuze to counter enemy air power in World War II. It was commonly understood that the Laboratory would be disestablished when the mission was achieved or the war ended, whichever came first. The first Lab director, Dr. Merle A. Tuve, clearly expressed that laser focus and urgency in his running orders to the staff: "I don't want any damn fool in this laboratory to save money. I only want him to save time. We don't want the best unit, we want the first one. . . . The fina l result is the only thing that counts, and the criterion is: Does it work then . . . Don't forget that the best job in the world is a total failure if it is too late."$^{6}$ Another culture-creating quote from Tuve doubled down on the entire organization's foundational commitment to the operational effectiveness of the new radar proximity fuze: "Our moral responsibility goes all the way to the final battle use of this unit; its failure there is our failure regardless of who is technically responsible for the causes of the failure. It is our job to achieve the end result." 6

As the war ended, related and emergent threats in naval warfare motivated the Navy to continue to support R&D at APL, and the Lab responded with evolutionary and expansionary follow-on innovations that helped the nation build an unrivaled naval force. It was during this period that APL achieved six of its historical defining innovations: the radio proximity fuze, Navy surface-to-air missiles, the Transit satellite navigation system, Navy phased-array radar, advanced sonar arrays, SATRACK ballistic missile testing, and the Tomahawk cruise missile weapon system.

While some diversification beyond the Navy occurred during this era, it was limited by a long-standing policy decision to restrict the Laboratory to first 2,600 and later 2,800 employees to ensure that APL would remain an elite R&D organization, working on only the most critical challenges facing the Navy. In practice, diversification was implicitly initiated at the request of Navy officials who referred the Laboratory to other national security sponsors as a systems engineering and technology innovator that could not only develop solutions to clearly specified problems but also collaboratively match government needs to science and technology solutions, often through innovative applications of technologies that had first been developed for the Navy. New non-naval innovations during this era included taking the first photo of Earth from space; developing telemetering technology, a modulated molecular beam mass spectrometer, and attitude stabilization for satellite tracking; and conducting Army ballistic missile testing.

## THE FIRST DISRUPTIVE DECADE: THE POSTCOLD WAR "PEACE DIVIDEND" (1991-2001)

National defense spending reductions, popularly known as the "peace dividend," had a disruptive effect on the Laboratory's 50-year-old partnership with the Navy and forced APL to adapt its business model in response. Soon after the breakup of the Soviet Union in 1991, the Department of Defense aggressively cut operating forces and civilian headquarters staff, reduced procurement funding, and closed or consolidated many military bases. Even though R&D budgets were generally stable during this decade, the broad reduction in funding for national security naturally led to an increased sense of competition among commercial industry and national laboratories for opportunities in R&D to replace reductions in more traditional manufacturing and procurement, as well as opportunities to gain an edge for subsequent production of systems related to successful research programs.

Commercial firms advanced a position that continuing sole-source awards to national laboratories prevented them from demonstrating that they could conduct R&D as well as or better than some national laboratories, and they further argued that not only should new R&D be competed, but some existing, long-term national laboratory roles should be as well. Perhaps the most disturbing trend, observed by then director Carl Bostrom, was that the Laboratory was being treated more like a contractor than a partner, which could hurt its ability to continue to serve as an innovative national resource. The Lab was at its best when presented with something that did not work and then allowed to both find and fix the problem rather than be told what to do. 7

When Gary Smith took over as director in 1992, working closely with APL leaders and armed with candid sponsor feedback, he initiated an APL improvement

initiative that included procedures that led to more timely responses to sponsors, more efficient teamwork, and streamlined processes to reduce costs.$^{5}$ As well, it was necessary to increase sponsor engagement calls to familiarize traditional and new sponsors with APL capabilities because they had lost significant corporate memory as senior civilian staff levels were reduced and increasingly replaced with active-duty military officers for relatively short-term assignments. But by early 1995, it was apparent that these measures would not be enough to adapt to the reduced funding and dynamically competitive environment. Discouragingly, APL found that it needed to downsize by about 10% and resolved to diversify beyond its Navy sponsors.

This controversy over competition for R&D opportunities was partially resolved in 1995 when the Office of the Secretary of Defense for Acquisition, Technology, and Logistics, or OSD (ATL), established complementary University Affiliated Research Center (UARC) and Federally Funded Research and Development Center (FFRDC) management plans. These plans specified core competencies that each type of organization had to maintain. As those competencies were needed, the plans authorized government sponsors to award sole-source contracts to UARCs and FFRDCs as established national resources. While the plans validated sole-source contracting under certain conditions, especially to avoid conflicts of interest, they did not allocate funding, and therefore some of the work APL previously did migrated to industry. But this new identification of APL as a UARC partially offset those declines, enabling the Lab to establish new program areas such as transportation and command, control, and communications, which diversified its sponsor base, energized critical staff members, and provided exceptional value to new sponsors.

To better position the Laboratory long term, and to find new ways to apply existing staff expertise toward a more diverse set of emerging national challenges, Smith initiated the first centrally managed, wide-ranging strategic planning effort. The 1998 strategic plan identified 21st-century challenges that APL could undertake as a UARC and that would expand the sponsor base into new areas while allowing the Lab to continue to make critical contributions to critical challenges for legacy sponsors. Indeed, three of APL's recognized defining innovations-the Cooperative Engagement Capability, ballistic missile defense from the sea, and low-cost planetary exploration-came to fruition during this decade.

The strategic planning effort resulted in new and accelerated program development, perhaps most notably in the areas of national ballistic missile defense and infocentric operations. Sponsor engagement efforts were bearing fruit such that the long-standing, now self-imposed limit of 2,800 staff members was set aside, and by 2001 the Laboratory's staff numbered 3,400. However, growth and mission impact of the new programs

were not uniform across the Laboratory's several technical departments. Reflecting the current sponsor base and areas of deep expertise, strategies and business plans had been primarily developed by departmental organizational teams. While this strengthened the operating posture of the Laboratory in aggregate, APL could still be characterized as a loosely tied confederation of independent departments rather than a fully integrated organization responding to a unified vision and strategy.

In the fall of 1999, the Johns Hopkins board of trustees announced that Richard Roca, a vice president at AT&T Bell Laboratories, would become APL's director. Roca, who had been the director of strategic planning during the Bell Systems divestiture that created the "Baby Bell" regional phone service companies, knew well the value of vision and strategy. During his first three months, he met with APL leaders, staff members, and government sponsors to discern whether the Lab should focus on diversification beyond its traditional sponsor base, which deeply depended on the Laboratory. What he heard convinced him that APL should "stick to its knitting," which now included infocentric operations, but should also be sufficiently flexible and agile to accommodate new sponsor needs when critically necessary to the nation, with success always defined as whether APL was making "critical contributions to critical challenges." Picking up on the insights in the 1998 strategic plan regarding a global trend toward unconventional warfare, he also moved to support nascent programs to counter biological, chemical, and nuclear national security threats. And in response to the growing importance of IT infrastructure and cyber defense, he established a chief information officer, an information technology department, and a cyber-focused business area. 5

The feedback that Roca received from the sponsor community was not all positive. While it was recognized that APL did amazing, impactful things, he heard that too often work was isolated in organizational silos. He thought that a sponsor should hear the best solution that all of APL could bring to a problem, not just one solution from one part of the Lab. To help the Lab think and work as a united entity, Roca decided that the role of a department should be to provide technical expertise and resources, and business areas-a new program-related matrix structure that he created-would assemble expertise from various departments to accomplish specific goals for each sponsor. An additional benefit of the business area construct was its potential to develop future Lab leadership.$^{5}$ The concept of business areas, today known at the Lab as mission areas, has endured as a key organizational construct.

The recognition of APL as a UARC and the Lab's initial strategic plan, business practice modernization, and new focus on diversification and making critical contributions to critical challenges all positioned APL well for the future.

## NEW STRATEGIES FOR NEW ADVERSARIES (2001-2010)

The horrific attacks on the Twin Towers and the Pentagon on 9/11 led to a national mobilization against terrorism, along with sharp increases in defense and intelligence agency funding for operations and rapid fielding of advanced technology. APL quickly formed cross-organizational teams to meet new and unexpected challenges; new sponsors fast-tracked many of the Lab's security-related programs; and over the next several years, the program portfolios in homeland protection, what became known as cyber operations, and special operations forces expanded in response to the growing importance of intelligence and networking capabilities.

Staffing levels grew quickly to meet critical mission needs, providing both opportunities and challenges for the Lab. With rigorous new business practices instituted by Roca, enterprise service expenditures were held flat to achieve economies of scale as the sponsored work grew. This enabled APL to allocate surplus funds to sorely needed new facility construction, advanced laboratory equipment, and greater investment in internal Independent Research and Development (IRAD) funding to explore emerging problems and technologies. A particular challenge was prioritizing among diverse sponsor needs in this era of advancing threats to homeland security and countering terrorism abroad-all of which were presented as urgently needed from the sponsors' point of view. The still-fresh memory of the funding challenges of the previous decade discouraged many APL managers from turning down new opportunities, which accelerated growth and put pressure on talent acquisition and infrastructure.

Roca led the development of a new 2004 strategic plan (later updated in 2008) to cope with the rapid growth and diversity of national challenges, requiring each of APL's 14 business areas to develop detailed business execution plans that sought to reconcile forecasts of programmatic growth with availability of staff expertise and necessary facilities. However, these attempts at rigorous planning and limiting staff growth were only partially successful in the face of incessant and emergent sponsor demands for advanced and rapidly fieldable technologies-which APL delivered again and again, often at a very highly classified level. While national security budgets increased by over 100% during this decade, the Laboratory's growth control efforts successfully limited its staff increase to about 50%, reaching 5,100, by 2010. This restraint to limit new work to critical challenge areas would mitigate the effects of the next storm, unlike for organizations that opportunistically rode the full force of the national security funding wave.

By early 2010, according to key measures, the Laboratory was in excellent shape from a business and technology perspective. Mission areas were providing

sponsors with expertise they could not find within the government or industry, the Laboratory was financially healthy, and its culture-with a focus on doing the right thing while solving problems of national interest-was admirable.

## PREPARING FOR THE STORM: STRATEGY IN ACTION (2010-2012)

But storm clouds were forming. As the decade began, the economy had become volatile, and with pressure to reduce federal budgets, nontraditional organizations sought defense funding at the same time government agencies were in-sourcing work to avoid downsizing. The Department of Defense (DoD) began to look to Silicon Valley for cost-effective and innovative solutions, bypassing the long-established national laboratories that were now perceived to be inflexible and bound by requirements.

Ralph Semmel, selected that year as APL's director, was convinced that APL needed a bold strategy for thriving in a world where connectivity among nations, cultures, and adversaries was becoming seamless, and where the pace of science and technology was accelerating chaotically. APL would need to be even more agile and connected and would need to increase collaborations with commercial industry. Every staff member would need to be empowered to innovate and develop potentially disruptive solutions to critical challenges. 5

APL leaders met to decide on a path forward and determined that this confluence of turbulent times for national security and federal budgets, the changing innovation landscape, and a new director offered a unique opportunity to strategically reset the Laboratory and prepare it for the coming storms-and beyond. As a result, the EC committed to developing a bold new strategy that the entire organization would follow.

The strategy and its implementation system comprised four interrelated elements, depicted in Figure 1 and described in more detail below.

## Capturing Actionable Strategy in Cascading Vision, Strategic Focus, and Execution Priorities

While participating on a government advisory board, Semmel saw how the networking and telecommunications firm Cisco had expressed its strategy on a single page: the VSE, for vision, strategic focus, and execution priorities.$^{8}$ A more mature version of the original Cisco VSE construct can be found online in bmc's The Business of IT Blog .$^{9}$ He resolved to try it out at APL. Not only could the VSE be easily shared and followed by the staff, but its brevity would serve to focus the EC as it developed this first high-level strategy product. The guidance was straightforward:

Figure 1. Strategy and its implementation system comprising four interrelated elements.

<!-- image -->

- · The vision would be crisp, inspiring, and focused on the longer-term future and include the value proposition for the organization.
- · The strategic focus areas, or SFs, would cover the next three years and include key decisions and directions that would guide fulfillment of the vision.
- · The execution priorities , or EPs, would be measurable activities implemented over the next year to realize the SF areas; they could include actions as well as critical decisions.

The executive team adopted the first APL VSE, shown in Table 1, in 2011. The strategy did not stop at the highest levels; it cascaded into tailored VSEs for each sector, department, and mission area (formerly referred to as business areas). The entire Lab adopted the process and the broad discussions necessary to converge on strategic priorities, and while the format has been refined, this one-page capture of vision, SF areas, and EPs persists today.

One feature that became important to the success of the VSE process in formulating the Lab strategy was widespread participation in the developmental process. As the EC met to contemplate successive VSEs, it began considering inputs from APL's corporate Board of Managers, external experts, and organized groups within the Lab. These included the other executive forums and even individual staff members, as well as purposely selected issue teams. This latter approach became especially successful. That is, teams of staff members nominated for their executive potential were tasked with developing strategic ideas to shape the future of the Lab. These teams became known as the "X,Y,Z" teams, and the EC dedicated a day to hearing their inputs. As one example attributed to their inputs, a strategic thrust that evolved

Vision: As a premier nonprofit research and development institution trusted by government and industry, make highly innovative, affordable, and timely contributions to critical challenges in national security and space.

Table 1. APL's first VSE, adopted in 2011 for fiscal year (FY) 2012

|    | Strategic Focus (FY2012-FY2014)                                                                                                                                  | Execution Priorities (FY2012)                                                                                                                                |
|----|------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  1 | Increase the impact of our contributions across all of our  business areas                                                                                       | Enhance the technical excellence of our overall program  portfolio through an increased emphasis on innovation,  affordability, and timeliness               |
|  2 | Place special emphasis on highly visible and high-risk  challenges that span our traditional sponsor and mission  boundaries                                     | Focus Lab resources to ensure success of PTSS [Precision  Tracking Space System] and to develop concepts for solutions to  the Navy's anti-access challenges |
|  3 | Establish enduring trusted technical agent roles in cyber  operations and CBRNE [chemical, biological, radiological,  nuclear, and high-yield explosives] defeat | Establish trusted Navy relationships for cyber, with a focus on  10th Fleet                                                                                  |
|  4 | Identify and assess emerging national challenges for APL  contributions                                                                                          | Create and ensure initial success of a Special Operations  Business Area                                                                                     |
|  5 | Adapt the enterprise to be robust and agile in the face of  shifting national priorities                                                                         | Transform the organization to increase flexibility, eliminate  unnecessary process, and significantly reduce costs                                           |
|  6 | Foster a Laboratory-wide culture that embraces creativity  and excellence                                                                                        | Create an innovation initiative in which business areas identify  and tackle "challenges after next"                                                         |

from one session became the basis of APL's National Health Mission Area.

A second critical feature of each VSE's SF/EP pairs was that they include no objectives related to revenue or staff growth. Instead, the focus was always on impact toward the vision, with the underlying assumption that necessary resources would become available to compelling initiatives through the natural competition for ideas.

But how to score success? If the expectation was that 100% achievement of the set of EPs was the standard, then easily achievable EPs could be offered up to ensure

success. So, Semmel set a 50% success criteria threshold to encourage boldness and willingness to fail in trying.

However, simply having a strategy, communicating it, and measuring its execution were not enough; implementation had to have a bite for leaders and staff members to take it seriously and live by it. Semmel reasoned that the implementation had to have consequences for allocation of scarce resources, executive accountability, and decision-making. These additional three elements of the strategic framework were quickly added and implemented for 2012 and each subsequent annual cycle.

Table 2. APL's VSE for FY2020

| Vision: Create defining innovations that ensure our nation's preeminence in the 21st century.   | Vision: Create defining innovations that ensure our nation's preeminence in the 21st century.                                                      | Vision: Create defining innovations that ensure our nation's preeminence in the 21st century.                                                                                                          |
|-------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Strategic Focus (FY2018-FY2020)                                                                 | Strategic Focus (FY2018-FY2020)                                                                                                                    | Execution Priorities (FY2020)                                                                                                                                                                          |
| 1                                                                                               | Develop bold next-generation national security initiatives  in each sector that have the potential for game-changing  impact                       | Incorporate breakthrough ISR&T [intelligence, surveillance,  reconnaissance, and targeting] concepts in a resilient and  modular framework that enables military operations in  contested environments |
| 2                                                                                               | Shape and lead disruptive opportunities in civil space that  will result in new groundbreaking missions and national  capabilities                 | Develop an APL-led mission model that enables a new  paradigm for space exploration                                                                                                                    |
| 3                                                                                               | Develop and implement revolutionary cyber situational  awareness and defense capabilities to enhance resilience in  naval platforms                | Demonstrate a capability to provide response options leveraging  cyber situational awareness across multiple subsystems                                                                                |
| 4                                                                                               | Become a transformative force in the biological sciences for  solving national security and global health challenges                               | Create a framework for the government to identify, assess, and  mitigate potential biological threats to national security and  public health                                                          |
| 5                                                                                               | Establish APL as the recognized leader in critical emerging  innovation ecosystems                                                                 | Develop the analytical foundation for a war game to inform  policy and programmatic decisions necessary for success in  seabed warfare                                                                 |
| 6                                                                                               | As part of One University [JHU initiative], become a  trusted partner in new educational initiatives, research  programs, and development pursuits | Design and deploy the delivery component of PMAP [Precision  Medicine Analytics Platform], with a focus on providing data- driven insights into patient prognosis                                      |
| 7                                                                                               | Be a model organization for innovation, inclusion, and  empowerment                                                                                | Establish a Lab-level innovation challenge that engages and  fosters professional growth among our early-career staff                                                                                  |

While the basic framework has remained the same, the annual VSE has evolved over time, with improvements to clarity and succinctness, explicit alignment of EPs to SFs areas, and hierarchical VSE connection, as can be seen in the Laboratory VSE for fiscal year (FY) 2020 (Table 2).

## Aligning Resources with Strategy: The Integrated Investment Plan

The spending of Laboratory contractual revenue is broken into two broad categories: "direct" expenses, which are directly associated with executing work for a sponsor, and "indirect" expenses, which support enterprise-wide activities, maintenance, or investments needed to sustain the organization in its core purpose. These indirect expenses are further broken down into routine overhead, program development (IRAD, bid and proposal, and sponsor engagement), and capital funds. When APL introduced the VSE, indirect expense budgets were managed in a distributed manner throughout the organization, and not explicitly aligned with strategic priorities. At the Laboratory level, overall budgetary planning of routine overhead and capital funds was the purview of the assistant director for operations, while the assistant director for programs handled allocation of program development funds.

To ensure that resources would be available to execute the VSE, Semmel established an investment strategy team (IST). This team is chaired by the chief strategy officer (later dual-hatted as the assistant director for programs) and includes the other assistant directors, the chief financial officer, and the chief of staff. It is charged with developing an annual integrated investment plan thatbased on proposals from sector and department leadership teams-aligns the allocations of all indirect funds with the strategic priorities, emphasizing the EPs of the VSEs.

Each sector, department, and mission area's budget allocation is fixed at the same level for three years. Reserves representing about 20% of available indirect funds are held back and allocated annually according to competing strategic needs. And to acknowledge the evolution of priorities among organizational elements within the Laboratory, in alternating three-year intervals, the baseline allocations for program development, capital, and overhead funds to each area are reduced by 10%, 10%, and 5%, respectively, and then reallocated among the areas in accordance with strategic priorities.

This fiscal and budgetary accountability has brought strategy to the forefront of decision-making while also providing a significant degree of agility to respond to emerging needs.

## Reviewing Portfolios for Accountability

Semiannual portfolio management reviews (PMRs) hold the executive for each mission area accountable for

properly executing their strategy, being a good steward of the investment resources allocated by the IST, and most importantly, enhancing the impact and quality of their mission area's direct-funded programs.

To provide uniform structure and efficiency to the PMRs, the outline for each session is clearly specified:

- 1. Sector and mission area VSEs
- 2. Quad-chart summary of mission area business status relative to strategy
- 3. Integrated investment plan-related accomplishments
- 4. Portfolio analysis
- a. Strategic importance of the work
- b. Alignment relative to the UARC mission
- c. Transition plans for misaligned programs
- 5. Quality management
- 6. Sponsor/customer feedback
- 7. Progress toward VSE EPs
- 8. Issues

The heart of each PMR is the portfolio analysis, which has three key elements of accountability. Aligning the work portfolio with the mission area's VSE provides insight into the strategic importance of new and ongoing sponsored work. Recognizing the Laboratory's special status as a UARC, executives discuss disposition of any programs that no longer align with the intended role of DoD UARCs. And finally, in the interest of continually strengthening the mission area's work portfolio, mission area executives are obligated to identify the least impactful 10% of their portfolios as candidate programs to be transitioned, either to commercial industry or government, or phased out. This directive was later revised to remove the characterization of "least impactful" to recognize that candidate programs may have been successful and were now mature enough for transition to programs of record. In practice, 2-5% of each mission area's portfolio is transitioned annually through this process.

These PMRs close the loop between establishing and executing the strategy, thereby creating real and visible accountability throughout the organization.

## Setting a Strategic Decision Agenda for Continuous Planning

While the EC performed well together in making operational decisions-that is, when making decisions on internally oriented tactical issues-it was still finding its way when tackling primarily externally oriented and strategic topics. It often took more time to arrive at strategic decisions. And some decisions were made without all members having a deep understanding of

the issue at hand, which inhibited full commitment and follow-through across the organization.

Semmel next leveraged a 2010 JHU deans' strategic planning retreat to help the EC refine its approach to strategic decisions. These discussions introduced an intriguing Harvard Business Review paper, "Stop Making Plans; Start Making Decisions."$^{10}$ The authors, Michael Mankins and Richard Steele, had developed a powerful method for identifying strategic issues and making effective decisions in a collaborative environment (Figure 2).

Mankins and Steele observed that most strategic planning is an annual (or even aperiodic) process and most often focuses on individual business units-which is how previous APL strategic planning efforts had been implemented. However, they discovered that executives actually make important strategic decisions outside of the strategic planning process, unconstrained by the calendar or organizational boundaries. Their research found that companies with standard strategic planning processes and practices make just two to three strategic decisions per year, while those that follow a continuous strategic decision-making process make more than double the number. Acknowledging this finding, their approach provides a discipline for identifying strategic

issues and making strategic decisions in a timely, collaborative fashion.

While APL had adopted the VSE process, the challenges in identifying the strategic decisions that fed the VSE and focusing the EC consistently on strategically important issues remained. This continuous, decision-oriented planning approach had promise. Like the VSE, it was deceptively simple:

- · Periodically identify a set of potentially strategic issues.
- · Prioritize the issues relative to importance and timing for decisions.
- · Consider each strategic issue over two sessions:
- 1. Data and alternatives (D&A)
- 2. Decision-making

In preparation for its October 2010 strategic planning meeting, the EC polled its members to identify the set of strategic issues the group should address during the coming year. Out of this poll came 37 candidate strategic issues, of which 11 were sufficiently time critical that they were decided in the first year.

Figure 2. Mankins and Steele method for identifying strategic issues and making effective decisions in a collaborative environment. (Reprinted by permission of Harvard Business Review . Adapted from p. 83 from "Stop Making Plans; Start Making Decisions" by Michael C. Mankins and Richard Steele, January 2006. Copyright ©2006 by Harvard Business Publishing; all rights reserved.)

<!-- image -->

The fundamental insight embodied in the construct was the two-session consideration sequence. The purpose of the D&A session is to ensure that EC members are fully informed on the issue at hand and satisfied that a robust set of choices, spanning the full range of what is feasible, is offered. For complex topics, an expert team researches and presents the data, articulating a set of feasible alternatives and an accompanying analysis that identifies objective pros and cons for each alternative. During the D&A session, EC members may ask for more data, pose additional alternatives for the expert team to explore, and offer additional pros and cons to be analyzed.

In some instances, the decision is sufficiently obvious once the alternatives are presented that the second session, the decision session, can be waved off if all members consent. However, decisions are usually not permitted during the D&A session. During the decision session, the expert team addresses questions raised during the D&A session and is then usually dismissed so that the EC may openly debate and come to a decision that cannot be subsequently attributed to individual members.

One unexpected benefit of this two-session process became quickly apparent. The pause between the D&A session and the decision session enabled EC members to engage their own leadership teams in evaluating the decision alternatives. This often revealed diverse perspectives and, ultimately, more thoughtful decisions that were embraced by those deeper within the organization. But another unexpected pattern, this one concerning, also developed. Often, three alternatives were posedstatus quo, mild change, and aggressive change-and it became tempting to just pick the middle alternative. To combat this tendency, the expert teams have since been charged with being bold in developing highly innovative alternatives, especially with particularly complex issues.

Overall, the Mankins and Steele framework oriented the EC toward truly strategic decision-making and resulted in robust decisions that stood the test of time as the Laboratory adapted within an uncertain environment. Since implementing this practice in late 2010, APL has made an average of nine strategic decisions per year through 2022, addressing diverse topics such as new mission areas, cost-control measures, IRAD investment posture, cybersecurity, business continuity planning, technology transfer and commercialization, strategic relationships, major reorganizations, campus development, growth control, and hybrid work environments.

In addition to adopting this planning construct, APL's "storm preparation" in 2011-2012 included some other initiatives. A steady stream of thought leaders was brought into the Laboratory to interact with the staff and explore diverse perspectives on emerging challenges, not yet fully apparent or understood, that the Lab would likely face. The most wide-ranging reorganization of the Laboratory's technical organizations and a

significant cost-control initiative positioned the Lab to better respond to the external environment and address evolved misalignments.

In the initiative most visible to the entire staff, Semmel in 2010 charged Jerry Krill, assistant director for science and technology, to launch an integrated set of innovation initiatives. These initiatives were based on a series of experiments involving interested staff members and supported ideas that might cross organizational boundaries in novel ways or be too forward-looking to find internal or government financial advocates.

While Semmel celebrated this tremendous progress, he also knew that a truly long-range vision-one that extended over 25 years to the Laboratory's 100th anniversary-was needed to inspire the organization to become fully strategy driven and to ensure that the commitment would take hold and last. But the long-expected storm was nigh, and the long-range vision and strategy would have to wait.

## THE PERFECT STORM OF 2013

The storm arrived with a vengeance in three intersecting waves, all in 2013: mandatory indiscriminate federal budget cuts through a process known as sequestration, associated delays in renewing APL's foundational UARC contract with the Navy, and a federal government shutdown that suspended many government services and triggered widespread employee furloughs in government and the private sector alike.

When Congress failed to reach agreement for FY2013 on how to implement spending cuts mandated by the Budget Control Act of 2011, a trigger mechanism in the bill, known as sequestration, was activated to reduce the rate of increase in spending across the board.$^{11}$ The sequestration effects had been looming for over two years by then, as several temporary measures that delayed the spending cuts were passed. But with Congress at an impasse, the cuts were ultimately scheduled for implementation on 1 March 2013. At the same time, the Laboratory's principal omnibus contract with Naval Sea Systems Command (NAVSEA) was up for a ten-year renewal worth just over $6 billion in potential, but not guaranteed, funding. But with the uncertainty of funding due to the impending sequestration, such a large, sole-source contract had increased visibility, and senior Navy officials were reluctant to approve it in that uncertain environment, even though the terms were nearly identical to the expiring NAVSEA contract. If the contract were not renewed, APL could face irrecoverable reductions in force starting in March and accelerating from that point on until alternative contracting mechanisms could be put in place to continue critical work for Navy sponsors.

Recognizing the seriousness of the sequestration and contract renewal confluence, the EC established

a strategic task force to examine the best ways to control costs while enhancing the Lab's value to the Navy. While difficult cost-reduction decisions were necessary in a number of areas, including retiree medical benefits, construction, and operational overhead, the EC knew it needed to continue to attract and retain a world-class workforce, so it made no changes to active staff members' benefits or compensation. Additionally, it made the strategic decision to protect investments in innovation. As a result, APL was able to meet its goal to reduce its cost to deliver by 5% relative to inflation. In fact, as the effects of long-term measures kicked in, APL reduced costs by over 10%, while holding voluntary staff turnover to the remarkably low level of less than 5% and preserving the innovation programs.

Finally, with strong support from all of APL's immediate Navy sponsors, the foundational UARC contract was awarded in mid-February 2013. However, because of the uncertain impacts of the underlying sequestration-related funding reductions, planning for the foreseeable future remained constrained.

The third wave emerged in the form of a "funding gap" between the two chambers of Congress on how to balance long-term appropriations and the federal debt limit. Ultimately, the impasse led to a federal government shutdown on October 1, 2013, for 16 days, the third longest in US history. The threat to APL's cash flow was significant, as approximately 800,000 federal employees were indefinitely furloughed and another 1.3 million were required to report to work without known payment dates$^{12}$-including government fiscal offices that process payments for valid contract expenses to organizations like APL. In an extraordinary all-staff meeting two weeks into the shutdown, Semmel announced that the Laboratory would continue to keep all staff members working and paid through the shutdown for at least three months by using a large line of credit and additional loans as necessary. Staff members, expecting a furlough announcement, were greatly relieved, inspired, and energized by the Laboratory's full commitment to its staff and willingness to assume considerable financial risk in such a time of turmoil.

With existential threats averted, and as the storm abated, Semmel decided that it was time to complete the full long-term vision and strategy, the critical and capstone fifth element of the system.

## BUILDING THE CENTENNIAL VISION

Semmel had a deep appreciation for the Collins and Porras method of building an organization's vision, as articulated in the 1994 landmark strategy book Built to Last ,$^{13}$ and had long planned to apply it rigorously to APL. During a six-year research project at Stanford, Collins and Porras studied 18 exceptional and long-lasting companies, comparing them not to the

Figure 3. Collins and Porras vision framework. Reprinted by permission of Harvard Business Review . (Adapted from p. 4 of "Building Your Company's Vision" by James C. Collins and Jerry I. Porras, September-October 1996. Copyright ©1996 by Harvard Business Publishing; all rights reserved.)

<!-- image -->

average performance of their business sectors, but rather to their very top competitors to isolate what made them truly great and lasting. The principal finding was that "companies that enjoy enduring success have core values and a core purpose that remain fixed while their business strategies and practices endlessly adapt to a changing world. . . . This rare ability to manage continuity and change-requiring a consciously practiced disciplineis closely linked to the ability to develop a vision." 14

Collins and Porras go on to describe how to discover an organization's core ideology and develop an envisioned future , which together form the vision framework (Figure 3). Each consists of two distinct elements. The core ideology consists of (1) core values , a set of guiding principles and tenets; and (2) the core purpose , the organization's most fundamental reason for existence. The envisioned future consists of (1) a 10- to 30-year Big Hairy Audacious Goal (BHAG) ; and (2) a vivid description , or a narrative of what successful achievement of the BHAG would look like.

APL's effort to build these elements into its strategy process began in earnest during one of the EC's semiannual 2.5-day planning meetings, this one in October 2014. Tim Galpin, assistant director for strategy and programs, had charged a strategy working group with critiquing APL's 2008 strategy relative to the Collins and Porras model and suggesting alternatives for the core ideology and envisioned future elements to formulate the vision framework. While the daylong discussions were a good introduction to building the vision, it was clear that intense and extended sessions would be required before significant progress could be made. Therefore, Galpin convened the EC for several lengthy and focused strategy working sessions over the next six months as preparation for spending the majority of the next planning meeting on fully developing the vision framework elements.

It would take until April 2016 to finalize the vision framework's four elements and to plan the rollout to the entire staff. Fortuitously, the Laboratory's 75th anniversary was just around the corner, on March 10, 2017, and the new strategy, which was extended to about 25 years, became known as the Centennial Vision since the time frame for achieving the BHAG aligned with the Laboratory's 100th anniversary. The four elements of the Centennial Vision and some interesting points about their development are discussed below to illustrate the journey and the challenges of APL's strategy development.

## Core Purpose

Many candidate core purpose statements had been proposed by the strategy working group and EC members, and four had each gained a degree of traction. Reviewing these statements illustrates the progression of thought needed to produce a simple and compelling statement:

- · Enhance the security of the nation through the application of science and technology.
- · Overcoming national challenges through applied research and development.
- · Securing the nation's well-being through science and technology.
- · Critical contributions to critical challenges .

The fourth statement was a clear choice because of its familiarity and resonance with the staff. It had been in use for over a decade, the staff knew what it meant, and it was a statement that everyone could recognize in their own work. And it was short and easy to remember. The other three statements unnecessarily included the means by which the core purpose was to be achieved. To APL staff, a critical challenge is understood as a hard problem whose solution has an important bearing on national security, military readiness, space exploration, national health, or on the advancement of fundamental science or engineering. CC2CC, as it is sometimes known, also reflects the staff members' pride in being a part of an organization that exists to ensure that our nation has access to a dedicated and powerful team of technical experts who are prepared and unafraid to tackle the hardest problems of national importance.

## Core Values

Developing crisp and inspirational statements of core values was more challenging. Keeping in mind the Collins and Porras enjoinder that core values must be discovered rather than aspirational, and that no more than five or six could be truly central values, the EC widely engaged extended focus groups. Terms and phrases that emerged included integrity , excellence , technical excellence ,

innovation , service , impact , respect for people , challenging and supportive work environment , and serving the nation . After much deliberation, the EC synthesized the inputs into five short statements:

- · Unquestionable integrity
- · Trusted service to our nation
- · World-class expertise
- · Game-changing impact
- · A highly collaborative, fulfilling (even fun!) environment

Interestingly, the first core value had been "unquestioned integrity" through many drafts until one executive observed that a recently disgraced public figure had been revered as having unquestioned integrity-and then some unsavory incidents came to light. Wouldn't we really want to have "unquestionable" integrity? This seemingly small distinction resonated deeply with the staff, and the story underlines how seriously the EC worked to discover this set of core values.

Another late change was the insertion of "even fun!" into the fifth core value. We were reminded that APL staff members have always had a good bit of fun-the fun of working in tightly knit teams that forge close and lasting friendships and the fun of successful accomplishments that make a difference to the nation. Once revealed, the simple "even fun!" phrase had the unexpected effect of unleashing a surge of excitement and creative activities throughout the Laboratory, often led by early-career staff.

## Big Hairy Audacious Goal

The BHAG associated with the 2008 strategy was "Become the premier technological institution sought by government and valued by industry for providing practical solutions to the nation's critical challenges." And the vision statement for the then-current FY2015 VSE was "Strengthen our nation through transformative innovation and trusted technical leadership in national security and space." Neither statement cleanly met all the Collins and Porras criteria for a BHAG: that it be clear and compelling, have a clear "finish line," drive a unified effort, be a stretch goal that should take a good 20 years to achieve, and of course be exciting. The 2008 BHAG focused on a subjective assessment of how we wished to be recognized as an organization, and the 2015 version was similarly flawed in that it provided a direction but not a goal that could be easily recognized as having been achieved.

A breakthrough occurred when the EC rallied around the concept of a defining innovation and expressed it as a BHAG: " Create defining innovations that ensure our nation's preeminence in the 21st century ." But what is a defining innovation ?

The proximity fuze of APL's origin story precipitated an inflection point. This, in fact, is the paramount characteristic of all defining innovations. Innovations, in general, are novel capabilities built on new or existing science and technology, but a defining innovation is a dramatic advance that completely changes the way we live or operate. Defining innovations are so profound that returning to the way we lived before the achievement is unthinkable. For APL, a defining innovation is a critical contribution to a critical challenge that forever changes our understanding of what is normal. Like all innovations, a defining innovation might involve the invention of a new scientific idea or principle, or it might arise from the ingenious use of existing technologies.

## Vivid Description of the Envisioned Future

Painstakingly, the EC prepared a vivid description of the envisioned future associated with achievement of the BHAG at the Laboratory's centennial, including the culture and environment that will need to exist to meet the goals:

When we celebrate our centennial, APL will be a treasured national resource, widely recognized for our technical leadership and bold, previously unimaginable technical solutions to the nation's most complex national security and space exploration challenges. Always anticipating the future, we will also be providing decisive advantage to the nation in complementary new areas. Never losing sight of why APL was created, we will be nurturing a culture of experimentation, embracing risk, and exemplifying what it means to be a trusted research and development laboratory. Furthermore, APL will be a magnet for the nation's top talent and a sought-after partner at the center of a vibrant innovation ecosystem. Finally, as an integral member of one of the world's finest universities, we will be sharing knowledge and technologies that benefit our society and the lives of people throughout the world.

## Table 3. Alignment of SFs to the vivid description

## Strategic Focus Area (FY2021-FY2023)

## Vivid Description

- 1 Develop bold next-generation initiatives in each sector that have the potential for game-changing impact
- 2 Shape and lead disruptive opportunities that leverage all dimensions of space to achieve groundbreaking national security capabilities
- 3 Create capabilities that will dramatically enhance national security by integrating demonstrated concepts and technologies from across APL
- 4 Create initiatives for sustainable contributions that address global challenges resulting from climate change
- 5 Become a national leader in biological security by anticipating and countering emerging biological threats

Always anticipating the future, we will also be providing decisive advantage to the nation in complementary new areas.

- 6 As part of One University, serve as a trusted partner and leader in JHU's artificial intelligence initiative
- 7 Be a model organization for diversity, inclusion, and empowerment

Furthermore, APL will be a magnet for the nation's top talent and a sought-after partner at the center of a vibrant innovation ecosystem.

Finally, as an integral member of one of the world's finest universities, we will be sharing knowledge and technologies that benefit our society and improve the lives of people throughout the world.

When we celebrate our centennial, APL will be a treasured national resource, widely recognized for our technical leadership and bold, previously unimaginable solutions to the nation's most complex national security and space exploration challenges.

Never losing sight of why APL was created, we will be nurturing a culture of experimentation, embracing risk, and exemplifying what it means to be a trusted research and development laboratory.

Figure 4. APL's Centennial Vision in its entirety.

<!-- image -->

The first sentence describes defining innovations, their impact on the nation, and the primary application domains for the Laboratory, while the second sentence encourages exploration in critical yet complementary domains. The third sentence characterizes the culture that will be needed, and the fourth sentence sets a high bar for the talent and collaboration necessary for this level of innovation. The final sentence explains the benefits and responsibilities associated with being part of JHU as a nationally recognized UARC.

Figure 5. The fully integrated system including the annual strategy implementation cycle and the Centennial Vision.

<!-- image -->

As Semmel unveiled the Centennial Vision (Figure 4) at an all-staff gathering, he summarized the sense of it with a now oft-quoted slogan: " Be bold! Do great things! Make the world a better place! "

With the complete vision framework in place, the annual strategy implementation cycle now had a long-term strategic foundation as its guide star. Just as the sector, department, and mission area VSEs flowed logically from the Laboratory-level VSE, now the overall VSE could be pegged to the vision framework. In the 2022 VSE, each of the seven SF areas aligns with one of the five statements in the vivid description of the envisioned future (Table 3).

And so, the annual strategy implementation cycle and the Centennial Vision can be illustrated as a fully integrated system (Figure 5).

## THE STRATEGY IN PLAY: INFUSING INNOVATION

The concept of innovation has been infused into all elements of APL's strategy.$^{15}$ The 2022 VSE, for example, includes such phrases as "Develop bold next-generation initiatives" and "Shape and lead disruptive opportunities." As mentioned, alongside the work to refine the strategy creation process, APL launched an integrated set of innovation initiatives. One of the first strategic decisions in 2011 was to transform a workplace bound by highly regulated practices into one of empowerment and measured risk-taking by eliminating the hundreds of documented policies and procedures down to essentials-ultimately reduced by 75%. The first to go was one of the most unpopular: a rule against Frisbee playing on one of the Lab's large outdoor gathering areas, the Central Green. Semmel announced the end of this policy while also unveiling the first major innovation initiative, Ignition Grants. At a town hall meeting, after describing the Ignition Grants program and the culture

shifts underlying it, he tossed out Frisbees branded to commemorate the new Ignition Grants initiative with Frisbee playing on the Green and adjourned the meeting by inviting everyone to take their Frisbees to the Central Green.

The Ignition Grants program of seedling funds was an experiment to encourage and stimulate innovative ideas and invite staff members to create game-changing concepts. The first Ignition Grants cycle proved popular, and staff members especially appreciated the trust implicit in the crowdsourced selection of winners. What began as an initial experiment has endured as one of the most popular innovation initiatives and led to the EC strategic decision to also establish a pair of much larger grants, Combustion Grants and Propulsion Grants, in 2015. These three levels of grants, known collectively as Project Catalyst, complement the traditional sponsor-oriented IRAD funds as a way to invite research into truly extraordinary ideas that are (perhaps yet) not in line with mission area strategies or sponsor timelines but just might yield a defining innovation.

## Enhancing the Management Framework

The EC realized the need to establish a new forum. APL already had two executive forums reporting to the EC. The Mission Area Forum of mission area executives, led by the assistant director for programs, coordinates program portfolios, sponsor needs, and opportunities for multi-mission collaborations. The Operations Forum of operations executives, led at the time by the assistant director for operations and now led by the chief financial officer, ensures efficient and effective operations of business, information technology, and human resources systems. However, the "line side" of the executive leadership, the managing executives, were not members of either forum but had the responsibility for staff development and technical excellence, with the vast majority of the staff reporting to them, directly and via middle management. The EC therefore established the Management Forum in 2011, led by the assistant director for science and technology, for the managing executives to collaborate in shepherding innovation and staff development.

## Expanding Space to Innovate and Collaborate

For one of the early Ignition Grant cycles the Management Forum suggested soliciting ideas for APL's next innovation experiment. The result was two proposals selected by the staff to develop a "maker space" and a facility to exercise design thinking, both ideas gaining increasing national popularity. The winning teams applied their Ignition Grant funds to develop an encompassing concept for a collaborative innovation center. The result, Central Spark, was unveiled in 2014. It included a design thinking studio, modeling and simulation and software app prototyping tools, and a maker

area including modular electronics and 3-D printers. Central Spark has proved so popular that in 2020 it was moved to a location with three times more space and equipment.

Central Spark gave APL leadership experience with open collaboration space at a relatively low cost, and the leadership team applied the lessons learned to the design of the next collaboration space, the Intelligent Systems Center. The "ISC" was designed to encourage resident researchers in robotics, neuroscience, autonomy, and information systems to collaborate. The ISC cost about ten times more than the original Central Spark. Lessons learned from the ISC then motivated the design of a new building, known as Building 201. It cost 20 times more than the ISC, with 263,000 square feet including 90,000 square feet of labs and collaboration spaces. In fact, Building 201 now houses the expanded ISC as well as most of the strategically redesigned Research and Exploratory Development Department. For subsequent building and renovation programs, APL has applied a menu of design options incorporating collaboration features across the spectrum of programs, facilities, and staff spaces according to their needs and the degree of security required.

## Rethinking Staff Performance Management

Another offshoot of the innovation strategy was a renewed look at the Lab's performance management process, a time-consuming end-of-year retrospective evaluation of every professional staff member. Recent research had indicated that the value of such a traditional process was not necessarily commensurate with the effort required. Semmel wondered whether excellence and innovation would suffer if the documentation-heavy process were replaced with a zero-documentation coaching approach. The Management Forum concluded that the coaching-centered approach should be tried. The experiment led to full adoption, and in the half-decade since revamping the process, staff performance has not faltered, and satisfaction with reviews and coaching has increased according to staff surveys.

## A DECADE OF RESULTS AND HARD LESSONS LEARNED

Since implementing the systems approach to strategy in 2010, robust innovation initiatives beginning in 2011, and the Centennial Vision in 2016, the Lab has enjoyed advances in measurable results and national recognition. Using the Mankins and Steele strategic

decision-making approach, the EC has made an average of nine strategic decisions annually, about three times that of companies that use standard strategic planning processes.$^{8}$ Even while the Lab has actively shed its lowest-impact work and reduced costs by over 10% relative to inflation, it has grown its staff by 60%- to over 8,000 in 2023-and has accelerated the number of staff members named as fellows in prestigious national-level professional societies. Other tangible results are summarized in the sections below.

## Direct Impact of Aligning Resources to VSE Priorities

The disciplined practice of aligning internal resources to strategic priorities as expressed in the VSE has resulted in new and accelerated innovations and high-impact contributions to the nation's most complex national security, space exploration, and health challenges. Two such examples resulting from the FY2020 VSE illustrate how this integrated systems approach works in practice and the resulting impact that has been achieved.

## Winning the Dragonfly NASA mission

In its 2015 Discovery Program selection process, NASA rated five APL proposals as selectable but did not select any of them to move forward. As a result, a precipitous drop in overall NASA funding to APL was looming. Therefore, in October 2016, Lab leadership created an out-of-cycle SF and EP pair (below) for FY2017 to evoke a strategy and corresponding resources to win a NASA mission competitively.

The charge to create a winning strategy included provision of program development funds to devise a winning proposal for a novel, affordable mission with acceptable risk. Resources were also allocated to ensure that the requisite development and testing facilities would be in place as a risk mitigation measure to strengthen the proposal. Recognizing NASA's strategic commitment to pursue the discovery of life elsewhere in the solar system, in accordance with the National Academy of Science's Decadal Survey, APL's Civil Space Mission Area proposed a novel mission in response to the New Frontiers Program's call for proposals. (New Frontiers is a consequence of APL's defining innovation to develop affordable planetary missions.) The proposed mission, called Dragonfly, featured a nuclear-powered dual-quadcopter to be landed on Saturn's moon Titan. It would fly through the thick Titanic methane atmosphere to high-interest surface locations where it would collect samples and test them for the presence of life. APL won funding for the proposal.$^{16}$ Paul Voosen, a writer for Science , noted that

Vision: Create defining innovations that ensure our nation's preeminence in the 21st century.

Strategic Focus (FY2015-FY2017)

Execution Priorities (FY2017)

- 2 Aggressively shape and pursue disruptive opportunities in civil space that will lead to at least one groundbreaking mission

Advocate and propose pioneering concepts for high-value planetary science and space weather monitoring

Vision: Create defining innovations that ensure our nation's preeminence in the 21st century.

## Strategic Focus (FY2018-FY2020)

## Execution Priorities (FY2020)

- 4 Become a transformative force in the biological sciences for solving national security and global health challenges Create a framework for the government to identify, assess, and mitigate potential biological threats to national security and public health

the mission "represents a calculated risk for the agency, embracing a new paradigm of robotic exploration to be used on a distant moon." 17

## Strategy Anticipating the Need for COVID-19 Situational Awareness

The FY2018-2020 SF and EPs for biological sciences (refer to Table 2; the relevant portion is repeated above) turned out to be prescient when the COVID-19 pandemic struck.

APL already had a decades-long history of collecting and curating medical data from both US state and international jurisdictions through the ESSENCE (Electronic Surveillance System for the Early Notification of Community-based Epidemics) and SAGES (Suite for Automated Global Electronic bioSurveillance) programs.$^{18}$ So, given the VSE-related provision of strategic resources and exploration of potential new roles, when Whiting School of Engineering faculty member Dr. Lauren Gardner began building the JHU COVID-19 Dashboard (which also became known as the JHU Coronavirus Resource Center), APL was equipped to step in, upon request, to validate, curate, and classify the data needed to scale the dashboard to the worldwide level as the trusted source of COVID's status. Further, APL began to develop algorithms to mine the data to identify resource needs, especially hospital beds, equipment, and consumables such as masks. APL was asked

to ramp up to support the technical team of the White House COVID Working Group with over 40 staff members. The JHU Coronavirus Resource Center data and APL-developed algorithms were leveraged, along with other government information, to prepare regular briefings for the president on the status of COVID (Figure 6) and became instrumental in the United States' ability to allocate resources to the counties across the country where they were most needed. The JHU Coronavirus Resource Center was identified by Time magazine as one of the best inventions of 2020.$^{19}$ As of this writing, the center's function has transitioned to the CDC and is being disestablished, having served the nation and world well during the emergency status of COVID-19.

## New Defining Innovations

As mentioned earlier, as APL celebrated its 75th anniversary, nine defining innovations were identified as the exemplars of contributions so significant that they changed the nature of their operational domain. They are the proximity fuze, Navy guided missiles, satellite navigation, Advanced Multifunction Array Radar, towed sonar arrays, satellite-based precision tracking of submarine-launched ballistic missiles, Tomahawk, the Cooperative Engagement Capability, and affordable planetary exploration.$^{20}$ These selections were each based on the retrospective conclusion that they, in fact, truly changed warfare and space exploration. For APL's

Figure 6. Members of the White House COVID Working Group, including President Biden, meeting in the Oval Office to review a COVID briefing book.

<!-- image -->

80th anniversary in 2022, the EC decided that it was time again to look back at game-changing innovations to determine whether any had by then risen to similar stature. Two additional defining innovations were identified and announced to the entire staff in early 2023 by Director Semmel, bringing the total number of defining innovations to 11.

## Ballistic Missile Defense from the Sea

Beginning in the early 1990s, APL responded to the critical challenge of proliferating ballistic missile threats by leading the development of the transformational technologies and experiments needed to demonstrate ballistic missile defense (BMD) from ships at sea. The resulting

Figure 7. USS Lake Erie (CG 70) launching the Standard Missile-3, which intercepted the satellite during the Burnt Frost mission. The missile struck a nonfunctioning US satellite as it traveled in space at more than 17,000 miles per hour over the Pacific Ocean. The nation called on APL, with its long experience with Aegis and Standard Missile, to make vital contributions to this critical operation. (US Navy image.)

<!-- image -->

Terrier Lightweight Exoatmospheric Projectile (LEAP) experiments proved that BMD technology could be integrated with the Navy's Aegis weapon system to "hit a bullet with a bullet" in space from the sea. APL's critical contributions opened the door for the Navy's central national role in BMD. The resulting impact is felt far beyond our nation's shores as BMD now provides enduring defenses at sea and ashore across the globe,

<!-- image -->

defending our allies and even engaging an errant satellite, during what was called Operation Burnt Frost (Figure 7), before it could deorbit and potentially cause civilian casualties.

## Planetary Defense

For more than a decade, APL engineers and scientists developed game-changing concepts and technologies to ultimately prove that it was possible to defend our planet from an asteroid on a potentially catastrophic Earth-impact trajectory. APL established the technological basis for planetary defense; solidified the domain as a research and development area at the federal level; played key roles in defining and exercising intra-agency and international coordination responsibilities; and captured worldwide attention by successfully completing the Double Asteroid Redirection Test (DART) mission in September 2022 (Figure 8), the first in-space demonstration of planetary defense technology.$^{21}$ In contrast with the other defining innovations, this one was solidified as a defining innovation in short order because of the national and global response to affirm that planetary defense was attainable.

## Innovations That Cannot Be Discussed

The EC also recognized and honored the fact that some classified projects, if they could be disclosed, would surely be identified as APL defining innovations as well. In addition to Director Semmel's recognition of these achievements during the 2023 strategy gathering of APL staff members, one blank poster accompanies those celebrating the 11 defining innovations in the hallway leading to the director's wing on APL's campus. It is a silent tribute to the family of special innovations that remain classified.

Figure 8. Left, the asteroid moonlet Dimorphos as seen by the DART spacecraft 11 seconds before impact. DART's onboard DRACO imager captured this image from a distance of 42 miles (68 kilometers). This image was the last to contain all of Dimorphos in the field of view. Right, members of the DART team celebrate in the mission operations center at APL on September 26, 2022. Along with viewers all over the world, they watched images livestreamed from the spacecraft showing that it successfully impacted the asteroid Dimorphos, completing the world's first planetary defense test mission.

<!-- image -->

## External Recognition

During 2020 through early 2023 alone, the Lab earned several national accolades for its innovation and desirability as an employer:

- · For five consecutive years, APL has been named to Fast Company's Best Workplaces for Innovators, including the inaugural list in 2019$^{22}$ and one year at number 3. 23
- · APL has been named one of Insider Pro and Computerworld 's top twenty "Best Places to Work in IT" for five years in a row, including being named in two categories in 2021$^{24}$ and three categories in 2023. 25
- · The APL team managing NASA's Parker Solar Probe mission was recognized by the American Institute of Aeronautics and Astronautics (AIAA) with the von Braun Award for Excellence in Space Program Management$^{26}$ in 2020.
- · JHU Whiting School of Engineering and APL researchers behind the Johns Hopkins Coronavirus Resource Center (CRC) were honored as Fast Company's Innovative Team of the Year for 2021.$^{27}$ The CRC was also named a Time Best Invention of 2020. 19
- · The Lab was named number 3 on Fast Company's 2022 World's Most Innovative Space Companies$^{28}$ list for building and managing NASA's DART spacecraft. 29
- · For two consecutive years, APL has won a Glassdoor Employees' Choice Award, ranking in the top 50 out of 100 US large companies on the Best Places to Work on the 2022$^{30}$ and 2023$^{31}$ lists. This award is based solely on feedback from employees, who anonymously complete company reviews about their jobs, work environments, and employers.
- · APL researchers earned two R&D 100 Awards in 2022$^{32}$ and one in 2023. 33

## Lessons Learned

The journey to becoming a fully strategy-driven organization with an exciting vision and systems implementation took about five years. Periodically stepping back and looking at lessons learned has been helpful in refining the process and in sharing insights with other organizations that have similarly sought to become strategy driven. APL learned ten hard-won lessons:

- 1. The CEO's ruthless commitment to aligning decisions with the vision and strategy is key to building a strategy-driven organization with a fully participative staff.

staff members themselves in experimentation to determine what works for the organization.

- -Strategic thinkers are scattered throughout most organizations, and many of them yearn for the fun and excitement of strategy development and the inclusivity that comes when they have a say in what the organization does and how it does it.
- -While concentrating strategy at the executive level feels efficient and timely, doing so can ignore valuable insights from other sources.
- 3. Without appropriate engagement, strategy has little value, impact, or relevance.
- -Participation and concurrence are important; otherwise, the strategy ends up as leadership's priorities, having to be explained repeatedly to rise above "normal" work priorities.
- -All staff members should (and deserve to) understand where the organization is heading.
- -Strive for the right balance between long-term goals and explicit actions tied to those goals.
- -Routinely discuss strategy with the staff, provide opportunities for input, align resource allocation to strategy, and hold the staff accountable for strategy execution to make strategy relevant.
- 4. Leaders focused on innovation must spend time interacting with the staff and explaining the nuances of their ideas and plans.
- -Run experiments with clear objectives and involving staff members to inform strategic decisions.
- -Encourage and provide plenty of opportunities for the staff to engage on strategy.
- -Schedule face-to-face time with executive teams.
- -Present strategy regularly. At APL, the director presents strategy twice per year to the entire staff.
- -Ensure that stakeholders regularly update leadership. Each APL mission area presents strategy updates and highlights to the Lab's Executive Leadership Team twice per year.
- 5. Executives want to focus on strategic issues but are sometimes hesitant to give up tactical control.
- -It is the responsibility of the executive team to tackle critical problems.
- -The executive team should identify potentially strategic issues, decide which ones are truly strategic, and explicitly delegate (most) others.
- 6. Managers can be more averse to losing resources than motivated by an opportunity to gain.
- 2. Strategy for innovation can and should be an exciting and substantive journey and must involve the
- -Promote enterprise behavior while ensuring that the best ideas are supported; avoid introducing unhealthy competition.

- -Allocate funding for exploration of new ideas. APL uses set-aside allocations and director's reserve annually for this purpose.
- -Reset baselines often. APL's resource baselines are reset every three years rather than annually to promote focus and progress on long-term goals.
- 7. There often is a reluctance to transition out of relatively lower-impact work to pursue potentially higher-impact opportunities.
- -Strategically, it is important for organizations to remain at the leading edge, but commitments to existing sponsors and comfort with existing work can lead to reluctance to embrace higherimpact opportunities.
- -Regularly review work portfolios and encourage tough decisions. APL actively phases out work by requiring executives to identify and explain their lowest-impact projects to the investment strategy team (IST) and develop their own transition paths or justification for retaining existing work.
- 8. Strategy should underpin resource allocation and performance assessment.
- -The first was a given, but the second had to be learned.
- -Both are needed to maintain strategic focus of the executive team.
- -A portion of each executive's above-base compensation is tied to achievement of at least 50% of the EPs in their organization's VSE (or VSEs if they have cognizance over one or more mission areas).
- 9. Embracing diverse perspectives and inclusion leads to new and novel ideas and approaches.
- -Leverage many different groups to develop a better, more inclusive, and accepted strategy. APL uses a participative process in which we iterate extensively and gather information from focus groups, but we do not get paralyzed by process or indecision.
- -To emphasize the strategic commitment to diversity, equity, and inclusion, a seventh SF/EP pair was added to the VSE in 2018 (see Tables 2 and 3).
- 10. A chief strategy officer who guides implementation is critical to success.
- -Someone has to ensure that the organization follows through. APL elevated the role of chief strategy officer to an assistant director who has control and oversight of critical investment resources.

## CONCLUSION

APL's integrated systems approach to strategy has resulted in a vision and strategy framework that is built to last and has proven itself in execution, even during a turbulent decade marked by changing national security priorities, economic uncertainty, and transformative technological advances in areas such as artificial intelligence, hypersonics, and cyber. Finally, as with other successful APL innovations, we have sought to widely share this systems approach to strategy in the conviction that it can be useful to any organization committed to becoming strategy driven as a basis for thriving in an uncertain world. 1

## REFERENCES

- $^{ 1}$R. R. Luman, T. J. Galpin, and J. A. Krill, "Becoming a strategydriven technology organization-A case study," IEEE Eng. Manage. Rev. , vol. 51., no. 2, pp. 104-119, 2023, https://doi.org/10.1109/ EMR.2023.3246431.
- $^{ 2}$"Vannevar Bush." Wikipedia. https://en.wikipedia.org/wiki/Vannevar \_Bush (accessed Oct. 4, 2022).
- $^{ 3}$"Applied Physics Laboratory." Wikipedia. https://en.wikipedia.org/ wiki/Applied\_Physics\_Laboratory (accessed Oct. 4, 2022).
- $^{ 4}$"History." Johns Hopkins Applied Physics Laboratory. www.jhuapl. edu/About/History (accessed Oct. 4, 2022).
- $^{ 5}$R. Banham, "Beyond New Horizons," in Defining Innovations: A History of The Johns Hopkins University Applied Physics Laboratory , Laurel, MD: APL, p. 130.
- $^{ 6}$R. B. Baldwin, The Deadly Fuze: The Secret Weapon of World War II . San Rafael, CA: Presidio Press, 1980.
- $^{ 7}$H. E. Worth, "The visionary directors of APL: Creating and nurturing a national resource," Johns Hopkins APL Tech. Dig. , vol. 34, no. 2, pp. 333-348, 2018. https://secwww.jhuapl.edu/techdigest/Content/ techdigest/pdf/V34-N02/34-02-Worth-Directors.pdf.
- $^{ 8}$"How to create a vision, strategy & execution plan," Cisco Inclusion and Diversity Resource Center, 2007, unpublished PowerPoint presentation.
- $^{ 9}$S. Watts, "The VSEM (vision, strategy, execution, and metrics) framework explained," The Business of IT Blog , bmc, Jun. 16, 2020. https://www.bmc.com/blogs/vsem-vision-strategy-execution-metrics/.
- $^{10}$M. Mankins and R. Steele, "Stop making plans; start making decisions," Harvard Bus. Rev. , Jan. 2006. https://hbr.org/2006/01/stopmaking-plans-start-making-decisions.
- $^{11}$"Budget sequestration." Wikipedia. https://en.wikipedia.org/wiki/ Budget\_sequestration (accessed Oct. 4, 2022).
- $^{12}$"2013 United States federal government shutdown." Wikipedia. https:// en.wikipedia.org/wiki/2013\_United\_States\_federal\_government \_shutdown (accessed Oct. 4, 2022).
- $^{13}$J. C. Collins and J. I. Porras, Built to Last: Successful Habits of Visionary Companies , New York, NY: HarperBusiness, 1994.
- $^{14}$J. C. Collins and J. I. Porras, "Building your company's vision," Harvard Bus. Rev. , Sep.-Oct. 1996.
- $^{15}$M. A. Garrison Darrin and J. A. Krill, Eds., Infusing Innovation into Organizations: A Systems Engineering Approach , Boca Raton, FL: CRC Press, 2016.
- $^{16}$APL staff, "Destination: Titan," press release, Laurel, MD: APL, Jun. 27, 2019, https://www.jhuapl.edu/news/news-releases/190627bdestination-titan.
- $^{17}$P. Voosen, "NASA will fly a billion-dollar quadcopter to Titan, Saturn's methane-rich moon," Science Insider , Jun. 27, 2019, https://www. science.org/content/article/nasa-will-fly-billion-dollar-quadcoptertitan-saturn-s-methane-rich-moon.
- $^{18}$"Health Surveillance." Johns Hopkins Applied Physics Laboratory. https://www.jhuapl.edu/work/projects/health-surveillance (accessed May 5, 2023).
- $^{19}$"The Best Inventions of 2020." Time . https://time.com/collection/ best-inventions-2020/ (accessed Oct. 4, 2022).

$^{20}$R. D. Semmel, "Defining innovations," Johns Hopkins APL Tech. Dig. , vol. 34, no. 2, pp. 107-133, 2018, https://secwww.jhuapl.edu/ techdigest/Content/techdigest/pdf/V34-N02/34-02-Semmel.pdf.

$^{21}$APL staff, "Bullseye! NASA's DART Mission Impacts Asteroid Target in World First," press release, Laurel, MD: APL, Sep. 26, 2022, https:// www.jhuapl.edu/news/news-releases/220926-nasa-dart-missionstrikes-asteroid-target.

$^{22}$"Best workplaces for innovators 2019." Fast Company. https://www. fastcompany.com/best-workplaces-for-innovators/2019 (accessed Oct. 4, 2022).

$^{23}$"Best workplaces for innovators 2020." Fast Company. https://www. fastcompany.com/90527870/best-workplaces-for-innovators-2020 (accessed Oct. 4, 2022).

$^{24}$M. Ambasna-Jones and Insider Pro Staff, "Best places to work in IT in 2021," Insider Pro , Jul. 12, 2021, https://www.idginsiderpro.com/ article/3623739/best-places-to-work-in-it-2021.html.

$^{25}$B. Stackpole and Best Places to Work in IT Team, "Best Places to Work in IT 2023," Computerworld , Dec. 13, 2022, https://www.computerworld. com/article/3681081/best-places-to-work-in-it-2023.html.

$^{26}$"von Braun Award for Excellence in Space Program Management." AIAA. https://www.aiaa.org/get-involved/honors-awards/awards/award/ award-von-braun-award-for-excellence-in-space-program-management (accessed Oct. 4, 2022).

<!-- image -->

Ronald R. Luman, Chief of Staff (retired), Johns Hopkins University Applied Physics Laboratory, Laurel, MD

Ronald R. Luman was APL's chief of staff from 2010 until 2022. He received a BA in mathematics from Middlebury College, an MS in applied mathematics from Michigan State University, an MS in technical

management from the Johns Hopkins University, and a DSc in systems engineering from George Washington University. He stepped down as APL's chief of staff in 2022 and is now an APL senior adviser. As chief of staff, he managed APL's strategic decision agenda and coordinated its collaborative executive management processes. He also chaired the systems engineering master's program at the Johns Hopkins Whiting School of Engineering from 2008 to 2020; in 2013, this program became the first such master's program to achieve ABET certification, and it remains one of the largest systems engineering master's programs in the nation. Dr. Luman was the vice chair of the National Academies' Naval Studies Board (NSB) and served on NSB committees related to climate change, missile defense, unmanned undersea vehicles, and asymmetric warfare. He is an inductee to the GWU Engineering Hall of Fame, a fellow of the International Council on Systems Engineering, a member of the National Advisory Council for the GWU School of Engineering and Applied Science, and a recipient of the Barchi Prize from the Military Operations Research Society. His email address is ronald.luman@jhuapl.edu.

<!-- image -->

Timothy J. Galpin, Assistant Director for Programs, Johns Hopkins University Applied Physics Laboratory, Laurel, MD

Timothy J. Galpin is APL's assistant director for programs. He earned a BS in history from the United States Naval Academy, an MA in political economy from Oxford University as a Rhodes Scholar, and a

PhD in public policy from the University of Maryland, Baltimore County. He holds certificates in management from the

$^{27}$"A group from Johns Hopkins University earns 2021's Innovative Team of the Year." Fast Company. https://www.fastcompany. com/90659001/best-workplaces-innovators-2021-innovation-team-ofthe-year (accessed Oct. 4, 2022).

$^{28}$"The 10 most innovative space companies of 2022." Fast Company. https://www.fastcompany.com/90724476/most-innovative-companiesspace-2022 (accessed Oct. 4, 2022).

$^{29}$"Double Asteroid Redirection Test." Johns Hopkins APL. https://dart. jhuapl.edu/index.php (accessed Oct. 4, 2022).

$^{30}$"Best places to work 2022." Glassdoor. https://www.glassdoor.com/ Award/Best-Places-to-Work-2022-LST\_KQ0,24.htm (accessed Oct. 4, 2022).

$^{31}$"Best places to work 2023." Glassdoor. https://www.glassdoor.com/ Award/Best-Places-to-Work-LST\_KQ0,19.htm (accessed Feb. 14, 2023).

$^{32}$APL staff, "Johns Hopkins APL researchers earn 2022 R&D 100 Awards," press release, Laurel, MD: APL, Aug. 26, 2022, https://www. jhuapl.edu/news/news-releases/220826-johns-hopkins-apl-researchers-earn-2022-randd100-awards.

$^{33}$APL staff, "Johns Hopkins APL's ultracompact, efficient cooling device earns 2023 R&D 100 Award," press release, Laurel, MD: APL, Aug. 23, 2023, https://www.jhuapl.edu/news/news-releases/230823aapl-wins-2023-rd100-award.

University of Virginia and in national security from the Harvard Kennedy School and MIT Seminar XXI. He oversees all government-sponsored technical work and serves as the Lab's chief strategy officer. In that role, he chairs the investment strategy team that aligns resources to strategy at the enterprise level. He has written on business and national security issues. Dr. Galpin chairs the engineering management master's program for the Johns Hopkins Whiting School of Engineering and serves on nonprofit boards, including the Maryland Science Center board, as well as federal advisory panels in acquisition and technology. His email address is timothy.galpin@ jhuapl.edu.

<!-- image -->

Jerry A. Krill, Assistant Director for Science and Technology and Chief Technology Officer, Johns Hopkins University Applied Physics Laboratory, Laurel, MD

Jerry A. Krill is APL's assistant director for science and technology and chief technology officer. He earned a BS and an MS from Michigan State University

and a PhD from the University of Maryland College Park, all in electrical engineering. He leads innovation initiatives toward APL's Centennial Vision to "create defining innovations that ensure our nation's preeminence in the 21st century." He holds 22 patents and has authored over 100 papers and documents, including co-editing the book Infusing Innovation into Organizations . As a member of the National Academies Naval Studies Board from 2006 to 2012, he co-led the study Responding to Capability Surprise: A Strategy for U.S. Naval Forces . More recently, he has served on the National Academies' ballistics and extramural research review panels for the Army Research Laboratory. Dr. Krill serves on the Johns Hopkins Whiting School of Engineering's advisory board. He received the American Society of Naval Engineers "Jimmie" Hamilton Award, was named Maryland Daily Record Innovator of the Year, and was inducted into the Clark School Innovation Hall of Fame at the University of Maryland, College Park. His email address is jerry.krill@jhuapl.edu.

H. K. Charles Jr.

## "APL in the Twenty-First Century":

A Retrospective on the 1983 Report to the Director

YEARS

Harry K. Charles Jr.

## ABSTRACT

In 1983, at the behest of the Johns Hopkins University Applied Physics Laboratory (APL) director, an accomplished group called the APL senior fellows produced a report on the projected state of the Laboratory at the beginning of the 21st century. This article presents a retrospective on that report, which Identified key technologies, relationships, and environmental factors that would be important to APL at the dawn of the 21st century and beyond. In this article, these key items are identified, discussed, and assessed for their relevance (or not) to the current state of the Laboratory.

## INTRODUCTION

In the early 1980s, Laboratory director Carl O. Bostrom$^{1}$ commissioned the APL senior fellows (H. C. Anderson, W. H. Avery, J. T. Massey, C. F. Meyer, R. C. Morton, and A. M. Stone; see Box 1 for biographical details) to project the state of the Laboratory in the twenty-first century. In their 1983 report,$^{2}$ the cover of which is shown in Figure 1, the senior fellows addressed several key areas:

- 1. The 21st-century environment
- 2. Long-range APL goals
- 3. APL's relationships with the military
- 4. Funding (research and development)
- 5. APL's relationships with other divisions of Johns Hopkins University (JHU)
- 6. Educational responsibilities and opportunities
- 7. Technology and new program opportunities

Figure 1. Image of the cover of the 1983 "APL in the Twenty-First Century" special report to the director from the senior fellows.

<!-- image -->

In addition, they devoted a significant number of pages in the document to describing (and presumably significant time to devising) their methods and models$^{3}$ for predicting long-term trends for things that were important in the early 1980s and would help shape the future after the turn of the 21st century, such as world population and gross national product (GNP). Table 1 illustrates some of their predictions for the year 2000, as well as actual statistical data for the years 2000 and 2020. As the table shows, their projections typically differed from the actual data. More will be said about this later in this article. In addition to the parameters shown in Table 1, the senior fellows speculated on raw material and food availability as well as war, space exploration,

Table 1. Comparison of the 1983 senior fellows projections for the year 2000 with actual data collected in years 2000 and 2020

| Parameter            | Senior Fellow  2000 Prediction   | 2000  Actual   | 2020  Actual   |
|----------------------|----------------------------------|----------------|----------------|
| Population a         |                                  |                |                |
| World                | 4.73 × 10 9                      | 6.15 × 10 9    | 7.84 × 10 9    |
| United States        | 4.92 × 10 6                      | 2.82 × 10 6    | 3.35 × 10 6    |
| GNP (US dollars) b   |                                  |                |                |
| World                | 10.76 × 10 12                    | 33.8 × 10 12   | 86.4 × 10 12   |
| United States        | 1.39 × 10 12                     | 10.1 × 10 12   | 21.43 × 10 12  |
| Energy Use (Btu) c   |                                  |                |                |
| World                | 5.71 × 10 18                     | 3.79 × 10 17   | 6.25 × 10 17   |
| United States        | 1.82 × 10 18                     | 9.81 × 10 15   | 1.22 × 10 16   |
| Pollution (ppm) d    |                                  |                |                |
| Atmospheric CO$\_{2}$ | 3.9 e                            | 369.7          | 414.2          |

$^{a }$Date source for 2000 and 2020: United Nations Department of Economic and Social Affairs World Population Prospects (2022).

$^{c }$Data source for 2000 and 2020: Energy Institute Statistical Review of World Energy (2022). $^{d }$Data source for 2000 and 2020: NOAA Climate.gov.

and deterrent weapons; again, more discussion of these projections will come later. They again detailed their methods of speculation, allocating a significant number of pages to discussing the theories of speculation that were prevalent at the time and why they would or would not work. The salient features related to APL's future, which can be distilled from these predictive models and forecasting (speculation) methods, are described in the sections that follow.

The senior fellows assumed that APL would maintain its 1983 staffing level (2,800 APL staff members plus a few hundred resident subcontract employees). They had no idea of the growth that APL would experience during the first 20+ years of the new century. This assumption limited their thinking about the number and size of programs that APL could or should undertake.

## KEY AREAS ADDRESSED IN THE REPORT

## 1. The 21st-Century Environment

As mentioned, Table 1 compares some of the fellows' numerical projections for the year 2000 with the actual data in the year 2000. Except for the atmospheric CO$\_{2}$ projection, which seems anomalous, they overestimated the United States' population and underestimated the world's by factors ranging from about 1.5 to 2. The world's GNP and that of the United States were underestimated by factors of about 3 to 7. Clearly, the information age's dramatic impact on world economies was not fully understood or even considered in the 1983 time frame. Energy use was overestimated in all cases, but especially in the United States. In 1983, few people could foresee

the energy conservation and energy technology developments that would occur over the next 20 years. Although the 1983 report recognized the need to control both automobile and factory emissions and to advance the use of alternative energy sources such as solar, geothermal, and nuclear, it did not discuss the impact of high atmospheric CO$\_{2}$ levels and climate change. There was also no mention of technologies such as light-emitting diodes and hybrid and all-electric vehicles. While these technologies were known, their impact on energy and society was certainly unknown at the time of the report.

The fellows projected that raw materials would be adequate for 20-30 years, except maybe mercury and tin, but they felt that mining of ocean nodules may alleviate any shortages. They did not envision the rapid increase in the use of batteries, for example in portable electronics and hybrid and all-electric vehicles. Battery technology has put strains on supplies of lithium, graphite, and cobalt. Rare earth elements are being used in many applications, and today's supply is limited.

The 1983 team speculated that food supplies would be adequate far beyond the year 2000 except perhaps for a few small countries. This possibly stems from the fact that they underestimated the year 2000 world population by about 1.4 billion people, and climate change's environmental effects on food production were, of course, unknown at the time. It is estimated that early in the 21st century, almost 1 billion people have inadequate food supplies owing to a variety of factors such as poverty, disease, natural disasters (earthquakes, floods, and storms), climate change, and conflict. According to some reports, upward of 75% of the world's malnourished people live in conflict zones. 45

## BOX 1. BRIEF BIOGRAPHIES OF SENIOR FELLOWS

Senior Fellow of the Applied Physics Laboratory was a professional appointment first announced by Dr. Steven Muller, president of the university in 1981. The title recognized those staff members who had distinguished themselves by making truly exceptional contributions to the accomplishments, reputation, and strength of the Laboratory throughout their careers.

<!-- image -->

<!-- image -->

1912-2004

<!-- image -->

<!-- image -->

<!-- image -->

<!-- image -->

Harry C. Anderson joined APL in 1949, working in the Bumblebee group as assistant supervisor of the Launching and Propulsion Group. Later he was supervisor of both the Personnel Group and the Solid and Liquid Propellant Information Agencies and chair of the Committee on Education. In 1952, he was named director of personnel and education and held that position until 1982, when he was appointed an APL senior fellow. From 1959 to 1969, he concurrently served as head of the JANNAF Solid and Liquid Propellant Information Agencies, later renamed the Chemical Propulsion Information Agency, which was part of APL. He retired from the Laboratory in 1983.

William H. Avery was the former assistant director for exploratory development and supervisor of APL's Aeronautics Division. He relinquished those posts in 1977 and was named director of ocean energy programs. A pioneer in rocket and ramjet research, he first joined the APL staff in 1947 as supervisor of the group developing launch rockets for guided missiles after having previously worked with Ralph Gibson (APL director from 1948 to 1969) and Alexander Kossiakoff (APL director from 1969 to 1980) at the National Defense Research Committee (NDRC). He retired from the Laboratory in 1998. For further details on Dr. Avery's career and life, see A. Kossiakoff. 4

Joseph T. Massey came to APL in 1945. He was assistant supervisor of the Guidance and Control Group and supervisor of the Guidance Intelligence Group from 1946 to 1949, and then he joined the Research Center. In 1965, he participated in establishing a collaborative biomedical program between APL and the Johns Hopkins School of Medicine, and from 1973 until his retirement from APL in 1983, he was the director of biomedical programs. After his retirement from APL, he was engaged in research on primate motor physiology at the Johns Hopkins School of Medicine, where he had faculty appointments in biomedical engineering and neuroscience.

Charles F. Meyer joined APL in 1944. While working at APL, he was also a part-time assistant professor in the Institute for Cooperative Research at Johns Hopkins, teaching atomic physics from 1946 to 1948. In 1947, he helped form the Warhead Analysis Group and served on various government groups interested in that subject. From 1950 to 1981, he headed what was to become the Central Laboratory Assessment Division, which analyzed naval warfare and continental air defense in collaboration with various outside agencies. At the time of the report, he was senior fellow on special assignment with the Director's Office. He retired from the Laboratory in 1983.

Robert C. Morton joined the APL staff in 1948 as a Terrier guided missile engineer. He later headed the Strategic Systems Department from 1963 until July 1981, making major contributions in testing and analysis of the Navy's Fleet Ballistic Missile Submarine system. Prior to that, he supervised the Polaris Analysis and Evaluation Group and had formerly served as systems group supervisor of the Terrier/ Tartar programs. At the time of the report, he was on special assignment as a senior fellow with the Director's Office. He was still a senior fellow at the time of his death. For more details of his life and career, see Potocki et al. 5

Albert M. Stone came to APL in 1949 and held several important Laboratory positions, including technical assistant to the director from 1949 to 1974, supervisor of the Plasma Physics Group from 1960 to 1973, and head of the Technical Information Division from 1961 to 1979. He was a member of the former Program Review Board and the first editor in chief of the APL Technical Digest , the progenitor of this journal, and served in that role from 1961 until 1963. At the time of the report, he held the post of director of Advanced Research Programs, a position he had also held since 1974. He retired from the Laboratory in 1987.

In their general reflections on the 21st century, the senior fellows commented on war, deterrence, and space. They did not believe there would be a major war between the United States and the Soviet Union because of the fear that the world would be destroyed by nuclear weapons. They did not foresee the breakup of the Soviet Union and its worldwide impact on strategic forces and deterrence. Similarly, they did recognize that smaller wars between other nations would occur and that there may be need for US intervention. The events of September 11, 2001, and the subsequent war on terror were not on their radar.

When they addressed deterrence, they thought of strategic deterrence between the United States and the Soviet Union mainly involving the submarine forces. As mentioned, the eventual breakup of the Soviet Union was unknown, and China's rise as a world power requiring strategic deterrence was not mentioned.

When considering space, the fellows speculated that space exploration would continue, and they specifically felt that it was possible that humans would have made expeditions to Mars. While they did note that satellite communications would increase and they were aware of GPS, the senior fellows did not foresee the almost ubiquitous use of GPS smartphones by the worlds' population. However, they were extremely familiar with the Transit system (Figure 2) for global navigation of ships and submarines, which was invented at APL and later recognized as one of APL's defining innovations.$^{6}$ No mention was made of the low-cost uncrewed planetary exploration missions that have become another defining innovation of the Laboratory.

Figure 2. APL designed, built, tested, and operated several satellites for the Transit navigation system. Transit greatly improved the ability of US submarines around the world to accurately determine their positions. In 1967, APL released use of the system to private industry, and it became the reference system for many critical measurements, continuing to serve into the 2000s.

<!-- image -->

## 2. Long-Range APL Goals

The senior fellows reiterated the long-standing mission statement of the Laboratory: "to make a major contribution to the solution of important problems of National security in which the solution depends strongly on the application of new technology or new uses of existing technology." They stated that national security was to be understood in a broad sense to include the maintenance of a strong US base in advanced technology that will allow the nation to continue its industrial preeminence in the world. The report devoted no real attention to globalization and the specter of major outsourcing that continues to impact our industrial base.

Underlying this mission statement is the assumption that APL will have special competence in the projects it undertakes and will continue to recruit staff members with outstanding talents in science and engineering. In addition to acknowledging the need for scientists and engineers, the senior fellows also recognized the need for staff members with social science backgrounds (economists, political scientists, and policy specialists) to make effective contributions to the solution of important national problems in the non-defense, non-aerospace sectors of the government, while also solving bureaucratic, funding, and political entanglements standing in the way of the technical work in the defense arena.

The senior fellows went on to say that APL is a unique national resource. The key word is unique , indicating that no other type of institution produces an environment in which independence of thought, depth of scientific understanding, freedom of imagination, and flexibility of approach can flourish to the same degree. The senior fellows felt so strongly about APL's uniqueness (as defined above) that they made preserving this characteristic their first and foremost goal for the 21st century. Fortunately for the nation, JHU, and the Laboratory's sponsors, APL continues to maintain world-class resources and facilities in a number of areas.

Aside from the first and foremost goal mentioned above, the senior fellows declined to set goals looking out more than 20 years, recognizing that APL would accomplish such goals with an almost entirely new staff in a world driven by new, unforeseeable technologies against a backdrop of not even vaguely defined national (and international) goals. They did, however, set down some tangible attributes and requirements of a unique resource, and these are reproduced verbatim in Box 2. It is easily recognized that these attributes apply to APL today, as APL is truly world-class in many of its activities.

In fact, the thinking of the senior fellows on maintaining the existence of the Laboratory in the future closely aligns with the strategic systems approach articulated by today's leaders (see the article by Luman, Galpin, and Krill, in this issue):

- 1. A consensus among key policymakers on the basic, long-range mission of the Laboratory
- 2. A clear statement of goals that can be expected to strengthen the Laboratory's ability to maintain the role defined by its mission
- 3. Definition of criteria that can be used to judge whether new or ongoing projects or programs are contributing significantly, holding the line, or either wasting resources or preventing work on more significant topics

The senior fellows did set some intermediate goals (nominally 15 years out) that would involve

- 1. the exploration of research and development activities leading to funded APL programs in
- · ocean science and engineering;
- · biomedical engineering (molecular engineering);
- · computer system applications to scientific and engineering research and development (such as artificial intelligence, computer graphics, and computer-aided design);
- · space science;
- · high-energy beam transmission; and
- · targeted solid-state research;
- 2. fleet systems integrated defense; and
- 3. submarine security science and tactics.

## BOX 2. ATTRIBUTES AND REQUIREMENTS OF A UNIQUE RESOURCE

- · To develop in-house scientific and technological expertise in areas even remotely thought to have application to solutions of major national problems.
- · To use effectively, that is, flexibly and with imagination, these resources as needed to evaluate technically, economically and socially contemporary national needs.
- · To foster new endeavors for which evaluation indicates need and for which APL has particular capabilities to bring to the endeavor.
- · To assess clearly and without bias the status of any program at any time and submit recommendations for its realistic future course.
- · To oppose vehemently any endeavor to reduce the Laboratory's hands-on capability in its mission (i.e. laboratory experimentation to the point of a prototype if necessary).
- · To foster and enhance closer ties to other divisions of The Johns Hopkins University through collaborative endeavors and other intellectual involvements.
- · To maximize advantages of the University-APL relationship rather than to emphasize differences.

Except for some of the research topics, these intermediate goals reflected extensions of APL business at that time, and they ultimately came to fruition.

## 3. APL's Relationships with the Military

In this section, the senior fellows mainly focused on the Navy and the size of its fleet and the weapon systems that would exist in the year 2000. The backdrop was the Cold War conflict with the Soviet Union. No one on the team foresaw the fall of the Soviet Union, but they made several subtle mentions of a "peace dividend" and what impact it might have on the nature of the Laboratory's business. This impact was characterized as shifting a portion of APL program interest from military to more civilian activities such as biomedicine, transportation, and space exploration. The senior fellows took the projections in the Navy's year 2000 report, prepared in 1978,$^{7}$ as a basis for discussion. This report predicted a 500-ship Navy in the year 2000 and talked about the strengths of missiles and bombers on both the US and Soviet sides. The senior fellows offered insights about the military environment (both hardware and "software") to be expected at the turn of the century. They foresaw the outer air battle being fought at distances greater than 1,000 nautical miles requiring more advanced development in missiles as well as improved surveillance and targeting capabilities. They forewarned of advanced anti-ship missiles and the greater need to protect the fleet. They were aware of the work APL was doing on multi-target tracking and fleet sensor integration that led to the Cooperative Engagement Capability (CEC), an APL defining innovation, in the 1990s (Figure 3). They mentioned the ballistic missile threat but did not envision APL's defining innovation of Ballistic Missile

Figure 3. CEC being operated aboard USS Cape St. George . APL conceived and provided technical leadership with collaborating partners in industry and warfare centers on behalf of the sponsor to develop CEC. CEC networks multiple radars to provide fire control-quality composite tracking of aircraft and missiles.

<!-- image -->

<!-- image -->

Figure 4. The senior fellows predicted space stations and greater human presence in space. Left, the International Space Station photographed by an STS-134 crew member on the space shuttle Endeavour after the station and shuttle began their post-undocking relative separation on May 29, 2011. Right, a timed exposure of the first Space Shuttle mission, STS-1, taken at Launch Pad A, Complex 39, on March 5, 1981. (NASA photos.)

<!-- image -->

Defense from the sea.$^{8}$ They felt there would be extensive use of stealth technology in aircraft and even suggested that vertical or short takeoff and landing aircraft would become the mainstay of the fleet. They made no mention of uncrewed autonomous vehicles (UAVs) for air, surface, and undersea applications, and the word drone never appeared.

The senior fellows did mention that space provides many of the significant tools of war and alluded to the possibility that it could become the battleground of the future. This is a real concern in 2023. They did not address the threat of our planet's destruction or devastation by an asteroid collision and, thus, never discussed planetary defense, which APL has since pioneered with the Double Asteroid Redirection Test (DART) mission.$^{9}$ They did predict things like space stations and greater human presence in space (Figure 4).

Submarines, both ballistic missile and attack, would provide a major strategic deterrent as the senior fellows predicted. They expressed concern about nonconventional weapons, such as laser and charged-particle beams, as well as the use of chemical and biological weapons. They also believed, for the most part, that the hardware trends of the early 1980s would continue through the year 2000. New technologies (such as advances in integrated circuits) would have a significant ultimate impact but would not change the general direction until after the year 2000, since the then-current hardware time constant was greater than 15 years. While such time constants may still be experienced for major hardware acquisitions, modularity of design in later systems is beginning to allow much more timely updates of functional capabilities.

The senior fellows introduced the term software as a means to discuss the political side of the Cold War and the general trend to support human rights and

settle conflicts by negotiations. This "software" part of the environment could change the hardware picture greatly with ongoing arms control negotiations. The senior fellows feared that, if successful, these negotiations could reduce our deterrent arms significantly and hence affect our total defense posture. Such reduction in arms would reduce the total defense budget, both strategic and tactical. In turn, there would be a reduced Navy budget, which would directly affect APL funding and the percentage of funds for defense. Such a "software" event downturn happened to APL during the early to mid-1990s when defense budgets were reduced as a result of the end of the Cold War with the Soviet Union.

## 4. Funding (Research and Development)

Just as it is today, funding was critical to the future of the Laboratory in 1983. The senior fellows recognized that only a large source of funding could support a laboratory of APL's size; thus, they believed that the bulk of APL's funding in the 21st century would still need to come from the federal government-notably, the Department of Defense and its agencies. Historically, APL was (and still is) dependent on annual funding of its various programs. The senior fellows looked at this fact in two ways. On one hand, they considered this predominantly annual funding of programs an advantage in that it ensured abandonment of weakly funded programs; but on the other hand they believed it was also a disadvantage because it emphasized short-term projects, prevented rejection of routine sponsor tasks (best done by other organizations), and discouraged work on high-risk and potentially high-payoff ideas that were vital to APL's future ability to contribute to national goals. Some of the same issues and concerns exist today, but APL has made significant strides in investing in facilities and technology development that are necessary for its future. 10

The senior fellows believed that it was imperative for the Laboratory to develop new sources of discretionary funding, apart from the discretionary funds that can be gleaned from program tasks (Independent Research and Development, or IRAD; and bid and proposal, or B&P). They thought that while IRAD and B&P funding was insufficient, it was essential for APL's survival. In addition to these sources of discretionary funding, they also thought there was a need for another source of discretionary funding, what they proposed as an "endowment" fund. They envisioned the endowment fund as a source of funding "to incubate new technologies and programs, and to provide for a flow of fresh talent through expanded pre-doctoral and post-doctoral fellows programs, as well as staff re-education [continuing education] programs."

They discussed many ways to finance the endowment fund: using patent and licensing revenue, launching an endowment-fund campaign, using the income from the Stabilization and Contingency fund, tapping the net revenue from graduate education program, and raising and restructuring the fee from the omnibus Navy contract. At the time, they concluded that raising the fee was the only viable solution, and they expended some effort on justifying this recommendation.

Fortunately, today APL's IRAD funding is much higher, at 3% of revenue. Also, as a university-affiliated research center (UARC) (APL was established as a UARC in the 1990s), the Laboratory can compete for science and technology (S&T) funds, which now amount to hundreds of millions of dollars. So, it is clear that raising the fee was not the answer.

## 5. APL's Relationships with Other Divisions of JHU

The senior fellows predicted no radical changes in APL's 21st-century relationship with the rest of the university. APL became a Limited Liability Corporation in 2009. This change did not deter APL from doing what the fellows predicted: strengthening collaborative relationships with the medical institutions and the Homewood faculties both in engineering and the physical sciences.

The senior fellows did envision expanded opportunities for graduate students to work at APL with the Laboratory's extensive advanced facilities and research and engineering experts. They also envisioned a greater flux of postdoctoral assignments. Both these ideas now have APL institutional roots with the joint research assistantship agreement with the Whiting School of Engineering and the Laboratory pool of central IRAD funding to support resident postdoctoral research studies.

Two additional ideas surfaced in the fellows' report: (1) a joint "Division of Research and Engineering Services," which would contract with industry to solve its problems; and (2) a "JHU Associates Program" in which industrial organizations would pay an annual subscription for special briefings and/or training in a specific area.

These programs were not pursued, probably because of potential conflicts of interest and concerns about working for industry.

## 6. Educational Responsibilities and Opportunities

The educational ties with the university were of paramount importance in 1983, just as they are today. Recognizing the ever-growing complexity of science and technology, the senior fellows foresaw the need for a "considerably more structured" educational program at APL. They discussed two aspects of this program: (1) the external aspect relating to the Laboratory's educational function as part of the university as a whole; and (2) the internal requirement to educate and support the APL staff.

The senior fellows foresaw an advanced engineering degree as part of the external activities-"a step beyond the Master's degree" as they called it. It would have the basic quality of a doctoral degree, but without the research dissertation requirement. Instead, there would be a practical project requirement. In 2018, some 35 years after the senior fellows' recommendation, APL and the Whiting School launched the Doctor of Engineering program, a portfolio-oriented degree program for working professionals.$^{11}$ The senior fellows also felt that APL should be the focus for the instruction and should provide the facilities and supervision for the portfolio. As of this writing in 2023, this exact scenario has not come to fruition, although 19 APL staff members have received their doctor of engineering degree by leveraging aspects of their daily work assignments for their portfolio. Another 21 APL staff members are enrolled in the program as of 2023.

When considering internal activities, the senior fellows recognized the need for lifelong learning and recommended increased emphasis on staff "re-training" considering rapidly changing technology. A specific management function would be to continually identify those technical disciplines vital to APL's future and provide access to a myriad of options to achieve the necessary re-education or re-training. These options would include:

- 1. an expanded education center program
- 2. sabbatical leave and fellowship programs
- 3. greater use of student interns and postdoctoral fellows
- 4. in-house experts to train other APL staff members

The Engineering for Professionals (EP) program now offers 23 degrees in engineering and scientific disciplines, compared with only 6 in 1982-1983. Despite the senior fellows calling for it in the 1980s, the in-house training of staff by APL's own subject-matter experts did not gain traction until the first decade of the 21st century. Given

the name Strategic Education, the annual program offers about 50 courses per year, as of 2023, in new and technology-relevant fields. With annual enrollments above 800, this program has made an impact on several thousand APL staff members.$^{11}$ APL also has made strong commitments to a sabbatical fellows and professors program with JHU, an intern hiring program, a central postdoc support program, and a fellowship program for Hopkins PhD students.

The senior fellows went on to make strong statements about the need for lifelong learning and the development of programs allowing staff members to continue to learn and grow throughout their careers. They were particularly concerned with the professional development of engineers (and scientists) and the collective national technological capability, particularly in areas of "high technology." The fellows recommended collaboration between engineering schools and industry to develop "a new pattern of engineering education" to meet the needs of a world characterized by rapid technology change and engineering systems of rapidly growing complexity. This new educational approach would be distinguished from those of the past by three attributes: (1) engineers' uninterrupted commitment to formal (and informal) education; (2) employers' wholehearted support of the notion that study and teaching are necessary and valuable components of productive work; and (3) university faculties' increased attention to the educational needs of working engineers of all ages.

The senior fellows believed that APL and the university were in a strong position to support these lifelong learning needs of the working professional. Although perhaps not as rapidly as the fellows would have liked, JHU and APL have responded to these recommendations with the continuing growth of the EP program, the Doctor of Engineering program, the Lifelong Learning 12 program; and the APL Strategic Education program. APL also encourages its staff to attend short courses and technical conferences as well as to become active members of professional societies.

Although the senior fellows mentioned distance learning through remote TV-microwave links, they did not anticipate the information age and the impact that the internet would have on all aspects of education. They had no notion that 99% of all EP courses would be online and that face-to-face courses would be taught via video communications platforms. They were still of the mindset that brick and mortar was the prevailing model and that the market for EP was regional. This is realistic for the time frame since we are talking about the era when the personal computer had just been introduced.

## 7. Technology and New Program Opportunities

In the chapter devoted to technological and program opportunities, the senior fellows identified several new technologies of the time and justified why they believed

they would be important (or not) to APL in the future. The technologies identified included

- 1. short-wavelength lasers (directed-energy weapons, nonexplosive triggering of a nuclear weapon, and perhaps containment and triggering of a fusion reaction);
- 2. large space structures such as space stations and laboratories (scientific research, weapons platforms, or even a "spacecraft carrier" concept);
- 3. high-power microwave generators (communications and radar);
- 4. space nuclear power (not to be practiced at APL; APL uses radioisotope thermoelectric generators as power sources for deep-space exploration missions);
- 5. particle beams (directed-energy weapons in all theaters of war including space);
- 6. electromagnetic pulse, from weapons to protection; optoelectronics, such as fiber optics surveillance, tracking, etc.;
- 7. artificial intelligence (nonmilitary versus military, robotics; they did not go as far as autonomous vehicles, etc.);
- 8. thermonuclear fusion (power, materials synthesis; they thought this would be too expensive for APL and noted the lack of critical staff);
- 9. near-theoretical-strength materials (they noted the lack of critical mass despite some early successes);
- 10. bioengineering (they mentioned the university-wide effort looking for an APL role); and
- 11. crewed lunar and planetary expeditions (they saw a role for APL, but because of costs and technology limitations, such activities have been delayed and will perhaps occur in the third and fourth decades of the 21st century)

The senior fellows ended their extensive report with a list of desirable directions for the Laboratory to explore or be engaged in 30 years hence. Their choices were tempered by the following assumptions:

- 1. There would be no radical changes in APL's relationship to the rest of the university.
- 2. The Laboratory would undergo no substantial growth in terms of its staff or facilities, although the fellows did expect a constant re-education of the staff and a steady modernization of the facilities.
- 3. The United States Navy would be the principal Laboratory sponsor and would support 65-70% of the work.

Based on these assumptions and their collective experience, the senior fellows projected the following new areas to be a significant focal point of APL activities in the 21st century.

- 1. Information networks, including optical fibers
- 2. Optoelectronics development (in light of electromagnetic pulse)
- 3. Military space systems
- 4. Particle and laser-beam weapons systems
- 5. Military bioengineering
- 6. Artificial intelligence
- 7. Microbiology and genetic engineering
- 8. Oceanography from space platforms

## DISCUSSION: WERE THE SENIOR FELLOWS RIGHT OR WRONG?

Just as with any set of predictions made by intelligent people based on the facts available to them at the time, the results of the senior fellows' projections are mixed. Their education predictions were truly on target, aligning with the growth of EP program and the advent of the Doctor of Engineering, Lifelong Learning, and Strategic Education programs, although the realization of these items took much longer than expected. However, they did not account for the information age and the invention and use of the internet, which has revolutionized education. They still embraced regional education manifested by brick-and-mortar classrooms and did not envision the 99% online education practiced by EP, but they did feel that the clever use of the video media was bound to have a strong impact on the methodology of updating professional competencies. The worldwide shift to online education at colleges and universities was accelerated by COVID-19.

In their projections on future APL technical directions, the fellows hit many of the key components of the Laboratory's current technology base, such as artificial intelligence, military space, information technology, and aspects of biotechnology and engineering. They envisioned longer-range missiles and the use of hypersonic vehicles, both areas of active work in the Laboratory's Air and Missile Defense and Force Projection Sectors. They saw the need for increased research and the maintenance of in-house facilities to enable the physical realization of prototype hardware. The United States was still in the midst of the Cold War, and the strategic deterrent was of prime concern. The ocean threat was the ballistic missile submarine, and little thought was given to the control of the seabed. Robotics was mentioned, but UAVs and the drone population explosion were not.

A lot of the predictions were influenced by underlying assumptions (e.g., little or no staff and facilities growth and the Navy being primary contractor accounting for 65-70% of the work) that had been overturned as APL entered the 21st century. In the 21st century, the Laboratory's staff has grown significantly (its technical staff has almost tripled), its facilities have expanded by almost a million square feet, and the Navy and the Missile Defense Agency (MDA) represent less than 50% of APL's work.

Also, one has to remember that the senior fellows were not privy to many events that helped shape the world environment in the late 20th and early 21st centuriesthe rise of the internet and email and the ubiquitous use of portable electronics equipment (computers to smartphones); the end of the Cold War; the events of 9/11; the artificial intelligence revolution; and the COVID-19 pandemic, to name a few. All these events have had a strong impact on the scale and nature of APL's work today and were unforeseen by the senior fellows. As we know, hindsight is 20-20, but foresight is rarely clear and is usually clouded by the underlying assumptions of the day. Obviously, it was no different for the senior fellows.

## SUMMARY

This article is a brief retrospective of the senior fellows report to the director in 1983. It highlights some of the projections in the ~90-page report and provides some insights on how they apply (or do not apply) to APL today. The report is an interesting read, not only for its projections but also for its use of language and phraseology by great APL technical leaders nearing the end of their careers.

## REFERENCES AND NOTES

$^{ 1}$Carl O. Bostrom is a retired APL director, having served in that position from 1980 to 1992. In 1960, he joined APL as a senior staff physicist and helped start a group to research the space environment. Between 1960 and 1980, he had a variety of responsibilities ranging from instrument design and data analysis to management of satellite development and space systems. From 1974 to 1978, he was the chief scientist of the Space Department and served as department head from 1979 to 1980. He served on many advisory boards, committees, and panels and received numerous awards and honors. Since retiring in 1992, he has worked as a consultant in research and development management and space systems. For more details on his career, see H. E. Worth, "The visionary directors of APL: Creating and nurturing a national resource," Johns Hopkins APL Tech. Dig. , vol. 34, no. 2, pp. 333-348, 2018, https://secwww.jhuapl.edu/techdigest/Content/ techdigest/pdf/V34-N02/34-02-Worth-Directors.pdf.

$^{ 2}$H. C. Anderson, W. H. Avery, J. T. Massey, C. F. Meyer, R. C. Morton, and A. M. Stone, "APL in the twenty-first century," special report to the director from the senior fellows, APL Archives Document ARC 000313563, Jun. 1983.

$^{ 3}$Ten predictive methods are briefly described in the report: genius forecasting, trend analysis, consensus forecasting, simulation forecasting, cross impact forecasting, decision tree forecasting, structural certainties, overriding priority forecasting, prime-mover forecasting, and sequential development forecasting. These ten methods were drawn from four relative current references at the time: (1) D. Bell, "Twelve modes of prediction: A preliminary sorting of approaches

in the social sciences," Daedalus , vol. 93, no. 3, pp. 845-860, 1967); (2) H. Kahn and A. J. Weiner, The Year 2000: A Framework for Speculation on the Next Thirty-three Years , New York: Macmillan, 1967; (3) J. Nesbitt, Megatrends: Ten New Directions Transforming Our Lives , New York: Warner Books, 1982; and (4) A. Toffler, The Futurist , New York: Random House, Inc., 1972.

$^{ 4}$A. Kossiakoff, "In Memoriam: William H. Avery (1912-2004), Johns Hopkins APL Tech. Dig. , vol. 25, no. 2, pp. 173-175, 2004, https:// secwww.jhuapl.edu/techdigest/Content/techdigest/pdf/V25-N02/2502-Avery.pdf.

- $^{ 5}$K. A. Potocki, A. Kossiakoff, L. Smith, R. Creswell, L. P. Montanaro, et al., "In Memoriam: Robert C. Morton 1915-1984," Johns Hopkins APL Tech. Dig. , vol. 5, no. 2, 1984, pp. 197-203, https://secwww.jhuapl.edu/ techdigest/Content/techdigest/pdf/V05-N02/05-02-Memoriam.pdf.
- $^{ 6}$R. D. Semmel, "Defining innovations," Johns Hopkins APL Tech. Dig. , vol. 34, no. 2, pp. 107-113, 2018, https://secwww.jhuapl.edu/techdigest/ Content/techdigest/pdf/V34-N02/34-02-Semmel.pdf.
- $^{ 7}$F. J. West, Sea Plan 2000: Naval Force Planning Study , Washington, DC: Department of the Navy, 1978.

<!-- image -->

- $^{ 8}$APL, "Defining innovations," https://www.jhuapl.edu/about/defininginnovations (accessed Jun. 29, 2023).
- $^{ 9}$APL Public Affairs, "Bullseye! NASA's DART mission impacts asteroid target in world first," press release, Sep. 26, 2022, APL, Laurel, MD, https://www.jhuapl.edu/news/news-releases/220926-nasadart-mission-strikes-asteroid-target.
- $^{10}$A. E. Kedia and J. A. Krill, "Inspiring innovation and creativity at APL," Johns Hopkins APL Tech. Dig. , vol. 35, no. 4, pp. 363-379, 2021, https://secwww.jhuapl.edu/techdigest/Content/techdigest/pdf/V35N04/35-04-Kedia.pdf.
- $^{11}$H. K. Charles Jr., "The future of graduate-level education at APL," Johns Hopkins APL Tech. Dig. , vol. 35, no. 4, pp. 549-551, 2021, https:// secwww.jhuapl.edu/techdigest/Content/techdigest/pdf/V35-N04/3504-Charles.pdf.
- $^{12}$While the JHU Lifelong Learning Program is aimed at providing continuing education for the general populace, it has provided significant teaching opportunities for the APL staff, thus enhancing their skills and technical reach in the world community.

Harry K. Charles Jr., Research and Exploratory Development Department, Johns Hopkins University Applied Physics Laboratory, Laurel, MD

Harry K. Charles Jr. is a program manager and group supervisor for the APL Education Center in the Research and Exploratory Development Department and associate dean for nonresidential graduate programs at the Johns Hopkins Whiting School of Engineering. He has a BS from Drexel University and a PhD from the Johns Hopkins University, both in electrical engineering. Harry has over 40 years of experience in the microelectronics field and is a specialist in electronics packaging. He has over 215 major technical publications, holds 17 US patents, and is a life fellow of both IEEE and the International Microelectronics and Packaging Society

(IMAPS). He is also the editor-in-chief of the Johns Hopkins APL Technical Digest . His email address is harry.charles@jhuapl.edu.

A. A. Akinpelu et al.

## Technology Visions for APL's Centennial

<!-- image -->

Akinwale A. Akinpelu, David W. Blodgett, Glenn E. Mitzel, Morgana M. Trexler, Kaushik A. Iyer, William G. Bath, Lynn M. Reggia, David B. Helmer, Ashutosh Dutta, Nancy F. Andersen, and Jerry A. Krill

## ABSTRACT

The Johns Hopkins University Applied Physics Laboratory (APL) will celebrate its centennial in 2042, about 20 years from the time of this writing. As the Lab looks toward this milestone, a team comprising APL staff members who are fellows of several premier technical societies or APL master inventors predicted which innovations and technologies might become global trends by 2042 and, consequently, could be considered as potential elements in APL's science and technology strategy. This article describes their predictions.

## INTRODUCTION

Akinwale A. "Wale" Akinpelu

For over 80 years, APL has been making critical contributions to our nation's critical challenges, creating scientific breakthroughs and developing innovative solutions to complex research, engineering, and analytical challenges. Among APL's thousands of contributions to national security and space exploration are a number of defining innovations, game-changing breakthroughs that have created inflection points in history. Examples of defining innovations are the radio proximity fuze, which changed the course of key battles in World War II, and the Transit system, the world's first satellite-based global navigation system. 1

As the Lab looks toward its centennial, a team of APL staff members considered which technical trends could become global game-changers by 2042. This team, known as the Centennial Task Force, includes two APL master inventors, an honor bestowed on staff members who have been granted 10 or more US patents based on APL intellectual property, and four fellows of premier

technical societies. The hope is that their predictions help APL anticipate, leverage, or contribute to realizing advances that might ultimately lead to defining innovations. They briefed their ideas at an event called APL Showcase held at APL on August 2, 2022. This article summarizes their projections.

In the first section, "Faster than the Speed of Thought," master inventor Dave Blodgett describes the concept of humans no longer constrained by the speeds at which our brains can transmit and receive speech and text.

The second section, also by Dave in collaboration with Force Projection Sector chief engineer Glenn Mitzel, describes the concept of coherent distributed networks (CDNs). Such networks could, for example, enable accurate identification of objects in space.

Master inventor Morgan Trexler, in the section titled "Game-Changing Materials on Demand," discusses a robust approach for warfighters in the battlefield, or astronauts on the moon, to fabricate tools, structures,

materials, and power sources from the resources around them. This approach would drastically reduce the loads they must carry and mitigate supply chain and logistics issues.

The fourth section, by American Society of Mechanical Engineers (ASME) fellow Kaushik Iyer in collaboration with Rama Venkatasubramanian, Ann Darrin, Ralph McNutt, and Paul Ostdiek, discusses NuX, or "Nuclear Power for Extreme and Space Environments." NuX is a concept to generate abundant nuclear energy in space.

Institute for Electrical and Electronics Engineering (IEEE) fellow Jerry Bath, in the section titled "Shifting Human-Machine Interaction to Symbiosis," considers an approach for human-machine cooperation. In the envisioned future, humans and their machine teammates learn together and increase their levels of cooperation and codependence over time.

The sixth section, by IEEE fellow Ashutosh Dutta and AIAA fellow Nancy Andersen, discusses "Assured Ubiquitous Communications." This concept centers on the development and deployment of a communications network that can be reconfigured instantaneously and with no service disruption in response to outages or cyberattacks.

Why are these centennial predictions important? Because we have observed that technology predictions stimulate creativity and innovation. For example, in 1876, the telephone mode of communication was invented. In 1963, a telephone company manager predicted the development of a smartphone that we would one day carry with us.$^{2}$ As we know, by the 2000s, this prediction had become a reality (Figure 1). We hope that the predictions by the Centennial Task Force will similarly stimulate creativity and innovations at APL.

But, as we also realize, many futuristic predictions fall short. In a companion article in this issue,

Figure 2. Data flow limited only by the speed of thought.

<!-- image -->

Harry Charles, a master inventor and an IEEE lifetime fellow, describes and assesses the technology projections for the 21st century that APL senior fellows made in 1983, on the occasion of the Lab's 40th anniversary. He notes which projections were realized and which were not.

We acknowledge the possibility that only a few-or even none-of our Centennial Task Force predictions will come to pass by 2042. But then again, one or two of these predictions just might come to fruition.

## FASTER THAN THE SPEED OF THOUGHT

David W. Blodgett

What does it really mean to operate faster than the speed of thought? What problem are we trying to solve when thinking about this concept? What is the capability gap that we are trying to close? Imagine if the brain's transmit or receive bottleneck had been disrupted and information flow was no longer bandwidth limited by either speech or text. What could we accomplish with unlimited data communication rates between the brain and the outside world? The possibilities are endless. So, how could we remove that bottleneck and access all the information in our brains? How could we decrease the time to decision and action? That is the game-changing technological breakthrough we envision (Figure 2).

APL and other research organizations are currently working to develop a brain-computer interface (BCI) that is able to read and write information to the brain. So back to the original question-what could we accomplish with unlimited data communication rates between the brain and the outside world? This brings us right to the "imagine if" scenario.

Imagine a battlefield with a squad of soldiers who want to convey actionable information (Figure 3). If limited by voice, the exchange might go something like this: "There's a building over there, second floor, second window to the right. I think I see a sniper." That is a lot of information both for the observing soldier to give and for the other soldiers to process. But what if they could

Figure 1. Technology predictions stimulate creativity and innovation.

<!-- image -->

Figure 3. Real-time thought integration across teams.

<!-- image -->

simply convey an image of the battlefield highlighted with danger zones? They could provide potentially life-saving information in the time it takes to blink. As the old adage goes, a picture paints a thousand words, and this is just one example of disrupting the information bottleneck.

In many ways, one can think of this as a reimagining of one of APL's defining innovations: the Cooperative Engagement Capability (CEC).$^{3}$ At its heart, CEC was motivated by the US Navy's need to combine remote data from dispersed units to provide coverage that no single ship-or even group of ships-could offer. Similarly, situational awareness could be enhanced by cooperative BCI integrating neural information across a squad, a platoon, or even an entire battalion. Think about how that would change the role of the commander.

Another "imagine if" scenario is the seamless integration of external sensor data into the brain (Figure 4). These sensors could provide data as complex as infrared or hyperspectral imagery acquired from uncrewed aerial vehicles (UAVs). Coupled with information from existing senses, these data would augment perception of the environment.

APL started its journey to realize a BCI many years ago at the inception of the Defense Advanced Research Projects Agency (DARPA) Revolutionizing Prosthetics program.$^{4}$ The vision of that program is as real today as it was 15 years ago. The Revolutionizing Prosthetics team demonstrated the ability to record and encode neural activity from and to the brain, resulting in actionable events. Examples include control of the

Modular Prosthetic Limb to support limb restoration for wounded warriors and the ability to fly an aircraft in a flight simulator. This work continues through DARPA, the National Institutes of Health (NIH), and even private industry.

However, much of this work focuses on development of invasive arrays-that is, arrays requiring brain surgery-to provide that high-speed interface to the brain. More recently, there has been a push to develop noninvasive neural interfaces. While regulatory and ethical questions will need to be addressed for invasive neural interfaces to be used by people who are not affected by sensorimotor injuries or diseases, the path toward use of noninvasive interfaces with similar capabilities is much clearer. Imagine being able to simply put on a headpiece that seamlessly syncs with your brain.

Figure 4. Persistent 3-D virtual world that coexists with the physical reality.

<!-- image -->

DARPA shares this vision and has been investing in multiple concepts-including APL's-to explore the realm of possibility in this domain (Figure 5). Even Facebook has invested in this area; its stated goal is to develop a BCI device allowing mobile device and computer users to communicate at a speed of 100 words per minute, far faster than the speed at which anyone can type on a phone.

The question, then, is, What else has to be accomplished over the next 20 years to realize a truly noninvasive neural interface? How would we leverage such a capability? If we were to invest at APL, where would we invest (Figure 5)?

One of the places APL can move the needle is in envisioning how a neural interface could impact and enhance solutions to warfighter challenges. To date, most of the fundamental research in BCI device development has been led by APL's Research and Exploratory Development Department (REDD), but understanding the needs of warfighters will require collaborations across all of APL. What are the known capability gaps that would represent opportunities for a neural interface? What would that neural interface have to achieve in terms of information bandwidth, accuracy, and bit error rate? What kind of information would need to be conveyed?

Extensive work will also be required to both miniaturize and harden the device. How do we fabricate these things? It is one thing to encode or decode neural information in an academic lab setting, but that is a far cry from deploying a technology on the battlefield. Fortunately, APL has a strong background in transitioning

technologies from fundamental research to the battlefield; its critical role in operationalizing light detection and ranging (lidar) is one example.

Another key challenge will be effective integration of artificial intelligence (AI), specifically leveraging AI to augment the neural interface's performance. A simple example is the control of a prosthetic limb. It would not be efficient to record every motor control step necessary to pick up an object (e.g., move your elbow, now move your fingers, now grab, now raise your arm . . .)." Instead, the AI should be responsible for these actions so that the person can simply think "pick up the glass" and the limb picks up the glass.

Finally, neural interfaces will require secure communications as they link directly to the brain. This requirement is in addition to exploring and tracking ethical issues involved with their use. Ultimately, the realization of this device will revolutionize both the way our sponsors address their most critical challenges and the way members of society as a whole live their daily lives, making this a prime example of an inflection-point technology.

## COHERENT DISTRIBUTED NETWORKS

Glenn E. Mitzel and David W. Blodgett

Large antennas have distinct advantages in sending and receiving electromagnetic signals. Generally, larger antennas emit or collect more of the intended signal energy and in preferred directions, thus increasing sensitivity and resolution. The benefits of larger antennas have driven

Figure 5. Ongoing work at APL in noninvasive neural stimulation and recording.

<!-- image -->

some extreme engineering, exemplified by China's enormous radio telescope, the Five-hundred-meter Aperture Spherical radio Telescope (FAST) (Figure 6).

However, the quest for larger antennas may be reaching its practical fabrication limits without radical changes in the approach. The size limits could be lifted, ostensibly without bound, if the larger antenna could be built from smaller distributed antennas. But, to realize the greatest benefit from the distributed networks, the antennas ideally need to be operated coherently; that is, the raw constituent signals aimed at or measured from specific distant points must be adjustable so that the signals' cycles can be aligned. Such configurations are known as coherent distributed networks, or CDNs.

Figure 6. China's FAST. (Liu Xu/Xinhua News Agency.)

<!-- image -->

Since the constituent CDN signal cycles are aligned, the amplitude of the sum is proportional to the number, N , of contributing antennas, assuming common antennas and local signal strengths. Since the power of a signal is proportional to the amplitude of the signal, CDNs boost combined signal power by a factor of N $^{2}$, an attractive, frequently cited theoretical improvement in sensitivity over a single CDN element. Also, an antenna's ability to resolve closely spaced distant sources is proportional to the maximum spread of the antenna. Since the maximum spread of a CDN is no longer limited by the largest dimension of a monolithic antenna, the CDN resolution capability can be stretched considerably, theoretically without limit. Of course, these CDN benefits are often mitigated by practical considerations and engineering challenges. But the potential benefits are hard to ignore.

Conceivably, CDNs could enable a number of applications. Among them are unprecedented or even otherwise unachievable capabilities to detect and track faint signals, distinguish closely spaced objects, identify objects with great precision, or extend the range of communication systems. Such capabilities may prove to be game-changers in astronomy, military conflicts with technologically sophisticated adversaries,$^{5}$ or cislunar domination. 6

However, although CDNs may hold promise for enabling remarkable applications by overcoming practical limits on the fabrication of monolithic antennas, coherency

itself imposes big, unique challenges. Allowing for imperfections, the constituent signal cycles from distributed antennas must be synchronized to within 5% of the electromagnetic wavelength. As the electromagnetic frequency increases, this requirement can become daunting, as illustrated in Figure 7. In the high-frequency (HF) band, the synchronization requirement is tens of nanoseconds in time or meters in position, both routinely achieved anywhere in world with GPS. But as the frequency increases, for example, to X-band (~10 GHz) where many radars operate, the synchronization requirement tightens by as much as a factor of 1,000, to tens of picoseconds or millimeters. At near-infrared, the synchronization requirements are overwhelmingly small, and other engineering challenges may preclude coherent operation.

Thus, CDNs present formidable challenges, arguably feasibly met, at least for certain portions of the electromagnetic spectrum. APL demonstrated a CDN-enabled radar for deep-space observation, known as Deep Space Advanced Radar Capability (DARC). DARC operates at S-band (~3 GHz) frequencies and is synchronized across multiple transmit antennas and receiving antennas, as illustrated in Figure 8.$^{7}$ The demonstration proved that a paper concept inspired by a 2009 NASA study could be realized, thus enabling a highly tailored, scalable, and affordable solution to a challenging surveillance problem. Furthermore, for synchronizing CDNs at even higher frequencies, APL demonstrated femtosecond time synchronization in free space.$^{8}$ These and other successes position APL to address the CDN challenges and applications more comprehensively. The potential benefits of scalability for improved sensitivity and resolution, coupled with APL's expertise in this area, make CDNs a goal worth considering in APL's Centennial Vision.

Figure 7. CDN temporal/spatial synchronization requirements.

<!-- image -->

Figure 8. DARC Technology Demonstrator.

<!-- image -->

## GAME-CHANGING MATERIALS ON DEMAND

Morgana M. Trexler

Imagine that missions were not limited by materials' availability, properties, and performance. What if we could quickly conceptualize and make new materials from the resources around us, no matter where we were? Discovery of materials is a driver for industrial innovation, but it is an extremely slow process, usually taking on the order of a decade. And it is largely reliant on trial and error, which is not effective or efficient.

Think about the periodic table. There are endless combinations of materials. How do we find the needle in the haystack? And what if the haystack is as big as the universe? How do we even start? This is the scale of the materials discovery challenge, and because of that, we normally stick close to what we know. We change composition slightly and hope the properties and performance improve and we find something that will enable what we need.

However, approaching materials discovery by using AI integrated with high-throughput material synthesis and highthroughput characterization opens the possibility to explore the unknown more strategically. By leveraging computationally driven discovery, we can potentially determine how to best use resources in austere environments and to make use of them to create new capabilities, regardless of where we are and what we have with us.

In that next frontier, we need the ability to discover the undiscoverable in a targeted and efficient manner in order to make new materials with unprecedented properties on demand. So imagine now a battlefield that our warfighters can set out to with minimal supplies so they are carrying a much lighter load (Figure 9). They can fabricate whatever they need as situations arise; they can make their tools, structures, and power sources from whatever they find around them.

Reducing load is a huge benefit, as is eliminating challenges with the supply chain and logistics. It may seem silly to fabricate a simple widget on the battlefield, but if you think about the cost and time to otherwise ship it to the battlefield, and the downtime and performance impacts in the meantime, it is actually incredibly impactful. Similarly, when an aircraft breaks and a replacement part is needed, ordering, fabricating, and shipping that part significantly impacts performance, preventing pilots from logging flight time and conducting their missions. There are huge trickle-down effects related to

Figure 10. Resilient Arctic operations.

<!-- image -->

Figure 9. In situ battlefield manufacturing.

<!-- image -->

manufacturing and supply chain challenges. So what if we could take the natural materials surrounding the battlefield and fabricate supplies, tools, or whatever is needed, on demand?

The Arctic is becoming operationally important, but there are a lot of technical challenges associated with those cold temperatures. Imagine an efficient and effective Arctic operations setup powered by revolutionary battery materials that can maintain long-duration performance in cold temperatures (Figure 10). Battery chemistry traditionally has

Figure 11. Emergent lunar infrastructure.

<!-- image -->

a very short lifetime, so we have limited power storage capabilities. Our energy storage capabilities and power for autonomous vehicles, heated textiles, and human-carried devices are limited, and that limits capabilities. So what if we could discover new chemistries for those batteries and revolutionize our capabilities in the Arctic?

Imagine the moon as a thriving cislunar economy based on mining and processing the lunar regolith into structural materials for lunar habitats, solar arrays for energy collection, and fuels for space maneuverability and exploration. Regolith has a variety of compositions that can be separated and processed into functional components. We could create an infrastructure for cislunar operations (Figure 11), fuel for missions to and from geosynchronous orbit, and oxygen for life support, for example. So what can we enable with these lunar resources with a novel discovery platform? Additionally, what if we were to exploit the different atmospheric and gravity conditions on the moon and use those to our advantage during fabrication to make materials that cannot be made here on Earth? And, perhaps, we could also use some of these new materials to solve challenges here on Earth.

APL is already working toward this future of novel materials discovery.$^{9,10}$ A multiyear research project has been focusing on disrupting the materials discovery paradigm by accelerating the process and optimizing where to look for novel solutions. We are working to solve critical challenges by discovering new materials and reducing discovery timescales from 10 years to months, weeks, and hopefully even less. There is no way we can make and test all the possible materials, so models are helping us to predict and down-select where in the compositional space we should be looking to even target discovery of new materials. We can then synthesize using high-throughput approaches, characterize the materials,

and use the resulting data to retrain the models, closing the "predict-make-measure" loop and teaching the models so that their accuracy improves over time. We have already demonstrated significant increases in throughput accuracy and the rate of discovery.

For proof of concept, we have developed machine learning models to accelerate discovery of superconductors in a targeted fashion. We have predicted, made, and measured many different compositions and closed this loop several times, demonstrating accelerated learning (Figure 12). Additionally, we are developing methods to make better use of the inherently sparse and noisy materials testing data by supplementing those data with computational modeling-generated data. So far, we have rediscovered five materials that were unknown to the training model. We have also discovered, fabricated, and validated a previously unknown superconductor. Though we originally focused on developing models that

Figure 12. Disrupting the materials discovery paradigm.

<!-- image -->

can forward-predict properties for superconductors, this framework is extensible to other systems. We are also working to discover low-temperature electrolytes and magnetic materials that do not contain rare earth elements.

Looking forward to APL's centennial, we believe that APL could revolutionize materials discovery and in situ manufacturing. Our grand vision is to integrate AI, accelerate discovery, and overcome the current paradigm of intuition-driven trial-and-error materials discovery (Figure 13). We believe that by integrating AI, machine learning, data management, materials science, and advances in computational innovations-maybe quantum computing in the future-we can begin to discover, design, and fabricate new materials on a much

Figure 13. Game-changing materials on demand.

<!-- image -->

quicker timescale, resulting in unprecedented speed and automation of discovery. And we hope that then, whether we are in Antarctica, on the moon, or even on Mars, we can create new capabilities for our next frontier.

## NuX: NUCLEAR FOR EXTREME AND SPACE ENVIRONMENTS

Kaushik A. Iyer

In response to being asked to look 20+ years into the future and prioritize cutting-edge research areas and notional missions, the bidecadal technology disruption we present to you is NuX. NuX stands for Nuclear Power for Extreme and Space Environments.

Imagine a world where we are a spacefaring civilization (Figure 14). What might that world look like? Would it involve expanding sustainable human presence into cislunar space on lunar soil or other planetary bodies, perhaps in some ways that have already been described in science fiction novels and in other ways we cannot possibly foresee today?

This then takes us to a world where we have abundant and

replenishable energy, both in space and here on Earthpower that is required for us to truly thrive as a spacefaring civilization. We believe the drive toward pervasive and resilient power sources applicable to both extreme terrestrial and space environments will start to manifest at high technology readiness levels (TRLs) by 2042.

Other nations are believed to have already deployed a miniature radioisotope power system (RPS) on the

Figure 14. Infrastructure for a truly spacefaring civilization takes form.

<!-- image -->

dark side of the moon or have the capability to do so. The advent of new commercial space entities and investment will drive the development of the radioisotope power and propulsion in space needed to expand the envisioned commercial activities and government operations on the moon in the next 20 years.

The confluence of urgent military competition and commercial capital will cause a shift in government (NASA and Department of Defense) policy to accommodate this technology development at private-sector cost. Government will play a guiding role, owing to numerous potential benefits, will from the private sector, and minimal risk to the government. Twenty years from now, we believe that the institutions that are foundational for a spacefaring civilization will possibly have started to emerge (Figure 15).

Figure 15. In-space power generation technology will drive envisioned futures on the moon, in cislunar space, and in other extreme environments.

<!-- image -->

One can imagine that we will go from single space-built and -powered satellites to the future that we have just outlined, much in the way that our oceanic shipping industry, born from the craft of building single seafaring vehicles, evolved into building

military fleets and then into the present-day massive commercial shipping industry. NuX can do in space in the second half of this century what nuclear-powered aircraft carriers did for the United States in the second half of the previous century.

We expect this world will have its own infrastructure, human presence in space, policy and regulations, and commercial and government activity related to invention, manufacturing, science, defense, and so on, all enabled by pervasive and resilient power sources in space (Figure 16). In this new world, APL can bring the ability to straddle military and commercial space and serve as a trusted head node with a unique ability to demonstrate flagship missions of high technical complexity, define the state of nuclear power technology, and develop a

roadmap for safe deployment in space and austere terrestrial environments.

The Space Age began on October 4, 1957, but the Nuclear Space Age began on June 29, 1961, when APL launched the first nuclear power source, Transit 4A.

Figure 16. New governance, policies, and institutions will enable human presence, virtual and in person, in extreme environments in ways previously not possible.

<!-- image -->

Figure 17. APL's unique legacy in advocacy for, and implementation of, nuclear power technology in extreme environments expands applications into the New Space Age with a focus on national interest.

<!-- image -->

Think about that-how fast we went from somebody else flying to APL flying a nuclear power source. Four years is all it took. For that launch, APL engineers held that the risk from the radioisotope thermoelectric

generator (RTG) was less significant than the risk from the solar cells and the nickel cadmium battery in the power system.

Since that time, APL has continued to contribute to nuclear technology through its work with several sponsors (Figure 17). Transit 4A flew a SNAP-3 RTG, and Triad flew what the Department of Energy (DoE) calls the Transit RTG. APL was also a member of the team that developed the general-purpose heat source (GPHS) RTG that flew on the Ulysses, Galileo, and Cassini NASA missions.

As the 21st century dawned, APL was building the New Horizons spacecraft to go to Pluto and beyond. New Horizons was powered by the GPHS-RTG. A few years after that launch, the core of what became APL's thermoelectric leadership had built the

first micro-RTG on a DARPA program called Micro Isotope Power Source. Today this APL team is leading the creation of an advanced version of the energy converter technology$^{11}$ at the heart of the GPHS-RTG to enable NASA's outer-planetary missions under design to possibly last past 2050. And consider an example that opens our imaginations even wider: NASA is now trusting APL to build a nuclear-powered quadcopter, Dragonfly, to fly and hop around on Saturn's moon Titan. At APL, the Nuclear Space Age continues.

So imagine all the things we could do as a civilization for humanity, all the critical challenges we could solve, if we could create energy with ease anywhere we want. So how can we do this? Can it be done? The answer is yes, possibly. We start by finding a way to create energy and fuel that creates itself,$^{12}$ so to speak, once the

process is started (Figure 18). We do this using the sun, and we do it safely. By combining special materials, either sourced from Earth or the moon with a neutron generator, we can generate power in space without fission.

Figure 18. Transforming benign materials into power-generating radioactive isotopes creates opportunities to explore and exploit the New Space Age. (Refer to Lavelle et al.$^{12}$)

<!-- image -->

The core of this technology is in use today in the medical community, in a capability known as the gamma knife, to treat tumors.

## SHIFTING HUMAN-MACHINE INTERACTION TO SYMBIOSIS

William G. "Jerry" Bath, Lynn M. Reggia, and David B. Helmer

We probably are not quite as far along with this vision as some of the others discussed in this article, but the prediction is that something might happen in the next 20 years that could have a significant impact.

Imagine a world where human and machine teammates sort of grow up together. Today you can talk to your phone, you can talk to your lamp, and you can talk to

Figure 19. Humans and machine teammates learning together.

<!-- image -->

your car. But imagine that you are now talking to something or communicating with something, or even brain interfacing to something, that is persisting over time and over the thousands of interactions you have when solving problems in your life. It learns what information you need when you are successful and when you are not successful; it learns whether information it provides is what

you wanted. And this gradually leads then to an ability to essentially collaborate, for the machine to predict what you need and for you to see things in a context that is provided by the machine.

Figure 19 is a symbolic illustration of this concept. Obviously, the machine is not growing and standing up and walking, but over time, the algorithms and code in the machine are learning about the human, and they are learning enough that the machine can be a true digital teammate.

If we all have these digital teammates, then we can get together to solve a problem. The people in the scenario shown in Figure 20 are trying to solve what is basically a military problem, and everybody is bringing a different perspective. The person on the left is talking about missiles and

radars and combat systems. There is another person on the right who is talking about economic sanctions, war crimes, world leaders, and other topics that are equally important. And there could also be someone in the room talking about logistics. These are the kinds of things we do not all understand equally. We are lucky to understand even one of these topic areas.

Figure 20. Human and machines with the same level of understanding.

<!-- image -->

Figure 21. Distributed collaborative decision-making.

<!-- image -->

However, each of our digital teammates provides an ability to present that information to us in a way we can understand. And it does that by collaborating with the other digital teammates. The result is that we see the same picture. It will not be perfect, but to some degree we are able to see the same picture.

So now if you can see the same picture, could you

work together to solve a problem, not just the N humans, but the 2 N humans plus digital teammates? Imagine a world in which we could do that. And in that world, the 2 N of us could be superhuman, more powerful than just the humans alone, and super AI, more powerful than just a big computer running AI because we would bring a human perspective to it.

Figure 21 conveys this idea. The left column shows this collaborative decision-making in a nonmilitary setting. For example, when flooding occurred in Kentucky in 2022, we had to bring together first responders, medical personnel, technicians to fix the electrical grid, and people responsible for clearing out the space. All that needed to be coordinated somehow. In another example, Hurricane Katrina, this

coordination did not go very well. But the approach of bringing all these people together through their digital teammates and having the teammates collaborate is a way to arrive at a more strategic solution to the problem.

The middle column conveys competition, not yet warfare but competition between states. So now picture the US president and the speaker of the House of Representatives each having a digital teammate, and those teammates can collaborate and present things in their own context. For serious geopolitical considerations, like economic and foreign relations competition, this approach could be hugely beneficial.

On the right is conflict itself, which is what APL mostly works on. In this area, speed is essential. The military has a notion of decision dominance-I can be out-

numbered and outgunned but can still win because I have the ability to make better decisions faster. That notion is right in the sweet spot of this digital teammate idea.

So, what are we doing today? Figure 22 shows some examples. As mentioned at the start of this section, we are not quite as far along on this as we are on some of the other predictions discussed in this article. We are just

Figure 22. What APL is doing today to shift human-machine interaction to symbiosis.

<!-- image -->

starting. One of the first things we are doing is trying to get machines to the state where humans can trust them to make decisions. Through the Johns Hopkins Institute for Assured Autonomy (IAA), we are exploring the algorithms in the AI world that could lead to trustworthy interaction. We are also looking at building the facilities and laboratories that will enable us to conduct experiments with warfighters so that we can understand their problems. We are investigating ethics, considering whether we can trust machines to make unbiased decisions. The robotic figure on the left of Figure 22 is holding an angel in one hand and a devil in the other to illustrate the ethics aspect. And, finally, we are building user interfaces. Dave Blodgett talked about a very advanced BCI, but we are also building less-advanced interfaces to facilitate data transfer from humans to machines.

We have made a start, but where could APL go in the long run (Figure 23)? To be frank, I doubt that we will be the place that designs these digital teammates worldwide for everybody. That work will probably come out of the commercial world and be driven by people making money doing it. I think we can assume that someday every 18-year-old who enlists in the military, every astronaut, every medical provider will have grown up with a digital teammate. They will bring that knowledge to the job at hand and to the next job as well. And that will change the whole paradigm of how things operate.

APL's role will be to conduct the critical experiments and development so that those digital teammates are what our soldiers and medical providers and astronauts need for our mission areas. If we can do that, people will be able to evaluate courses of action very quickly, faster

than our adversaries, and gain the decision dominance advantage in most of our mission areas. And there are analogies in the nonmilitary cases as well.

## ASSURED UBIQUITOUS COMMUNICATIONS

Ashutosh Dutta and Nancy F. Andersen

What is going to happen 20 years from now? We are keeping track of what is happening in the world, and we are asking how we can divide communication that can have different verticals-not only military but commercial, agriculture, and health. Communication is the fabric, and we have to develop a fabric that will help evolve this concept.

Three examples are presented here. The first example is communication at a futuristic scale (Figure 24). This example assumes a lot of data, different kinds of networks-low Earth orbit (LEO) and medium Earth orbit (MEO) satellites, different types of cellular networks, and Wi-Fi-and a first responder as the user. The first responder arrives at the scene and starts communicating using cellular communication, perhaps 4G or 5G, and then a hurricane, or some other catastrophic event, affects cellular communication and the tower becomes nonoperational.

At that point, this first responder is communicating with a doctor and is trying to treat a patient. The first responder must be able to seamlessly switch over to Wi-Fi and still maintain priority service for communication. Then the first responder rides with the patient

Figure 23. APL revolutionizing mission space via human-machine teaming in 20 years.

<!-- image -->

in an ambulance to a helipad and must switch back to cellular when the Wi-Fi network is out of range. Once the helicopter is en route to the hospital, communication switches again, this time to satellite communications. This scenario illustrates handoffs between different types of wireless communication technologies, namely cellular, Wi-Fi, UAVs, and satellite. This communication must be ubiquitous, and secure at the same time, because it may be transmitting patient data and other sensitive information.

How can we make sure the future communication infrastructure is distributed, resilient, and adaptable? There may be a surge of data, so how can we scale the network up and down to support the surge without affecting the quality of service? These are the

Figure 24. Communications at a futuristic scale.

<!-- image -->

interesting questions we need to study, and several APL mission areas are doing just that.

The next example is predictive security (Figure 25). An attack usually targets different parts of the network, not only on the radio network. The 4G-5G network, for example, has different components-radio access networks, the cloud, end devices, and applications. Today

we usually take reactive measures when the attack is happening or after it has happened; we try to determine how quickly we can detect and mitigate or recover from the attack.

We should be focusing on predictive measures-identifying certain predictable traffic behaviors or patterns so that we can anticipate that an attack is coming and prevent it altogether. In what is called a zero-day attack, we have no malware signature or any other knowledge about the attack. We are unaware of the vulnerability the attack will exploit. To mitigate these kinds of attacks, we should be looking at technologies that can predict them. It is important to develop self-learning technologies that can detect attacks proactively, preventing both known and unknown attacks.

A third example is auto-

configuration (Figure 26). Think back to the example of communication at scale. Consider scenarios like 9/11, Hurricane Katrina, or an active assailant situation. An ad hoc network is set up with perhaps five nodes, and then a lot of people start communicating over that network. High volumes of data need to be transmitted, and the data traffic grows exponentially. The network grows

Figure 25. Predictive security.

<!-- image -->

from having one node or 10 nodes to having a thousand or even many thousands of nodes. How quickly can we automate and scale up the network?

Imagine the need for microsecond network auto-scaling and digesting context-free, massive amounts of data-many terabytes of data and many nodes. We need a mechanism that will allow us to scale the network up and down within fractions of seconds; we need automation and orchestration that actually help to scale the network. This is important because mission-critical applications need the support to ensure desired quality of service.

These are just three examples. So, where are we today? What are the enablers? A lot of 5G work is happening at APL in collaboration with others in IEEE and the 3rd

Figure 26. Auto-configuration, big data, and unlimited bandwidth.

<!-- image -->

Generation Partnership Project (3GPP; www.3gpp.org).$^{13}$ This work focuses on converged networks (Figure 27). We mentioned Wi-Fi, cellular, and satellite, but there are also wired networks, like Ethernet (depicted by the RJ45 connector in the figure), or fiber connections. We have the option of using various types of networks based on the availability and application need. Hence, the network

has to be ubiquitous and then we can determine how to take advantage of the convergence of wired and wireless networks.

Various next-generation technologies, such as dynamic spectrum sharing, virtualization, and softwarization, do not depend on any proprietary systems or software. Software-defined networking (SDN) can be used to make the network programmable, and mobile edge cloud computing can support ultra-low latency applications, such as remote surgery. We have to take advantage of technologies like network slicing to ensure the quality of service for mission-critical applications.

We have a vision. We know what the state of the art is today. So, as APL, how can we work with the world to explore what we can do 20 years from now? We have seen the evolution of cellular

technologies. Every 10 years a new cellular generation has been introduced. We are in the middle of 5G deployment right now, with 5G being deployed in various parts of the world. People have already started looking to 6G, so we should be investing in Next G (Figure 28). APL is a contributing member of the Next G Alliance (www.nextgalliance.org), the third generation partner-

Figure 27. Current state-of-the-art communications technologies.

<!-- image -->

ship program (www.3gpp.org), the Next Generation Mobile Network (www.ngmn.org), and NSF PAWR (Platforms for Advanced Wireless Research) consortium. APL also leads the roadmap efforts within the IEEE Future Networks Technical Community and, hence, is contributing to the evolution of 6G research and standards.

But to identify and leverage emerging technologies, we need to focus on other areas as well, such as

- · quantum communication;
- · homomorphic encryption;
- · big data;
- · predictive security;
- · assured autonomy;
- · non-terrestrial networks;
- · the metaverse;

Figure 28. Opportunities for APL and the world: 20-year horizon.

<!-- image -->

- · terahertz communications;
- · AI and machine learning;
- · reconfigurable intelligent surface (RIS);
- · biologically inspired communications;
- · resilient distributed computation;
- · distributed smart and programmable networks; and
- · Zero Trust.

## POSTSCRIPT

## Jerry A. Krill

As mentioned, these six visions of the future were presented to interested APL staff at an "APL Showcase" event in August 2022. As also mentioned, several visions could come to fruition commercially without requiring APL to contribute to their development. APL could then leverage these advances in applications as they begin to appear.

For example, as Jerry Bath notes, human-machine synergy (beyond teaming) is likely to emerge from commercial markets, and the best thing APL should do is continue research in conjunction with the IAA to ensure trusted teaming and, eventually if it happens, trusted synergy. Further, as APL develops test bed facilities for studying human-machine partnered combat and command and control systems, we will be in a position

to evaluate emerging synergy processes.

Similarly, Kaushik Iyer points out that APL has been a pioneer in using RPSs from the beginning of both the Space and Atomic Ages and will be involved in their use into the foreseeable future, as exemplified by the Dragonfly mission to Titan. Iyer offers that more could be done to transform RPS technology into ubiquitous and safer systems for spacefaring as well as austere environments on Earth. The DoE labs tend to lead such endeavors. In addition to the NuX technologies mentioned above, nuclear fission reactors for space, initially for long-range propulsion, are being jointly developed under DARPA and NASA sponsorship.$^{14}$ So, APL may invent some aspects of the emerging RPS technology for our applications and will likely one day be

a user, but developing nuclear power systems is not itself a mainline APL mission focus.

Most assured ubiquitous communications technologies and products will be developed by commercial industry as they evolve from 5G to 6G and eventually to 7G in the farther future. Most communications challenges for the extreme distances of space operations as well as the extreme adverse environments, both natural and adversary-induced, in national security domains will continue to require APL contributions. An example is APL's ongoing research to develop a "cognitive communication network" that employs AI to determine the clear channels among a variety of interconnected networks of a military force. 15

The other three predictions, "Faster than the Speed of Thought," "Coherent Distributed Networks," and "Game-Changing Materials on Demand," are areas that may not find commercial investment. At the time of this writing, discussions are underway for APL to consider investing in aspects of these visions.

How the six visions play out as the future unfolds is anyone's guess. But as Harry Charles points out in his companion article about how the predictions of 1982 unfolded, when APL has been a player in the development of visions, we sometimes tipped the balance in making them become realities. This is an opportunity to see to what extent we can predict, leverage, and even invent the technologies of the future "to benefit our society and improve the lives of people throughout the world" (quoting APL's present Centennial Vision vivid description).

ACKNOWLEDGMENTS: Thanks to Dave Van Wie for his overall guidance and insights and to the APL Communications Department team for creating graphics. Thanks to the dozens of people who contributed to discussions on coherent distributed networks (CDNs), particularly Ken Olson, Chuck Quintero, Peter Sharer, and Hank Tillman. Thanks to Claire DeSmit of the Communications Department for help with the NuX project and to the entire NuX team: Ann Darrin, Ralph McNutt, Paul Ostdiek, and Rama Venkatasubramanian. Thanks to the Materials on Demand team: Bob Bamberger, Jodi Berdis, Jenny Boothby, Athonu Chatterjee, Christine Chung, Betsy Congdon, Brenda Clyde, Mallory DeCoster, Brett Denevi, Janna Domenico, Wes Fuhrman, Jarod Gagnon, Kostas Gerasopoulos, Eddie Gienger, Leslie Hamilton, Kapil Katyal, Jen Lambert, Nam Le, Andy Lennon, Jessica Ma, Ian MacLeod, Bobby Mueller, Alex New, Sal Nimer, Michael Nord, Bart Paulhamus, Stergios Papadakis, Nick Pavlopoulos, Mike Pekala, Christine Piatko, Adrian Podpirka, Michael Presley, Lisa Pogue, Ann Pollack, Ali Ramazani, Elizabeth Reilly, Corban Rivera, Chris Stiles, Steve Storck, Jared Townsend, Doug Trigg, Mike Wolmetz, Zhiyong Xia, Dajie Zhang, and Walter Zimbeck. Thanks to Rob Nichols for consulting on assured ubiquitous communications and providing many helpful suggestions and comments. Finally, thanks to the many APL staff members who contributed their ideas to members of the Centennial Task Force during a series of follow-up discussion events after the APL Showcase presentations.

## REFERENCES

$^{ 1}$R. D. Semmel, "Defining innovations," Johns Hopkins APL Tech. Dig. , vol. 34, no. 2, pp. 107-113, 2018, https://secwww.jhuapl.edu/techdigest/Content/techdigest/pdf/V34-N02/34-02-Semmel.pdf.

$^{ 2}$"You'll be able to carry phone in pocket in future," Mansfield NewsJournal , April 18, 1963.

$^{ 3}$APL CEC Team, "The Cooperative Engagement Capability," Johns Hopkins APL Tech. Dig. , vol. 16, no. 4, pp. 377-396, 1995, https:// secwww.jhuapl.edu/techdigest/Content/techdigest/pdf/V16-N04/1604-APLteam.pdf.

<!-- image -->

Akinwale A. Akinpelu, Asymmetric Operations Sector, Johns Hopkins University Applied Physics Laboratory, Laurel, MD

Akinwale A. Akinpelu is a scientist in APL's Asymmetric Operations Sector Transformational Projects Office. He earned a BS in mathematics from Obafemi Awolowo University, a diploma in computer science

from the University of Lagos, and an MS in computer science from Newcastle University under an IBM Fellowship. Wale is a recognized expert in computer and network communication architecture and protocols. He created an innovative solution and a test facility to introduce secure communication services for US government executive members and Department of Defense (DoD) senior leaders. Previously, he was a director at

- $^{ 4}$D. G. Smith and J. D. Bigelow, "Biomedicine: Revolutionizing Prosthetics-Guest editors' introduction," Johns Hopkins APL Tech. Dig. , vol. 30, no. 3, pp. 182-185, 2011, https://secwww.jhuapl.edu/techdigest/ Content/techdigest/pdf/V30-N03/30-3-Smith-Bigelow\_Editorial.pdf.
- $^{ 5}$US Department of Defense, 2022 National Defense Strategy of the United States of America , Washington, DC: DoD, Oct. 27, 2022, https://media.defense.gov/2022/Oct/27/2003103845/-1/-1/1/2022NATIONAL-DEFENSE-STRATEGY-NPR-MDR.PDF.
- $^{ 6}$Cislunar Technology Strategy Interagency Working Group, National Cislunar Science & Technology Strategy , Washington, DC: National Science & Technology Council, Nov. 2022, https://www.whitehouse. gov/wp-content/uploads/2022/11/11-2022-NSTC-National-CislunarST-Strategy.pdf.
- $^{ 7}$S. Jackson and K. Melton, "Johns Hopkins APL delivers new satellite tracking capability to U.S. Space Force," news release, Laurel, MD: APL, Mar. 24, 2022, https://www.jhuapl.edu/news/news-releases/220324-apldelivers-satellite-tracking-capability-to-space-force.
- $^{ 8}$L. C. Sinclair, W. C. Swann, H. Bergeron, E. Baumann, M. Cermak, et al., "Synchronization of clocks through 12 km of strongly turbulent air over a city," Appl. Phys. Lett. , vol. 109, art. 151104, 2016, https://doi. org/10.1063/1.4963130.
- $^{ 9}$APL Staff, "Accelerating materials research with AI Keeps Johns Hopkins APL researchers ahead of 'impossible' challenges," press release, Laurel, MD: APL, May 9, 2022, https://www.jhuapl.edu/news/ news-releases/220509-novel-materials-characterization-analysis.
- $^{10}$B. P. Croom, M. Berkson, R. K. Mueller, M. Presley, and S. Storck, "Deep learning prediction of stress fields in additively manufactured metals with intricate defect networks," Mech. Mater. , vol. 165, art. 104191, 2022, https://doi.org/10.1016/j.mechmat.2021.104191.
- $^{11}$NASA Staff, "Silicon-germanium unicouple paper wins best radioisotope power paper award," news release, Washington, DC: NASA, Aug. 15, 2022, https://rps.nasa.gov/news/61/silicon-germaniumunicouple-paper-wins-best-radioisotope-power-paper-award/.
- $^{12}$C. M. Lavelle, R. Venkatasubramanian, R. L. McNutt, K. Iyer, and A. Darrin, "Avoiding Earth launch of radioactive material: Concepts for in-situ fabrication of radioisotope power generators for cislunar applications," being presented at the Nuclear and Emerging Technologies for Space (NETS) 2023 Conf., Idaho Falls, ID, May 9, 2023. $^{13}$C.-M. Chen et al., IEEE International Network Generations Roadmap (INGR) , 2022 Ed., IEEE Future Networks, 2022, futurenetworks.ieee. org/roadmap.

$^{14}$NASA TV, "NASA, DARPA will test nuclear engine for future Mars missions," News Release, Washington, DC: NASA, Jan 24, 2023, https://www.nasa.gov/press-release/nasa-darpa-will-test-nuclearengine-for-future-mars-missions.

- $^{15}$S. Jones, R. Awadallah, P. Chimento, T. Hanley, J. Hansen, and R. Nichols, "Long-range maritime communications through a multi-link ensemble," in Proc. OCEANS 2019 MTS/IEEE SEATTLE , Seattle, WA, 2019, pp. 1-7, https://doi.org/10.23919/ OCEANS40490.2019.8962745.

Bell Labs and AT&T Labs where he developed and introduced an access network and services for US Fortune 500 corporations, with network availability of 99.9999%, generating over $2 billion in annual revenue. He won the 1998 AT&T Strategic Patent Award for this reliable access network. He led the design, development, and deployment of the US government FTS2000 network, which is now called DoD Information Network (DODIN), an effort for which he won the AT&T Federal Systems Quest Award. He was the winner of the 2005 Harlem YMCA Black Achievers in Industry Award and the 2014 Black Engineer Science Spectrum Trailblazer Award. He holds 8 US patents and 11 foreign patents. He is a senior member of IEEE and American Institute of Aeronautics and Astronautics (AIAA), a member of the Association for Computing Machinery (ACM), and the financial treasurer of the Baltimore Chapter of ACM. His email address is wale.akinpelu@jhuapl.edu.

<!-- image -->

David W. Blodgett, Research and Exploratory Development Department, Johns Hopkins University Applied Physics Laboratory, Laurel, MD

David W. Blodgett is the chief scientist for the Research and Exploratory Development Department at APL. He earned a BS in electrical engineering from Purdue Uni-

versity and an MS and a PhD in materials engineering from Johns Hopkins University. In his role as chief scientist, he provides technical leadership across multidisciplinary programs and groups in the department to identify and promote technology development. In addition, Dave is actively engaged in the development of next-generation optical sensors for operation in challenging environments in support of Defense Advanced Research Projects Agency (DARPA), Intelligence Advanced Research Projects Activity (IARPA), and other Department of Defense (DoD) sponsors. Current research interests include coherent and diffuse optical imaging techniques for the development of noninvasive, high-resolution imaging systems to operate in turbid environments. This research focuses on the development of novel solutions for neural activity imaging, health monitoring, and the detection, localization, and treatment of severe traumatic brain injuries in austere environments. His email address is david.blodgett@jhuapl.edu.

<!-- image -->

Glenn E. Mitzel, Force Projection Sector, Johns Hopkins University Applied Physics Laboratory, Laurel, MD

Glenn E. Mitzel is a chief scientist in the Precision Strike Mission Area in APL's Force Projection Sector. He has a BE, an MS, and a PhD in electrical engineering, all from Johns Hopkins University. Glenn

is a recognized authority in military surveillance, targeting, and upstream data fusion and its applications, and he has strong expertise in optimal estimation and control, remote sensing, and rapid prototyping. In addition, he is a demonstrated leader of large multidisciplinary technical teams attacking and solving complex technical problems in these fields. His email is glenn.mitzel@jhuapl.edu.

<!-- image -->

Morgana M. Trexler, Research and Exploratory Development Department, Johns Hopkins University Applied Physics Laboratory, Laurel, MD

Morgana M. Trexler is a program manager in APL's Research and Exploratory Development Department (REDD). She has a BS in materials science and engineering

from Carnegie Mellon University and an MS and a PhD in materials science and engineering from the Georgia Institute of Technology. She leads a diverse and expanding portfolio of research projects in the Science of Extreme and Multifunctional Materials Program and previously served as the supervisor of REDD's Multifunctional Materials and Nanostructures Group. Morgan is APL's first-ever female master inventor; is a Hopkins Extreme Materials Institute (HEMI) Fellow; serves on the Maryland Science Center's Science Council; and was

a recipient of Georgia Tech's 2015 Council of Outstanding Young Engineering Alumni Award, Maryland Science Center's 2014 Young Engineer Award, APL's 2010 Invention of the Year Award, and Georgia Tech's 2009 Luther Long Memorial Award in Engineering Mechanics. Her email address is morgana. trexler@jhuapl.edu.

<!-- image -->

Kaushik A. Iyer, Space Exploration Sector, Johns Hopkins University Applied Physics Laboratory, Laurel, MD

Kaushik A. Iyer is a materials physicist in APL's Space Exploration Sector. He earned a PhD in materials science and engineering from Vanderbilt University. His contributions span a number of fields, including

hypervelocity impact physics in the context of orbital debris and interplanetary dust impact effects on spacecraft systems, dynamic material failure, fracture mechanics and contact mechanics, and physics-based laser damage modeling. Kaushik and his team developed the Directed Energy Illumination and Visualization (DEIVI) multi-physics software for simulating ablation resulting from high-energy nanosecond- to millisecond-duration laser pulses. He is a fellow of the American Society of Mechanical Engineers (ASME) and a member of IEEE. His email address is kaushik.iyer@jhuapl.edu.

<!-- image -->

William G. Bath, Air and Missile Defense Sector, Johns Hopkins University Applied Physics Laboratory, Laurel, MD

William G. (Jerry) Bath is supervisor of the Distributed Command and Control Branch in APL's Air and Missile Defense Sector. He received a BS, an MS, and a PhD in electrical engineering from Johns

Hopkins University. Jerry's research interests are sensor integration and automation, radar systems tracking, filtering, and statistical estimation. His experience includes development of technical requirements and the algorithmic approach for the Navy's Cooperative Engagement Capability-now deployed on 130+ ships and aircraft; development of a reduced-cost/rapiddeployment solution for Navy interoperability; response to 7th Fleet electromagnetic warfare issues-resulting in a change in fleet concepts of operations; and development of avionics models for foreign anti-ship cruise missiles (to enable analysis of both US Navy hard kill and soft kill). He is working on initiatives in transformational command and control and in accelerating the process for new command and control algorithms to be deployed in fielded systems. He is a fellow of the IEEE. His email address is jerry.bath@jhuapl.edu.

<!-- image -->

Lynn M. Reggia, Air and Missile Defense Sector, Johns Hopkins University Applied Physics Laboratory, Laurel, MD

Lynn M. Reggia is the lead humanmachine engineer and supervisor of the Human-Machine Engineering Group in APL's Air and Missile Defense Sector. She received dual bachelor's degrees in

computer science and piano performance from the University of Maryland, College Park and an MS in human systems engineering from Johns Hopkins University. She has been involved in efforts ranging from electronic warfare projects to future Combat Information Center independent research and development. Lynn's primary interest is in advocating for the end users of the systems and capabilities she works to design. She helped establish, and now leads, a team that provides technical leadership and strategic direction in these competencies. Her email address is lynn.reggia@jhuapl.edu.

<!-- image -->

David B. Helmer, Air and Missile Defense Sector, Johns Hopkins University Applied Physics Laboratory, Laurel, MD

David B. Helmer is a project manager and assistant supervisor of the HumanMachine Engineering Group in APL's Air and Missile Defense Sector. He has a BS in mechanical engineering from Johns Hop-

kins University and an MS and a PhD in mechanical engineering from Stanford University. David is an experienced experimentalist and analyst with a technical background in heat transfer and fluid mechanics and has worked on a wide variety of programs and technical areas at APL, ranging from additive manufacturing to artificial intelligence and robotic and autonomous systems. He previously served as the program manager for the emerging technologies portfolio in APL's National Security Analysis Department. He is a part-time professor teaching advanced experimental methods in the Department of Civil and Mechanical Engineering at the United States Military Academy (USMA), where he also advises on capstone design and independent study courses in addition to serving more broadly as a resource to cadets. His email address is david. helmer@jhuapl.edu.

<!-- image -->

Ashutosh Dutta, Asymmetric Operations Sector, Johns Hopkins University Applied Physics Laboratory, Laurel, MD

Ashutosh Dutta is currently the chief 5G strategist in APL's Asymmetric Operations Sector. He earned a BS in electrical engineering from the National Institute of Technology Rourkela, an MS in computer

science from the New Jersey Institute of Technology (NJIT), and a PhD in electrical engineering from Columbia University. As a technical leader in 5G and security, Ashutosh is the founding co-chair for the IEEE Future Networks Initiative, which focuses on 5G standardization, education, publications, test bed, and roadmap activities; the founding co-chair for the premier IEEE 5G World Forums; and the chair for IEEE Industry Connection's O-RAN activities and IPv6. He has authored more than 100 technical papers, co-authored the book Mobility Protocols and Handover Optimization: Design, Evaluation and Application , and has 31 issued patents. His contributions to education include serving as chair of the Johns Hopkins Engineering for Professionals Electrical and Computer Engineering program and as director of the Whiting School's doctor of engineering program, co-founding the IEEE Integrated STEM Education Conference (ISEC) and serving as its general co-chair for the last 10 years, and helping to implement Engineering Projects in Community

Service (EPICS) in several high schools. He received the 2009 IEEE MGA Leadership Award, the 2010 IEEE Professional Leadership Award, the 2022 IEEE George F. McClure Citation of Honor, and the 2022 IEEE North American Region Exceptional Service Award. Ashutosh is a fellow of IEEE and has held many roles in the organization, and he is a distinguished member ACM. His email address is ashutosh.dutta@jhuapl.edu.

<!-- image -->

Nancy F. Andersen, Asymmetric Operations Sector, Johns Hopkins University Applied Physics Laboratory, Laurel, MD

Nancy F. Andersen is the assistant program manager supporting the Warfighter Health Research and Military Healthcare Systems programs within APL's National Health Mission Area. She earned a BS in

aerospace engineering from the University of Cincinnati and an MS in aerospace engineering from the University of Maryland. At APL, Nancy has supported many sponsor domains with her expertise in systems engineering and project management, including efforts focused on military readiness and resilience, supply chain illumination and vulnerability analysis, remote video surveillance systems, and integrated systems architectures. Outside of APL, her career has included various technical and leadership positions at Lockheed Martin Space, where she supported the Navy's nuclear weapons security, Fleet ballistic missile D5 life extension, reentry systems engineering, defensive missile systems multiple kill vehicle, and wind tunnel testing. Nancy is an American Institute of Aeronautics and Astronautics (AIAA) fellow and has been actively involved with AIAA for over 30 years. Her email address is nancy. andersen@jhuapl.edu.

<!-- image -->

Jerry A. Krill, Assistant Director for Science and Technology and Chief Technology Officer, Johns Hopkins University Applied Physics Laboratory, Laurel, MD

Jerry A. Krill is APL's assistant director for science and technology and chief technology officer. He earned bachelor's and master's degrees from Michigan State Univer-

sity and a PhD from the University of Maryland, all in electrical engineering. Previously he was APL's assistant director for programs, head of the Power Projection Systems Department, and executive for air defense programs. He was a co-conceiver and APL's systems engineer for the Cooperative Engagement Capability, meeting its accelerated, congressionally directed fleet introduction in 1996. He was APL's systems engineer for the Mountain Top advanced concept technology demonstration leading to today's Naval Integrated Fire Control - Counter Air capability. He led the Navy/Ballistic Missile Defense Organization Concept Formulation Working Group in a study of the Navy's role in ballistic missile defense. He holds 22 patents; has authored over 100 papers and documents, including coauthoring the book Infusing Innovation into Organizations and co-leading the Naval Studies Board study entitled Responding to Capability Surprise: A Strategy for U.S. Naval Forces ; and serves on the Whiting School of Engineering's advisory board. He was inducted into the University of Maryland Clark School Innovation Hall of Fame. His email address is jerry.krill@jhuapl.edu.

Among APL's thousands of critical contributions to national security and space exploration are a number of defining innovations: game-changing breakthroughs in technology that have created inflection points in history. These revolutionary advances have ignited new engineering accomplishments globally, saved lives, and secured the United States against threats at home and abroad.

At its 75th anniversary, APL named its first nine defining innovations:

- 1. Radio Proximity Fuze: APL's First Game-Changing Technology
- 2. APL: The Birthplace of U.S. Navy Surface-to-Air Missiles
- 3. Transit: The World's First Satellite-Based Global Navigation System
- 4. AMFAR: Pathway to Phased Array Radar
- 5. Exploiting Undersea Physics: Enabling Advanced Sonar Arrays
- 6. SATRACK: Transforming Ballistic Missile Testing
- 7. Tomahawk: The World's First Long-Range, Autonomous, Precision-Guided Weapon
- 8. Cooperative Engagement Capability: Networking Fleet Air Defenses
- 9. Discovery: Pioneering Low-Cost Planetary Exploration On the occasion of its 80th anniversary, APL named two new defining innovations, its 10th and 11th. They

APL Identifies Two New Defining Innovations

## APL Identifies Two New Defining Innovations

<!-- image -->

APL Staff Writers

are described briefly below. Read about all of APL's defining innovations and download the posters at https://www.jhuapl.edu/about/defining-innovations.

## BALLISTIC MISSILE DEFENSE FROM THE SEA

APL responded to the critical challenge of proliferating ballistic missile threats, leading the development of the transformational system needed to demonstrate Ballistic Missile Defense (BMD) from the sea. The resulting experiments proved that BMD technology could be integrated with a Navy weapon system to "hit a bullet with a bullet" in space from the sea. APL's critical contributions opened the door for the Navy's central role in BMD. The resulting impact is felt far beyond our nation's shores as BMD now provides enduring defense at sea and ashore across the globe.

## PLANETARY DEFENSE

For more than a decade, APL engineers and scientists developed game-changing concepts and technologies to prove that it was possible to defend our planet from an asteroid on a potentially catastrophic Earth-impact trajectory. APL established the technological basis for planetary defense; solidified the domain as a research and development area at the federal level; played key roles in defining and exercising interagency and international coordination responsibilities; and captured worldwide attention by successfully completing the Double Asteroid Redirection Test (DART) mission, the first in-space demonstration of planetary defense technology.

<!-- image -->

## PLANETARY DEFENSE

Close-up image from a poster in the defining innovations series. Visit the APL website to view or download the full poster. https://www.jhuapl.edu/about/ defining-innovations

## BALLISTIC MISSILE DEFENSE FROM THE SEA

Close-up image from a poster in the defining innovations series. Visit the APL website to view or download the full poster. https://www.jhuapl.edu/about/ defining-innovations

<!-- image -->

The Lab's Top Inventions, Discoveries, and Accomplishments in 2022

## APL Achievement Awards and Prizes: The Lab's Top Inventions, Discoveries, and Accomplishments in 2022

<!-- image -->

APL Staff Writers

## ABSTRACT

For 80 years, APL's dedicated staff members have made thousands of critical contributions to critical challenges in trusted service to the nation. They have delivered game-changing solutions in diverse areas-undersea warfare, space exploration, missile defense, cybersecurity, artificial intelligence and autonomy, biology and bionengineering, and the environment to name just a few. The incredible dedication and achievements of the Lab's staff are enabled by outstanding enterprise services; a deep-rooted culture of innovation; a commitment to diversity, equity, and inclusion; and an emphasis on the mission. Every year the Lab honors these accomplishments with an awards program. This article details the awards presented for achievements during 2022, APL's 80th year.

## INTRODUCTION

On April 25, 2023, APL honored nearly 200 staff members for their exceptional contributions in 2022, the Lab's 80th year, during its annual Achievement Awards ceremony. For awards honoring outstanding publications and notable projects, individuals, and teams throughout the Lab, 753 staff members were named in 144 nominated entries in 25 categories. Ultimately, 168 staff members were recognized for 31 winning entries. The virtual ceremony celebrated staff members' outstanding work in areas such as publications, Independent Research and Development (IRAD) projects, internally funded innovation initiatives, inventions, mission and enterprise accomplishments, and more.

This article details the winning staff members and their achievements. Because the awards program is open to only current APL staff members, only APL contributors are named. These projects and accomplishments

exemplify what APL staff members have been doing for 80 years: making critical contributions to the nation's most critical challenges.

## PUBLICATION AWARDS

The publication awards, first presented in 1986, are the genesis of APL's annual Achievement Awards program. Administered by the Johns Hopkins APL Technical Digest editorial board, these awards encourage and honor scholarship through publication in the professional literature. Departments and sectors may submit up to two nominations in each of the eight award categories. Judges consider the nominated works' significance and clarity, giving considerably greater weight to the significance of the work in advancing science, engineering, or A PL's m i s sio n.

<!-- image -->

<!-- image -->

## Author's First Paper in a Peer-Reviewed Journal or Proceedings

The award for an author's first paper published in a journal or proceedings in 2022 went to Vivian Maloney for "Qubit Control Noise Spectroscopy with Optimal Suppression of Dephasing," published in Physical Review A .$^{1}$ This paper introduces a protocol to characterize amplitude noise, which causes faulty gates. Understanding noise that causes errors in quantum devices is essential to the ability to build better quantum computers. The protocol is robust to competing sources of error, allowing amplitude noise to be characterized in regimes where it was previously impossible.

## Walter G. Berl Award - Outstanding Paper in the Johns Hopkins APL Technical Digest

This award recognizes excellence in APL's own technical journal, which has been published since 1961. The honor is named for Walter Berl, who was editor-in-chief of the Digest when the publication awards program was created and who oversaw the program for many years.

The 2022 award went to Krithika Balakrishnan, Eyal Bar-Kochba, and Alexander Iwaskiw for "Identifying Patterns and Relationships Within Noisy Acoustic Data Sets."$^{2}$ This paper is part of an issue highlighting work from staff members in the Lab's Discovery Program, a 2-year rotational opportunity that allows new college graduates a unique opportunity to experience APL's wide array of technical challenges.$^{3}$ It describes a novel methodology for understanding biomechanical fracture and characterizing acoustic signatures with

distinct failure modes, leveraging a creative fusion of existing individual tools for analysis. This methodology is aiding our understanding of human injury, enabling more efficient evaluation of trauma effects and, ultimately, better protection.

## Outstanding Research Paper in an Externally Refereed Publication

Two awards were presented for outstanding research papers published in externally refereed publications in 2022. The first went to Plamen Demirev, James Johnson, Jesse Ko, Nam Le, Collin McDermott, Danielle Nachman, and Zhiyong Xia for "Destruction of Per/Poly-fluorinated Alkyl Substances by Magnetite Nanoparticle-Catalyzed UV-Fenton Reaction," published in Environmental Science: Water Research & Technology .$^{4}$ This team developed an eco-friendly, nontoxic, cost-effective, and reusable technology to destroy per-and poly-fluorinated alkyl substances (PFAS) in drinking water. The technology, which is scalable to industrial applications, reduces these "forever chemicals" in drinking water by more than 90%.

<!-- image -->

The second award went to Stefan Allen, Ra'id Awadallah, Brian Gibbons, and Andrew Goers for "Natural-Modes Expansion of Microwave Fields Emitted by Ultra-Short Pulse Laser Illumination of a Conduct-

ing Wire," published in IEEE Transactions on Electromagnetic Compatibility .$^{5}$ This paper describes a rigorous theoretical model corroborated by experimental verification of radio frequency (RF) emissions due to ultrashort pulse laser illumination of metallic targets. It presents definitive evidence that a major contribution to RF emissions is transient current, which flows to neutralize the charge induced on the target by laser ablation.

## Outstanding Development Paper in an Externally Refereed Publication

Two awards were also presented for outstanding development papers published in externally refereed publications in 2022. The first, again recognizing work on PFAS, went to James Johnson, Jesse Ko, Nam Le, Danielle Nachman, K. Michael Salerno, and Zhiyong Xia for "Removing Forever Chemicals via Amphiphilic Functionalized Membranes," published in npj Clean Water .$^{6}$ This paper presents evidence that APL-synthesized novel materials capture PFAS from water more efficiently than currently available filters. Computer simulations successfully predict the capture properties of these novel materials. The developed theoretical and experimental methods can be expanded to synthesis of new materials for efficient water clean-up from other toxic chemicals.

The second award was presented to Andrew Badger, Matthew Fifer, David

Handelman, Luke Osborn, Francesco Tenore, Brock Wester, and Jared Wormley for "Shared Control of Bimanual Robotic Limbs with a Brain-Machine Interface for Self-Feeding," published in Frontiers in Neurorobotics .$^{7}$

## Publication: Outstanding Research Paper in an Externally Refereed Publication

'Natural-Modes Expansion of Microwave Fields Emitted by Ultra-Short Pulse Laser Ilumination of a Conducting Wire

Stefan R. Allen

<!-- image -->

Ra'id S Awadallah

Brian B Gibbons

Andrew J. Goers

## Publication: Outstanding Development Paper in an Externally Refereed Publication

"Removing Forever Chemicals via Amphiphilic Functionalized Membranes"

<!-- image -->

<!-- image -->

Jesse $. Ko

Nam Q. Le

Danielle R. Nachman

K Michael Salerno

<!-- image -->

Zhiyong Xia

<!-- image -->

"Shared Control of Bimanual Robotic Limbs with a Brain-Machine Interface for Self-Feeding

Publication: Outstanding Development Paper in an Externally Refereed Publication 80

Andrew R. Badger

<!-- image -->

Matthew $. Fifer

David A. Handelman

Luke E. OsbornFrancesco V. Tenore

<!-- image -->

Brock A Wester

<!-- image -->

Jared M. Wormley

<!-- image -->

<!-- image -->

<!-- image -->

<!-- image -->

<!-- image -->

<!-- image -->

<!-- image -->

<!-- image -->

James K. Johnson

<!-- image -->

<!-- image -->

<!-- image -->

These researchers demonstrated for the first time that an intelligent shared control strategy can enable a human with brain implants to manipulate bimanual robotic limbs to cut and eat food. This work opens new possibilities for restoring quality of life and enhancing human function through novel human-machine teaming.

## Outstanding Professional Book

The award for outstanding professional book published in 2022 went to Rick Chapman for Remote Sensing Physics: An Introduction to Observing Earth from Space , co-published by the American Geophysical Union and John Wiley & Sons.$^{8}$ This advanced textbook examines the physical principles underlying remote observations of Earth using passive and active electromagnetic sensors in the visible, infrared, and microwave bands.

## Outstanding Special Publication

Nour Raouafi was presented the Outstanding Special Publication Award for "A Journey to Touch the Sun," published in Physics Tod ay .$^{9}$ This Physics Tod ay cover article describes the Parker Solar Probe, which is braving extreme conditions to explore the mysterious solar corona, a region that harbors some of the most difficult-to-understand phenomena in astrophysics.

## Outstanding Conference Publication

The Outstanding Conference Publication Award recognizes the value of participating in conferences

<!-- image -->

<!-- image -->

to meet colleagues and establish professional contacts. The award for 2022 went to Kimberly Ord for "Parker Solar Probe Pre-Launch Mission Operations Orbit-in-the-Life Mission Simulation," published in the SpaceOps 2021 post-conference book Space Operations: Beyond Boundaries to Human Endeavours .$^{10}$ Kimberly, the Parker Solar Probe deputy mission operations manager, led the prelaunch development and execution of the mission operations "orbit-in-the-life" and early operations mission simulations performed using the spacecraft during thermal vacuum testing. This paper describes the challenges, lessons learned, and anomalies encountered.

## Lifetime Achievement Publication Award

Lifetime Achievement winners are not selected every year. In fact, only six have been named over the past decade. This award honors an author's career of achievement through a substantial body of publications that are significant in terms of peer recognition, prizes, citation frequency, or influence on the innovation ecosystem. In 2022, Andy Cheng from APL's Space Exploration Sector was presented the Lifetime Achievement Publication Award for his historic publications advancing space science from the Voyager missions to, most recently, the Double Asteroid Redirection Test (DART) mission. Andy published his first scientific paper in 1974 as a graduate student and has since added over 200 more to his curriculum vitae.

<!-- image -->

## R. W. HART PRIZES FOR EXCELLENCE IN INDEPENDENT RESEARCH AND DEVELOPMENT

The R. W. Hart Prizes for Excellence in Independent Research and Development (IRAD)-first presented in 1989 and named for former APL assistant director for research and exploratory development Robert W. Hart-recognize significant contributions that advance science and technology through IRAD. Sectors and departments recommend candidates, and the Management Forum judges the nominations on their quality and importance to APL. Prizes are awarded in two categories: best research project and best development project.

## Best Research Project

The award for the best IRAD research project in 2022 went to principal participants Plamen Demirev, Claresta Joe-Wong, James Johnson, Phillip Johnson, Jesse Ko, Nam Le, Danielle Nachman, K. Michael Salerno, Luke Skala, and Zhiyong Xia for Water and Beyond.

## Best Development Project

The award for the best 2022 IRAD development project was presented to Jessie Barrick, Robert Bruce, Joseph Centurelli, Nora Lane, Joseph Miragliotta, Lance Oh, David Shrekenhamer, Juliana Vievering, Angelos Vourlidas, and Chad Weiler for Multifunctional Metasurface Optics.

<!-- image -->

<!-- image -->

<!-- image -->

## INVENTION AWARDS

## Government Purpose Invention Award

The first Government Purpose Innovation Award, recognizing an invention that meets a critical sponsor need, was presented in 2011. Selected by a team of technical leaders from across the Lab who are acquainted with APL's technology transfer practices, finalist inventions are judged on their novelty and potential impact to the sponsor community.

The award for innovation in 2022 went to Jonathan Cohen for Method for Tracking Provenance of Information.

## Invention of the Year Award

The Invention of the Year Award was first presented in 2000 to encourage new technology and innovation at APL. To identify the top technology from the preceding year, an independent review panel judges invention disclosures. The judges, including technical and business consultants, technology transfer professionals, and intellectual property attorneys, assess inventions' creativity, novelty, improvement to existing technology, commercial potential, and probable benefit to society.

The winner of the Invention of the Year Award for 2022 is Will Coon for System to Augment Restorative Sleep.

<!-- image -->

<!-- image -->

## Master Inventor Award

Lab management first presented the Master Inventor Award in 2007 to honor those staff members who have demonstrated a career of innovation with 10 or more patents based on APL intellectual property. To date, only 33 staff members have attained the honor. In 2022, the Lab was incredibly proud to add Joseph Miragliotta$^{11}$ to the list of APL Master Inventors.

## AWARDS FOR INNOVATION

To position the Lab to respond to increasingly complex national challenges and to capitalize on rapid technological advances, APL's leaders have introduced several initiatives to encourage innovation across the Lab.$^{12}$ One of these initiatives, Project Catalyst, offers staff members three funding opportunities for bold, high-risk, transformational ideas that will ensure our nation's preeminence in the 21st century. Staff members submit ideas in response to challenges posted during several cycles throughout the year. Peers vote on the submissions, and finalists receive funding to develop their ideas. Awards recognize excellent work that is part of these initiatives.

## Ignition Grant Prize

The inaugural Project Catalyst award, the Ignition Grant Prize, was presented for the first time in 2013 for

the project judged to be most creative and to have the greatest potential impact.

The 2022 award went to Meera Kesavan, Joel Sarapas, and Scott Shuler for ICICLE: Ice Crystallization Inhibitor Coatings for Low-temperature Environments.

## Combustion Grant Prize

The Combustion Grant Prize, first presented in 2017, recognizes high-risk, high-impact technical ideas.

Ryan Carter, Gehn Ferguson, Mark Graybeal, Alexander Lark, and Steven Szczesniak were recognized for their 2022 work on Thermal Management for Additive Hypersonic Leading Edges.

## Propulsion Grant Year 3 Prize

And, finally, presented for the first time in 2018, the Propulsion Grant Prize honors ideas that were selected for their third year of funding. Three teams earned this prize in 2022.

Greyson Brothers, Noah Ford, Naveed Haghani, Thomas Urban, and John Winder earned a third year of funding for Beyond Human Reasoning - Bridging the Information Gap.

The second team selected for a third year of funding includes Ra'id Awadallah, Sean Ellison, Chester Hewitt, Francesca McFadden, and Jordan Wiker for Early Warning Network.

<!-- image -->

Propulsion Grant Prize for Innovation 8 Beyond Human Reasoning Bridging the Information Gap

<!-- image -->

<!-- image -->

<!-- image -->

<!-- image -->

Greyson Brothers

Noah P Ford

Naveed E Haghani

Thomas J Urban

John J. Winder

Propulsion Grant Prize for Innovation 80 Early Warning Network

<!-- image -->

<!-- image -->

<!-- image -->

Ra'id $. Awadallah

<!-- image -->

Sean M. Ellison

Chester H. Hewitt

Francesca R McFadden

Jordan R. Wiker

<!-- image -->

Janna Domenico, Megan Hannegan, Nam Le, Carlos Martino, Ryan McQuillen, and K. Michael Salerno were awarded another year of funding for their project Novel Optimal Biomagnetic Sensor.

## AWARDS FOR OUTSTANDING ACCOMPLISHMENTS

## Mission Accomplishment Awards

The Outstanding Mission Accomplishment Awards, first presented in 2014, recognize major achievements in mission-oriented programs and projects. Awards are given in two categories: a current challenge and an emerging challenge. For both types, a review team of top

managers and executives from APL's sectors and mission areas solicits nominations for technical accomplishments in sponsored programs during the previous year. A program has to have achieved a significant milestone within the previous fiscal year to be eligible. The panel judges entries on technical excellence and potential impact.

## For a Current Challenge

Awards were presented for two 2022 accomplishments. The first went to core team members Elena Adams, Nancy Chabot, Michelle Chen, Andy Cheng, Zachary Fletcher, Jeremy John, Daniel O'Shaughnessy, Edward Reynolds, Andy Rivkin, and Evan Smith for DART,$^{13}$ the first-ever mission to demonstrate asteroid deflection by a kinetic impactor.

<!-- image -->

<!-- image -->

The second award was presented to core team members Charles Goldblum, Christopher Griffin, Christopher James, N. Jordan Jameson, Patrick Lee, Maureen O'Connor, Bradley Potteiger, David Sames, and Jacklyn Truong for creating an unprecedented capability for the Department of Defense.

## For an Emerging Challenge

The award for the 2020 mission accomplishment for an emerging challenge went to principal contributors Rui Chen, David James, Marina Johnson, Adaleena Mookerjee, Brandon Patterson, Eric Ross, Cory Sheffer, Michael Thompson, Craig Williams, and Robert Zaborowski for completing a comprehensive program of at-sea testing and analysis for an advanced Navy sensor.

## Enterprise Accomplishment Award

The Enterprise Accomplishment Award, first presented in 2015, recognizes the enterprise accomplishment with the greatest impact on APL's operations and culture of innovation. Winners are selected by a joint panel of APL's operations executives and managing executives. Two teams were honored for their work in 2022.

The first award recognized DART impact media and guest events, with the team led by Mike Buckley, Brooke Hammack, Lee Lachman, Tricia Latham, John O'Brien, Duane Pickett, Steven Smith, Justyna Surowiec, Shannon Thornton, and Jessica Tozer for coordinating the DART media outreach campaign and guest event that allowed a global audience to witness the world's first planetary defense test mission.

<!-- image -->

<!-- image -->

The second award recognized hiring in a challenging recruiting environment, with the team led by Joseph Ames, Eliza Bell-Andrews, Jenny Danick, Bryant Garcia, Carrie Gingras, Denise Hockensmith, and Camille Stauffer for hiring talent for APL in a challenging and unprecedented recruiting environment.

## The Alvin R. Eaton Award

The Alvin R. Eaton, or ARE, Award has been presented annually since 2001 but was not presented publicly during the awards ceremony until 2016. It honors staff members who have spent much of their careers leading remarkable achievements that we cannot talk about openly. Awardees are selected by APL's director and assistant director for programs.

Eric Adles was honored with this award for leading precision navigation and timing (PNT) radio frequency photonics and optical communications projects.

<!-- image -->

## Director's Award for Special Achievements

Sometimes a major accomplishment is outside the usual award categories. The Director's Award for Special Achievements recognizes such accomplishments. This award was first presented in 2017. Two awards were presented for special achievements in 2022.

The first award went to team members Charles Anderson, John Atchison, Sarah Bergman, Carolyn Eady, Tri Freed, Thomas Johnson, Brennan Movius, J. Greg Near, Jerry Richard, and Ed Russell for providing systems engineering expertise in direct support of government space capabilities.

The second award went to principal participants Timothy Allensworth, Michael Dennis, John Mack, Michael Purcell Lee Rogers, James Sari, Elad Siman-Tov, Clara Smart, Benjamin Turek, and Chad Weiler for

developing a novel sensing approach to protect critical infrastructure.

## THE "BOLDIES"

In early 2018, Lab management asked a team of technical leaders and contributors for recommendations on increasing APL's boldness. This group, Team Bold, proposed instituting two formal awards to celebrate boldness.

## Bumblebee Award

The first award, the Bumblebee Award, recognizes improbable designs that had remarkable results, much like APL's historic Bumblebee program, whose name

<!-- image -->

<!-- image -->

was inspired by a quote attributed to aviation pioneer Igor Sikorsky: "According to recognized aerotechnical tests the bumblebee cannot fly because of the shape and weight of his body in relation to the total wing areas. BUT, the bumblebee doesn't know this, so he goes ahead and flies anyway."

The Bumblebee Award recognizing 2022 achievements was presented to Chace Ashcraft, Jay Brett, David Chung, Marisa Hughes, Anshu Saksena, Jennifer Sleeman, Caroline Tang, and Larry White for developing the Physics-informed AI Climate Model Agent Neuro-symbolic Simulator (PACMANS) for Tipping Point Discovery,$^{14}$ a hybrid AI climate modeling approach that enables the discovery of tipping points that would have catastrophic effects on our planet.

## Noble Prize

The second award in this category, the Noble Prize, celebrates work that was not fully successful but yielded valuable lessons. Its name is a play on Nobel Prize and noble failure.

The Noble Prize for 2022 was awarded to Sarah Brewer, Megan Hannegan, Raymond Lennon, Anna Munro, and William Stone for MAINER: Manipulating Atmospheric Ice Nucleation Events, Redux, which targets the development of novel bio-derived cloud seeding applications.

## LIGHT THE FUSE AWARD

The Light the FUSE Award was first presented during the 2021 ceremony. The award name is a play on the acronym FUSE, referring to APL's FUSE employee resource group, which created this award, as well as the Lab's general innovation theme. FUSE, which stands for Fostering Unity and Staff Empowerment, is a consolidation of representatives from APL's affinity groups, sectors, and departments who are focused on enhancing the Lab's work environment and culture of innovation. This award recognizes significant contributions that promote a positive, diverse, and inclusive culture at the Laboratory, increasing APL's potential for innovation.

<!-- image -->

<!-- image -->

The 2022 award went to Jennifer Benzing, Stephanie Berry, Gill Brown, Megan Leahy-Hoppa, Molly Nichols, and Felipe Westhelle for establishing their sector's Diversity and Inclusion Ambassadors program.

## APL ANALYTICAL ACHIEVEMENT AWARD

The newest honor is the Analytical Achievement Award, which recognizes the most insightful analytic work that resulted in a critical contribution to a government decision-maker or program. It was first presented during the 2022 ceremony.

The Analytical Achievement Award was presented to core team members Timothy Allensworth, Toni Matheny, Robert Miceli, Jeffrey Miers, Fazle

Siddique, and Christopher Watkins for developing an analysis-based game executed for senior leadership from multiple US government organizations.

## CONCLUSION

APL staff members have an 80-year legacy of making critical contributions in pursuit of solutions to the nation's most critical challenges. The Lab's annual Achievement Awards, which have been presented for almost 40 years of APL's storied history, recognize many of these contributions. For a brief history of APL's awards program, refer to the article by Richardson and Livieratos in the issue commemorating APL's 75th anniversary.$^{15}$ This same issue includes a complete list of

<!-- image -->

winners through 2017 (for 2016 achievements).$^{16}$ Summaries of the winners for achievements in subsequent years are also available in the Digest .

## REFERENCES

- $^{ 1}$V. Maloney, Y. Oda, G. Quiroz, B. D. Clader, and L. M. Norris, "Qubit control noise spectroscopy with optimal suppression of dephasing," Phys. Rev. A , vol. 106, no. 2, art. 022425, 2022, https:doi.org/10.1103/ PhysRevA.106.022425.
- $^{ 2}$K. Balakrishnan, E. Bar-Kochba and A. S. Iwaskiw, "Identifying patterns and relationships within noisy acoustic data sets," Johns Hopkins APL Tech. Dig. , vol. 36, no. 3, pp. 259-269, 2022, https://www.jhuapl. edu/Content/techdigest/pdf/V36-N03/36-03-Balakrishnan.pdf.
- $^{ 3}$APL, "Discovery Program," YouTube, Jan. 17, 2020, https://youtu.be/ eRQYe741VHg.
- $^{ 4}$D. R. Schlesinger, C. McDermott, N. Q. Le, J. S. Ko, J. K. Johnson, P. A. Demirev, and Z. Xia, "Destruction of per/poly-fluorinated alkyl substances by magnetite nanoparticle-catalyzed UV-Fenton reaction," Environ. Sci. Water Res. Technol. , vol. 8, pp. 2732-2743, 2022, https://doi.org/10.1039/D2EW00058J.
- $^{ 5}$R. S. Awadallah, B. B. Gibbons, A. A. Vartanyan, R. Thapa, S. R. Allen, and A. J. Goers, "Natural-modes expansion of microwave fields emitted by ultra-short pulse laser illumination of a conducting wire," IEEE Trans. Electromagn. Compat. , vol. 64, no. 6, pp. 1958-1968, 2022, https://doi.org/10.1109/TEMC.2022.3193911.
- $^{ 6}$J. K. Johnson, K. M. Salerno, D. R. Schlesinger, N. Q. Le, J. S. Ko, and Z. Xia, "Removing forever chemicals via amphiphilic functionalized membranes," npj Clean Water , vol. 5, art. 55, 2022, https://doi. org/10.1038/s41545-022-00193-y.
- $^{ 7}$D. A. Handelman, L. E. Osborn, T. M. Thomas, A. R. Badger, M. Thompson, et al., "Shared control of bimanual robotic limbs with a brain-machine interface for self-feeding," Front. Neurorobot. , vol. 16, art. 918001, 2022, https://doi.org/10.3389/fnbot.2022.918001.

- $^{ 8}$R. Chapman and R. Gasparovic, Remote Sensing Physics: An Introduction to Observing Earth from Space , Hoboken, NJ: American Geophysical Union and John Wiley & Sons, 2022.
- $^{ 9}$N. E. Raouafi, "A journey to touch the sun," Phys. Today , vol. 75, no. 11, pp. 28-34, 2022, https://doi.org/10.1063/PT.3.5120.
- $^{10}$K. J. Ord, "Parker Solar Probe pre-launch mission operations orbitin-the-life mission simulation," in Space Operations , C. Cruzen, M. Schmidhuber, and Y. H. Lee, Eds. Springer Aerospace Technology Series. Cham: Springer, 2022, pp. 57-87, https://doi.org/10.1007/9783-030-94628-9\_3.
- $^{11}$A. Mantiply, "Master Inventor Miragliotta taps into the power of teamwork," news release, APL, Laurel, MD, May 11, 2023, https:// www.jhuapl.edu/news/news-releases/230511-master-inventor-josephmiragliotta.
- $^{12}$A. E. Kedia and J. A. Krill, "Inspiring innovation and creativity at APL," Johns Hopkins APL Tech. Dig. , vol. 35, no. 4, pp. 363-379, 2021, https://www.jhuapl.edu/Content/techdigest/pdf/V35-N04/35-04 -Kedia.pdf.
- $^{13}$"Bullseye! NASA's DART mission impacts asteroid target in worl d fir st," news release, APL, Laurel, MD, Sep. 26, 2022, https://www. jhuapl.edu/news/news-releases/220926-nasa-dart-mission-strikesasteroid-target.
- $^{14}$"Johns Hopkins scientists Leverage AI to discover climate 'tipping points,'" news release, APL, Laurel, MD, Mar. 31, 2023, https://www. jhuapl.edu/news/news-releases/230331-johns-hopkins-scientistsleverage-ai-to-discover-climate-tipping-points.
- $^{15}$E. M. Richardson and K. K. Livieratos, "APL achievement awards and prizes," Johns Hopkins APL Tech. Dig. , vol. 34, no. 2, pp. 306-325, 2018, https://www.jhuapl.edu/Content/techdigest/pdf/V34-N02/34-02 -Richardson.pdf
- $^{16}$"APL achievement awards and prizes: Complete history of winners through 2017," Johns Hopkins APL Tech. Dig., vol. 34, no. 2, pp. S1S16 (online only), 2018, https://www.jhuapl.edu/Content/techdigest/ pdf/V34-N02/34-02-CompleteAwards.pdf.

<!-- image -->

<!-- image -->

<!-- image -->

<!-- image -->

<!-- image -->

<!-- image -->

5

8

9

11

<!-- image -->

<!-- image -->

Y

YEARS

- 1. Army Private First Class Harold Pukl, 36th Division, U.S. 7th Army, puts a proximity fuze on a 155-mm shell in France on Apr. 6, 1945 (Signal Corps photo). The fuze, developed and perfected by APL, changed the course of World War II and has been judged by historians as one of the three most important technology developments of the war, along with radar and the atomic bomb.
- 2. A Terrier missile roars off the aft launcher of USS Mississippi (BB 41) in 1953. APL's pioneering research to develop the first generation of Navy surface-to-air missiles laid the foundation for technologies and systems that continue to defend the fleet today and provide the backbone of US air and missile defense.
- 3. Illustration of the APL-developed Transit , the world's first satellite-based global navigation system serving the Navy's ballistic missile submarine force. The forerunner of modern GPS, Transit provided essential capability to the US Navy from 1964 until the 1990s.
- 4. A view of the Advanced Multifunction Array Radar (AMFAR) prototype with panels removed. APL designed, built, and demonstrated the Navy's prototype phased array radar to defend against multiple simultaneous aircraft and missile attacks. The prototype served as the foundation for the SPY-1 series.
- 5. Brooke Clayton working in APL's towed sonar array fabrication facility. APL developed prototypes, experiments, and ocean physics and engineering models that unlocked the potential of towed sonar arrays, enabling long-range towed arrays that revolutionized anti-submarine warfare and guided stealth designs for multiple generations of US submarines.
- 6. A Trident II ballistic missile is launched from the USS West Virginia (SSBN-736) during a 2014 missile test. APL developed the transformational instrumentation system that confidently estimates missile accuracy anywhere in the world. SATRACK has saved the Navy billions of dollars in flight test costs and remains essential to US nuclear deterrence strategy.
- 7. A Tomahawk Land Attack Missile (TLAM) is launched from USS Cape St. George in 2003 (US Navy photo). APL developed the guidance and control technology for the Tomahawk, making it the world's first long-range, precision-guided weapon and enabling it to travel hundreds of miles over varied terrain and strike heavily defended targets with great accuracy.
- 8. Illustration of the Cooperative Engagement Capability (CEC) operating at sea. Led by APL for the Navy, CEC provided the first networked air defense for US Navy ships and airborne early warning aircraft, enabling ships to engage aircraft and missiles not even seen by their own radars by using composite radar tracks created from the radars of the ships within the battle group.
- 9. Illustration of NASA's NEAR spacecraft. APL's revolutionary approach to low-cost planetary exploration , demonstrated by the NEAR mission to the asteroid Eros, inspired NASA's Discovery and New Frontiers programs and led to the highly successful MESSENGER mission to Mercury and New Horizons mission to Pluto.
- 10. A Standard Missile-3 Block 1B interceptor launches from USS Lake Erie during a 2013 test (Missile Defense Agency photo). APL led development of the transformational system needed to demonstrate Ballistic Missile Defense (BMD) from the Sea , proving that BMD technology could be integrated with a Navy weapon system to "hit a bullet with a bullet" in space from the sea. BMD now provides enduring defenses at sea and ashore across the globe.
- 11. Illustration of NASA's DART spacecraft prior to impact at the Didymos binary system. APL established the technological basis for planetary defense ; solidified the domain as a research and development area; played key roles in defining and exercising coordination responsibilities; and successfully completed the DART mission-the first in-space demonstration of planetary defense technology.

www. j huapl . edu/techdi gest