# Awesome-Cloud-Detection-n-Response

## Top Cloud Detection & Response (CDR) Platforms Ecosystem



**Curated List of SaaS Products & Open-Source GitHub Projects**

*Focused on Cloud Control-Plane Detection, Runtime Threat Detection, Identity Threat Detection & Automated Response*

**Last updated: September 2026**



This repository tracks notable **SaaS platforms** and **open-source projects** for **Cloud Detection & Response (CDR)**. These tools help security teams detect active threats inside cloud environments—monitoring the control plane (API calls), runtime (workload and container behavior), and cloud identity (credential misuse, privilege escalation) in real time and responding before adversaries can exfiltrate data.



**Examples** include Wiz (Gem Security), Sysdig, CrowdStrike Falcon Cloud Security, Palo Alto Networks (Prisma Cloud/Cortex), Microsoft Defender for Cloud, Orca Security, and Uptycs (the category leaders).



**Open-source emphasis**: This section is heavily expanded with every major active project for self-hosting, custom detection rules, and transparent cloud telemetry. The standout is **Falco**—the CNCF-graduated runtime threat detection engine that forms the foundation of Sysdig's commercial CDR offering. **Kubescape's node-agent** provides eBPF-based runtime detection with CEL rules and malware scanning. **Argus** delivers open-source AWS/Azure cloud forensics with MITRE ATT&CK correlation. **Tetragon** brings eBPF-native enforcement with in-kernel policy application. This section documents these production-grade solutions honestly.



Contributions welcome! Open a PR to add/update entries. Keep descriptions factual and link to official sites.



## Table of Contents



