name derivation ( so**lar** s**e**ntina**l** )

### ⚠️ **Key Incidents & Concerns Behind the Problem Statement**

1. **US SolarWinds Hack & Energy Infrastructure Attacks (2020):**
    
    - While not solar-specific, this attack showed how **supply chain vulnerabilities** can affect critical infrastructure.
    
    - It raised alarms globally about **energy sector cybersecurity**.
    

1. **India's Increasing Solar Capacity**
    
    - India crossed **70 GW+** of installed solar capacity.
    
    - Many of these installations use **imported inverters** (mainly from China) with **closed or unknown firmware**, raising **national security concerns**.
    

1. **Unsecured Solar Inverters Found Exposed on Shodan (2022–2024):**
    
    - Thousands of solar inverters were found **exposed online** via open ports like Telnet, Modbus, and HTTP, with **default or no passwords**.
    
    - Hackers can remotely **control or disable** these devices.
    

1. **Ransomware in Renewable Sector (e.g., Invenergy USA 2021):**
    
    - A major **renewable energy firm** faced a ransomware attack.
    
    - Showed that **green energy is not immune** to cyberthreats.
    

1. **Lack of Mandatory Security Audits in Indian Rooftop Installations**
    
    - Many **residential and institutional solar systems** in India are installed by third parties with **no security validation**.
    
    - This leaves systems vulnerable to **firmware tampering or remote exploits**.
    

  

## Protocols to be read :

MQTT, custom TCP, LoRaWAN

## News Articles (for the incident)

