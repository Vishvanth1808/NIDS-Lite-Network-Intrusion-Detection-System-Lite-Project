CN - Project
Jerovin Floyd - 2023261
Vishvanth - 2023602
Dayanand - 2022145

NIDS-Lite: Network Intrusion Detection System

1.  Introduction

    For this CN project we decided to make NIDS-Lite, which is a lightweight network intrusion detection
    system written in C. It analyzes raw network packets in real time
    and detects suspicious or malicious behavior using simple rule-based
    detection logic. The system is designed to be fast, efficient, and
    easy to run on Linux environments.

It monitors: - TCP SYN Flood attacks - Port scanning activity - ARP
spoofing attempts - DNS tunneling indicators

NIDS-Lite uses raw packet capture via AF_PACKET sockets, which requires
root permissions.

2.  Features 

    Real-Time Packet Inspection 
    Multi-Module Detection (SYN flood, Port scan, ARP spoof, DNS tunneling) 
    Color-Coded Alerts
    Lightweight & Efficient

3.  System Requirements

-   Linux environment
-   GCC compiler
-   Root access
-   Optional tools: hping3, nmap, arpspoof, dig

4.  Project Structure

    nids_lite.c -> main implementation file

5.  How to Compile

    gcc -Wall -O2 nids_lite.c -o nids_lite

6.  How to Run

    sudo ./nids_lite

7.  Detection Logic Overview

-   SYN Flood: tracks rapid SYN packets
-   Port Scan: detects many port probes
-   ARP Spoof: identifies conflicting ARP replies
-   DNS Tunneling: detects long/abnormal DNS queries

8.  How to Demonstrate SYN Flood:

    sudo hping3 -S -p 80 -i u100 127.0.0.1

    Port Scan: sudo nmap -sS -p 1-1000 127.0.0.1

    ARP Spoof: sudo arpspoof -i -t 127.0.0.1 127.0.0.1

    DNS Tunneling: for i in {1..20}; do dig $(openssl rand -hex 30).com;
    done

9.  Limitations

-   Basic pattern detection only
-   Linux-only
-   No logging
-   Static thresholds

10. Future Improvements

-   pcap file support
-   Config file support
-   Logging to files
-   Multithreading
-   ML-based anomaly detection

11. Conclusion

    NIDS-Lite is a minimal but functional NIDS demonstrating
    real-time packet inspection and simple attack detection.