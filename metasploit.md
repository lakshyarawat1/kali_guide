# Metasploit Guide

## Introduction 

- Ruby-based, modular pentesting platform
- Enables us to write, test and execute exploit codes.
- The metasploit framework has a suite of tools that can be used to test security vulnerabilities, enumerate networks, execute attacks, and evade detection.

### Metasploit Framework Console

- The msfconsole is the most popular interface for Metasploit framework.

## Architecture

- By default, all the base files for the framework can be found under /usr/share/meatsploit-framwork

- Data and Lib files are the functional parts of the framework and the Documentation have technical specifications of the framework enlisted.

### Plugins

- Offers more flexibility to the pentester when using the msfconsole.

### Scripts

- Meterpreter functionality and other useful scripts.

### Tools 

- Command line utilities

## MSF engagement structure

- The MSF engagement structure can be divided into five main categories.
    - Enumeration
    - Preparation
    - Exploitation
    - Privilege Escalation
    - Post-Exploitation

## Metasploit Modules

- Modules are prepared scripts for a specific purpose
- `` exploit `` category consists of so-called ``proof-of-concept`` POCs that can be used to exploit existing vulnerabilities.
- Most exploits doesnot run on their own, they need customization for being effective.

### Index no.

- No. displayed to select the exploit we want afterward during our searches.

### Type

- Type tag is 1st level of segregation between msf modules.
- Types show what the exploit is going to do.

- Here are some possible types of the exploits : 
    - Auxiliary : Scanning, fuzzing, sniffing and admin capabilities. Offer extra assistance and functionality.
    - Encoders : Ensure that payload are intact to their destination.
    - Exploits : Defined as modules that exploits a vuln.
    - NOPs : No Operation Codes. Keep the payload size consistent across exploits.
    - Payloads : Code run remotely and calls back to the attacker machine to establish a connection or shell.
    - Plugins : Additional scripts can be integrated.
    - Post : Wide array modules to gather information, pivot deeper, etc.

- To use any module use : ``` use <no. > ``` command.