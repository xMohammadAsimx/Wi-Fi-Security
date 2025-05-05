# Wi-Fi Network Security

This repository contains research and practical implementations related to Wi-Fi network security. It covers the evolution of Wi-Fi security protocols from WEP to WPA3, discusses their vulnerabilities, and demonstrates practical attack scenarios using tools like Flipper Zero, Wireshark, and Hashcat.

## Introduction
Wi-Fi has become an essential part of modern digital life, enabling wireless internet connectivity in homes, businesses, and public spaces. However, the openness of wireless channels exposes networks to various security threats. This project aims to provide a comprehensive analysis of Wi-Fi security protocols, their vulnerabilities, and practical attack scenarios.

## Wi-Fi Security Protocols
### WEP (Wired Equivalent Privacy)
- **Overview**: The first security protocol for Wi-Fi, introduced in 1999.
- **Vulnerabilities**: Short IVs, weak RC4 encryption, linear CRC-32 integrity checks, and shared key authentication weaknesses.
- **Attacks**: FMS attack, ARP replay attack, bit-flipping attack, KoreK attack, PTW attack.

### WPA (Wi-Fi Protected Access)
- **Overview**: Introduced in 2003 as a transitional solution to WEP vulnerabilities.
- **Vulnerabilities**: Weaknesses in TKIP, MIC (Michael) algorithm, and shared key model.
- **Attacks**: Beck-Tews attack, Hole196 attack, dictionary and brute-force attacks, TKIP MIC DoS attack, Evil Twin attack.

### WPA2 (Wi-Fi Protected Access II)
- **Overview**: Standardized in 2004, it introduced AES-based encryption and stronger integrity mechanisms.
- **Vulnerabilities**: KRACK attack, PMKID attack, nonce reuse issues, group key rekeying flaws, EAP vulnerabilities.
- **Attacks**: KRACK attack, PMKID-based WPA2 password cracking.

### WPA3 (Wi-Fi Protected Access III)
- **Overview**: Introduced in 2018 to address WPA2 vulnerabilities, it includes features like SAE handshake, forward secrecy, and stronger encryption.
- **Vulnerabilities**: Side-channel attacks, downgrade attacks, DoS attacks, authentication bypass vulnerabilities, formal verification challenges, WPA3-PK specific vulnerabilities.
- **Mitigations**: Dragonshield, autoencoder-based noise injection, Hamming-distance redistribution, transition disable, SSID inclusion in handshake, AFST-DA, bad-token detection, IDS, SAE-PK, ComPass protocol, SPIN model checking.

## Vulnerabilities and Attacks
### Key Vulnerabilities
- **Short Initialization Vectors (IVs)**: Lead to keystream reuse and IV collisions.
- **Weak Encryption (RC4)**: Reused keystreams allow attackers to recover plaintext.
- **Linear Integrity Check (CRC-32)**: Allows bit-flipping attacks.
- **Shared Key Authentication Weaknesses**: Challenge-response can be captured and reused.

### Practical Attacks
- **FMS Attack**: Uses statistical analysis to recover the WEP key.
- **ARP Replay Attack**: Injects spoofed ARP requests to generate predictable encrypted responses.
- **Bit-Flipping Attack**: Modifies encrypted messages without knowing the key.
- **KoreK Attack**: Uses correlations to recover the root key byte by byte.
- **PTW Attack**: Reduces the number of packets required for a successful attack.
- **Beck-Tews Attack**: Injects arbitrary packets by crafting MICs.
- **Hole196 Attack**: Spoofs DHCP, DNS, or ARP responses.
- **KRACK Attack**: Forces nonce reuse by manipulating handshake messages.
- **PMKID Attack**: Captures PMKID for offline brute-force cracking.

## Practical Implementations
### Evil Portal (Captive Portal Phishing)
- **Tools**: Flipper Zero, Wi-Fi Development Board.
- **Process**: 
  1. Set up a rogue access point.
  2. Redirect users to a fake login page.
  3. Capture user credentials.
- **Mitigation**: User education, HTTPS enforcement, network authentication mechanisms.

### PMKID-Based WPA2 Password Cracking
- **Tools**: Flipper Zero, Hashcat, Wireshark.
- **Process**:
  1. Capture PMKID from the access point.
  2. Use Hashcat for offline brute-force cracking.
- **Mitigation**: Strong passwords, WPA3 implementation.

## Comparative Analysis
| Aspect                | Evil Portal Attack | PMKID Attack |
|-----------------------|--------------------|--------------|
| Attack Type           | Social Engineering | Cryptographic |
| User Interaction      | Required           | Not Required |
| Target Protocols      | WEP, WPA, WPA2     | WPA2         |
| Tools Used            | Flipper Zero       | Flipper Zero, Hashcat |
| Mitigation Strategies | User Education, HTTPS Enforcement | Strong Passwords, WPA3 Implementation |

## Contributions
- **Mohammad Asim**: Research, writing, implementation of attacks, and project coordination.
- **Mohammad Zubair**: Research, writing, and presentation.

## References
- [1] S. Fluhrer, I. Mantin, and A. Shamir, "Weaknesses in the key scheduling algorithm of rc4," in Selected Areas in Cryptography. Springer, 2001, pp. 1–24.
- [2] M. Vanhoef and F. Piessens, "Key reinstallation attacks: Forcing nonce reuse in wpa2," in Proceedings of the 2017 ACM SIGSAC Conference on Computer and Communications Security. ACM, 2017, pp. 1313–1328.
- [3] M. Vanhoef and E. Ronen, "Dragonblood: Analyzing the dragonfly handshake of wpa3 and eap-pwd," in Proceedings of the 2019 IEEE Symposium on Security and Privacy. IEEE, 2019, pp. 517–533.
- [4] N. Borisov, I. Goldberg, and D. Wagner, "Intercepting mobile communications: The insecurity of 802.11," in Proceedings of the 7th annual international conference on Mobile computing and networking. ACM, 2001, pp. 180–189.
- [5] C. He and J. C. Mitchell, "Security analysis and improvements for ieee 802.11i," in Proceedings of the Network and Distributed System Security Symposium (NDSS), 2005.

For more detailed information, please refer to the [Full Paper](Project%20Report/Wi_Fi_Network_Security.pdf) and [Presentation](Presentation/WiFi-Security.pdf).