- [SaaS/Hosted Platforms](#saas-hosted-platforms)

- [Open-Source GitHub Projects](#open-source-github-projects)

- [How to Contribute](#how-to-contribute)

- [Disclaimer](#disclaimer)



## SaaS/Hosted Platforms



- **[Wiz (with Gem Security)](https://www.wiz.io/)**

  Top-scoring CDR platform (8.7/10) for **contextual correlation**. Incorporates Gem Security's real-time CDR into Wiz's cloud security and vulnerability graph, allowing active runtime alerts to be evaluated directly against identity entitlements, exposed network paths, and existing vulnerabilities. Strengths: real-time detection plus graph context, agentless visibility plus runtime, strong cloud-identity detection. Trade-offs: integration of Gem to confirm, premium pricing.



- **[Sysdig](https://sysdig.com/)**

  Top-scoring CDR platform (8.9/10) for **best real-time detection**. Provides **Falco-powered runtime protection** correlated with cloud control-plane telemetry, utilizing eBPF-driven runtime threat detection to catch in-progress container escapes and abnormal process execution. Strengths: fastest, deepest cloud runtime detection; Falco lineage; strong drift and threat detection. Trade-offs: VM/Windows breadth trails giants.



- **[CrowdStrike Falcon Cloud Security](https://www.crowdstrike.com/)**

  Top-scoring CDR platform (8.7/10) for **best response automation**. Applies battle-tested EDR and threat intelligence to cloud control-plane events and runtime containers, delivering real-time threat detection and automated response with rapid incident containment. **Real-time CDR** eliminates log batch processing (15+ minutes) by using event streaming technology, analyzing cloud activity as it happens and stopping breaches in seconds. Extended to Google Cloud in April 2026 with regional data sovereignty support. Strengths: best response automation; adversary intel; endpoint+cloud+identity in one console. Trade-offs: cloud-native breadth trails pure-plays; modular pricing.



- **[Palo Alto Networks (Prisma Cloud + Cortex XDR)](https://www.paloaltonetworks.com/)**

  CDR platform (8.4/10) for **best in a platform**. Delivers comprehensive cloud threat detection spanning Prisma Cloud and Cortex XDR, unifying control-plane auditing with host runtime telemetry and modern Security Service Edge (SSE) platforms. Strengths: platform breadth; strong runtime and identity detection; unified response. Trade-offs: credit modelling; platform commitment.



- **[Microsoft Defender for Cloud](https://www.microsoft.com/)**

  CDR platform (8.1/10) for **best Azure economics**. Provides native control-plane audit log analysis and workload threat detection across Azure, extending to AWS and GCP via Azure Arc, bundled into Microsoft Defender cloud security plans. Strengths: Azure-gravity economics; Defender XDR correlation; multicloud via Arc. Trade-offs: real-time depth outside Azure trails specialists.



- **[Orca Security](https://orca.security/)**

  CDR platform (7.9/10) for **best agentless telemetry**. Agentless side-scanning feeds cloud detection with broad estate coverage and data/identity context. Strengths: 100% agentless visibility across compute and storage; broad multi-cloud coverage; rich context around data exposure and software vulnerabilities. Trade-offs: real-time runtime response trails agent-based leaders; pair for enforcement.



- **[Uptycs](https://www.uptycs.com/)**

  CDR platform (7.6/10) for **best unified telemetry**. Normalizes osquery and eBPF telemetry for unified detection across cloud workloads.



- **[Skyhawk Security](https://www.skyhawk.security/)**

  CDR platform (7.9/10) for **best purpose-built CDR**. Spun out of Radware, focuses specifically on cloud threat detection using machine learning to correlate API anomalies into complete attack sequences alongside identity threat detection and response (ITDR). Strengths: purpose-built CDR focus; attack-sequence ML; multicloud. Trade-offs: smaller ecosystem.



- **[Sweet Security](https://www.sweet.security/)**

  CDR platform (7.9/10) for **best runtime-sensor CDR**. Delivers deep runtime detection using a lightweight eBPF sensor, focusing on runtime workload vulnerability and threat management to filter out cloud noise and elevate verified security incidents. Strengths: deep runtime detection; strong signal-to-noise; cloud-native focus. Trade-offs: younger vendor; breadth building.



- **[Stream.Security](https://www.stream.security/)**

  CDR platform (8.1/10) for **best cloud-model real-time**. Leverages a dynamic Cloud Twin model to track infrastructure changes in real time, rapidly identifying cloud misconfigurations and exposures the instant an architectural modification occurs. Strengths: real-time change-driven detection; cloud-model approach; good response. Trade-offs: younger vendor; durability diligence.



## Open-Source GitHub Projects



### Runtime Threat Detection Engines



- **[Falco](https://github.com/falcosecurity/falco)**

  **The CNCF-graduated runtime threat detection engine and the foundation of open-source cloud runtime security.** Created by Sysdig in 2016, donated to CNCF in 2017, graduated in 2024. Monitors system calls (low-level interface between kernel, user applications, and hardware) and checks them against rules to detect suspicious activity. **Key capabilities**: broadest community rule library, Kubernetes audit log monitoring, cloud events via APIs and plugins, MITRE ATT&CK-aligned predefined rules, PCI DSS and SOC 2 compliance support. **Extensible** via Falcosidekick (alert routing), Falco plugins, Falco Talon (no-code threat management), and Falcoctl (rule lifecycle management). **Apache-2.0**. Detects T1611 (Escape to Host), T1610 (Deploy Container), and T1613 (API discovery).



- **[Tetragon](https://github.com/cilium/tetragon)**

  **eBPF-native runtime security and observability enforcement from Isovalent (Cisco).** Unlike Falco (userspace rule engine), Tetragon runs eBPF-native: **TracingPolicies** define observation and optional **in-kernel enforcement**, including killing a process before the syscall completes. **Kubernetes Identity Aware Policies** (v1.1) enable granular policy application to specific pods or namespaces, reducing alert noise and overhead. **Default Ruleset** for enterprise users provides out-of-the-box monitoring for runtime executions, network observability, file integrity, OS integrity, container sandboxing, and security-sensitive events. **Sandbox Policies** provide high-level system call auditing and enforcement. Runs lower p99 CPU overhead than Falco; strong on T1059.004. **Apache-2.0**.



- **[Tracee](https://github.com/aquasecurity/tracee)**

  **eBPF-native runtime security and forensics from Aqua Security.** Built-in signature library plus **Rego policy** support. Strong on T1611 escapes and ptrace privilege escalation (T1055.009). **Apache-2.0**.



- **[KubeArmor](https://github.com/kubearmor/KubeArmor)**

  **LSM-based runtime security from AccuKnox (AppArmor, SELinux, BPF-LSM).** Enforces policy at the kernel rather than only observing. **Apache-2.0**.



- **[Sysdig OSS](https://github.com/draios/sysdig)**

  The low-level syscall capture engine that sits under Falco. Useful as a forensic capture-and-replay primitive.



### Cloud Control-Plane & Forensics



- **[Argus](https://github.com/nssriraam/argus)**

  **Open-source AWS & Azure cloud forensics and threat detection platform.** Features **MITRE ATT&CK attack chain correlation**, live dashboard, automated PDF reports, and **zero infrastructure cost**. **Key capabilities**: AWS CloudTrail JSON parser, Azure Activity Log normalizer, real-time CloudTrail polling daemon, detection rule engine with MITRE ATT&CK rules (credential access T1552/T1078, defense evasion T1562), AWS CLI remediation command mapper, case isolation with partitioned datasets, audit trail with `ingested_at` timestamps and hash verification, and chain of custody (`OPEN → INVESTIGATING → CLOSED → ARCHIVED`). **Python 3.10+**, requires AWS credentials. **Open source**.



### Kubernetes Runtime Detection



- **[Kubescape node-agent](https://github.com/kubescape/node-agent)**

  **eBPF-based runtime detection agent for Kubernetes from Kubescape.** **Key components**: Tracer Manager (eBPF tracers for syscalls and events), Rule Manager (evaluates security rules using **CEL expressions**), Profile Manager (learns and maintains application behavior profiles), Malware Manager (coordinates **ClamAV scanning**), SBOM Manager (generates Software Bill of Materials using **Syft**). **Built-in gadgets**: exec, open, network, dns, capabilities, seccomp, exit, fork, symlink, hardlink, ptrace, kmod, ssh, http, randomx, iouring, unshare, bpf. **Detection Rules**: CEL-based rules defined as Kubernetes Custom Resources (RuntimeAlertRuleBinding). Built-in rule categories include Process Rules (unexpected executables, shell spawning) and Crypto Mining Detected (R1001, critical severity). **Feature toggles** for application profiling, runtime detection, malware detection, network tracing, SBOM generation, file integrity, seccomp profiles, HTTP detection, and network streaming. **Apache-2.0**.



### Network Detection & Response



- **[Clear NDR Community (Stamus Networks)](https://github.com/StamusNetworks/SELKS)**

  **Free, open-source, turn-key Suricata network detection and response (NDR) implementation** with built-in threat hunting and **native AI interfaces** (MCP support). **GPLv3 license**. Available as live/installable **Debian-based ISO** or **Docker container**. **Components**: Suricata 8.0 (IDS/IPS/NSM engine), Fluent (data collector), OpenSearch (search and observability), Evebox (alert and event management), Arkime (network analysis and packet capture), Scirius (Suricata hunting and ruleset management UI), MCP (standard interface to third-party AI systems). **Scirius** provides web interface for managing rulesets, hunting threats with predefined filters, applying thresholding/suppression, and viewing Suricata performance stats. **Minimum requirements**: 2 CPU cores, 8-10 GB RAM, 50GB disk, 2 network interfaces. **Suitable as production-grade NDR for small-to-medium organizations**.



### Additional Strong Open-Source Options



- **Runtime Detection**: **Falco** (CNCF graduated, broadest rule library), **Tetragon** (eBPF-native enforcement), **Tracee** (signature + Rego), **KubeArmor** (LSM-based enforcement).

- **Cloud Forensics**: **Argus** (AWS/Azure, MITRE ATT&CK, zero infrastructure cost).

- **Kubernetes Runtime**: **Kubescape node-agent** (CEL rules, ClamAV, SBOM).

- **Network Detection**: **Clear NDR Community** (Suricata-powered, MCP AI interfaces).



**Frameworks for building custom systems**: Combine **Falco** for runtime threat detection with the broadest rule library, **Tetragon** for eBPF-native enforcement (killing processes before syscall completion), **Argus** for AWS/Azure cloud forensics with MITRE ATT&CK correlation, **Kubescape node-agent** for Kubernetes-specific CEL-based detection and malware scanning, and **Clear NDR Community** for network-level detection. Add **Falcosidekick** for alert routing and **Falco Talon** for no-code threat management.



## How to Contribute



1. Fork the repo.

2. Add/edit entries in `README.md` (follow existing format).

3. Include: name, link, 1–2 sentence description, and whether it's SaaS or open-source.

4. Submit PR with a short explanation.



Star the repo if you find it useful!



## Disclaimer



- This is a **community-curated** list — not exhaustive and not an endorsement.

- CDR platforms handle sensitive cloud telemetry and security data; ensure compliance with data protection regulations and cloud provider terms of service.

- **Open-source reality**: The open-source ecosystem for cloud detection and response is **mature at the runtime detection layer** (**Falco**, **Tetragon**, **Tracee**, **KubeArmor**) and **cloud forensics layer** (**Argus**). **Clear NDR Community** provides production-grade network detection for small-to-medium organizations. **Kubescape node-agent** delivers comprehensive Kubernetes runtime detection with CEL rules and malware scanning. However, **commercial CDR platforms** (Wiz, CrowdStrike, Sysdig, Palo Alto) provide **real-time control-plane correlation, automated response at scale, identity threat detection, and unified multi-cloud visibility** that open-source alternatives require significant integration and engineering investment to match. The open-source path is most viable for organizations with strong platform security engineering capacity or for specific runtime/forensics use cases.



---



**Made for cloud security architects, SOC analysts, threat hunters, and platform security engineers.**

Let's make cloud detection and response more open, transparent, and real-time.