1. Rogue communication devices found in Chinese solar inverters - ["https://www.reuters.com/business/energy/rogue-communication-devices-found-chinese-solar-inverters-2025-05-14/"](https://www.utilitydive.com/news/rogue-communication-devices-found-on-chinese-made-solar-power-inverters/748242/)

1. [https://industrialcyber.co/utilities-energy-power-water-waste/us-energy-sector-at-risk-as-chinese-inverters-are-under-investigation-for-suspicious-communication-gear/](https://industrialcyber.co/utilities-energy-power-water-waste/us-energy-sector-at-risk-as-chinese-inverters-are-under-investigation-for-suspicious-communication-gear/)

1. Solar power gear vulnerable to remote sabotage -[https://www.cybersecuritydive.com/news/solar-power-gear-vulnerable-remote-sabotage/743806/](https://www.cybersecuritydive.com/news/solar-power-gear-vulnerable-remote-sabotage/743806/)

1. [https://www.forescout.com/press-releases/forescout-vedere-labs-uncovers-severe-systemic-security-risks-in-global-solar-power-infrastructure/](https://www.forescout.com/press-releases/forescout-vedere-labs-uncovers-severe-systemic-security-risks-in-global-solar-power-infrastructure/)

1. [https://www.cisa.gov/news-events/ics-advisories/icsa-25-105-04](https://www.cisa.gov/news-events/ics-advisories/icsa-25-105-04)

1. [https://www.infosecurity-magazine.com/news/solar-power-vulnerabilities/](https://www.infosecurity-magazine.com/news/solar-power-vulnerabilities/)

[[ForeScout Sundown incident -]]

1. **800 Solar Monitoring Units Hijacked (Japan, 2024) :**
    
    1. the perpetrators used a known vulnerability to install a backdoor
    
    1. This attack did not affect Japan’s power grid
    
      
    

Sungrow inverters could be hijacked by harvesting communication dongle serial numbers through various insecure direct object references (IDORs), using hard-coded credentials found on the device and publishing messages that lead to remote code execution, and full takeover of the inverter.

## Research papers:

1. **Anomaly Detection in Industrial Control Systems—A Survey**IEEE, 2020[https://ieeexplore.ieee.org/document/9091296](https://ieeexplore.ieee.org/document/9091296)

1. **Security and Privacy in IoT-Enabled Smart Grid: A Survey**IEEE, 2019[https://ieeexplore.ieee.org/document/8894217](https://ieeexplore.ieee.org/document/8894217)

1. **Firmware Analysis and Risks in Critical Infrastructure Devices**NDSS Symposium[https://www.ndss-symposium.org/ndss-paper/firmware-analysis-and-risks-in-critical-infrastructure-devices/](https://www.ndss-symposium.org/ndss-paper/firmware-analysis-and-risks-in-critical-infrastructure-devices/)

1. **Machine Learning for Industrial Control System Security: A Survey**IEEE, 2021[https://ieeexplore.ieee.org/document/9495969](https://ieeexplore.ieee.org/document/9495969)

1. **Cybersecurity Assessment of Solar Photovoltaic Systems**ScienceDirect, 2021[https://www.sciencedirect.com/science/article/abs/pii/S0038092X21003474](https://www.sciencedirect.com/science/article/abs/pii/S0038092X21003474)

1. **A Survey on Machine Learning for Cyber Security in Industrial Control Systems**IEEE Access, 2022Explores ML approaches for anomaly detection, intrusion prevention, and forensic analysis in ICS environments.[https://ieeexplore.ieee.org/document/9362115](https://ieeexplore.ieee.org/document/9362115)

1. **Firmware Vulnerabilities in Embedded Devices: Classification and Detection Techniques**ACM Computing Surveys, 2021Investigates common firmware flaw classes and automated security testing, especially in industrial and IoT devices.[https://dl.acm.org/doi/10.1145/3439726](https://dl.acm.org/doi/10.1145/3439726)

1. **Anomaly Detection in the Internet of Things: A Survey**Journal of Network and Computer Applications, 2020Reviews anomaly and intrusion detection methods tailored for resource-constrained IoT devices, including energy systems.[https://www.sciencedirect.com/science/article/abs/pii/S1084804520301952](https://www.sciencedirect.com/science/article/abs/pii/S1084804520301952)

1. **Cybersecurity Risk Assessment in Smart Grid Systems: A Survey**International Journal of Critical Infrastructure Protection, 2023Discusses risk models, attack vectors, and mitigation strategies relevant to smart grids and renewable energy infrastructures.[https://www.sciencedirect.com/science/article/pii/S1874540023000123](https://www.sciencedirect.com/science/article/pii/S1874540023000123)

1. **Machine Learning for Smart Grid Security: Threats, Challenges and Future Directions**Computer Science Review, 2022Examines AI methods for detecting cyberattacks in smart grids and related energy assets.[https://www.sciencedirect.com/science/article/pii/S1574013722000744](https://www.sciencedirect.com/science/article/pii/S1574013722000744)

1. **Security Challenges and Solutions for Distributed Renewable Energy Resources**IEEE Transactions on Smart Grid, 2021Studies security vulnerabilities specific to renewable energy interfacing devices like solar inverters and proposes mitigation techniques.[https://ieeexplore.ieee.org/document/9310835](https://ieeexplore.ieee.org/document/9310835)

1. **Firmware Integrity Verification in Cyber-Physical Systems**ACM Transactions on Cyber-Physical Systems, 2023Focuses on methods to verify firmware authenticity and detect tampering in critical infrastructure devices.[https://dl.acm.org/doi/10.1145/3567254](https://dl.acm.org/doi/10.1145/3567254)

  

  

## 🔍 **2. Reusing AI Models from Existing Research**

|Model / Project|Purpose|Source|
|---|---|---|
|**VulDeePecker**|Deep learning for detecting vulnerabilities in code based on code gadgets|[GitHub](https://github.com/CGCL-codes/VulDeePecker)|
|**LineVul**|Predicts vulnerable code at line-level using BiLSTM+attention|[Paper](https://arxiv.org/abs/2002.04839)|
|**SySeVR**|Uses semantic and syntactic features to predict vulnerabilities|[Research](https://arxiv.org/abs/1807.06756)|
|**BinDiff + ML**|Binary diffing with ML to detect patched vs. unpatched firmware|Used in security audits and CTF challenges|