([https://industrialcyber.co/reports/forescout-sundown-research-uncovers-critical-vulnerabilities-in-solar-inverters-that-threaten-power-grid-stability/](https://industrialcyber.co/reports/forescout-sundown-research-uncovers-critical-vulnerabilities-in-solar-inverters-that-threaten-power-grid-stability/))

1. six major solar inverter manufacturers, including Huawei, Sungrow, Ginlong Solis, Growatt, GoodWe, and SMA Solar Technology

1. The SUN:DOWN research revealed that Sungrow, SMA, and Growatt have nearly 50 vulnerabilities that could disrupt the power grid and lead to blackouts. Additionally, the research identified 93 known vulnerabilities, with 80 percent classified as high or critical severity, having a CVSS score ranging from 9.8 to 10.

1. First, attackers hijacked 800 Contec SolarView Compact devices in Japan, raising concerns about grid stability, with conflicting reports attributing the breach to either the hacktivist group HackerCN or random malware botnets. Second, Chinese threat actor Flax Typhoon exploited similar devices, using botnets to obscure their identities while targeting networks abroad. Lastly, the Just Evil hacktivist group accessed the power monitoring dashboard of 22 clients of Lithuania’s Ignitis Group, including two hospitals, by obtaining valid credentials through a Trojan on customer devices.

1. These include multiple Insecure Direct Object Reference (IDOR) issues in the APIs leading to unauthorized access to resources in cloud platforms, broken authorization, multiple Cross-Site Scripting (XSS) vulnerabilities in web applications, and unrestricted file uploads on cloud web applications, also leading to remote code execution (RCE). They also identified hard-coded credentials and improper certificate validation in a mobile application, buffer overflows in a Wi-Fi communication dongle, and unauthenticated over-the-air firmware updates leading to RCE and persistent device takeover.

1. “Vulnerabilities on Growatt have not been assigned CVE IDs,” the research report said. “For these vulnerabilities, we use internal identifiers starting with FSCT-2024.

1. The operational technology deeply integrated into the traditional grid, with legacy programmable logic controllers (PLCs), remote terminal units (RTUs), intelligent electronic devices (IEDs) and other equipment that is either not secure-by-design or, worse, is insecure-by-design, left us with power grids that can be taken over by cyberattacks.”

1. If an attacker can use the manufacturer’s cloud as an entry point, execute malicious code on an inverter, and use that as a pivot point into parts of the network, they must have a way to mitigate this risk.

1. vulnerability exploitation, password guessing, and unauthorized use of OT protocols.

1.   
      
    

- **Sungrow devices** suffered **IDOR issues** (insecure direct object references), using **hard-coded credentials** and abused unsecured **MQTT messages** to trigger **Remote Code Execution (RCE)** on dongles, enabling full control of the inverter [LinkedIn+4Forescout+4Owler+4](https://www.forescout.com/press-releases/forescout-vedere-labs-uncovers-severe-systemic-security-risks-in-global-solar-power-infrastructure/?utm_source=chatgpt.com).

- **SMA’s SunnyPortal** had an RCE vulnerability allowing attackers to upload `.aspx` files that ran on the company’s web server (e.g. CVE‑2025‑0731)