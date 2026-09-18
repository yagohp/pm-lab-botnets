# Description
- Probable Name: Trojan Strictor?
- Description: Infection and access to https://www.us.hsbc.com with a MITM proxy.
- MD5: 6e2c7ac99c050398518c06cfe913b59c  
- SHA1: eefbb18e94db73b7c098d48835eeff70c1442757  
- SHA256: 5a94ce69d7d3ec73901c1b85e89e9e879f529d07fd564011f3443c693b32225c  
- Password of zip file: infected
- Duration: 8.8 minutes
- Proxy Usage: This capture did use an intermediate proxy.

- [VirusTotal](https://www.virustotal.com/en/file/5a94ce69d7d3ec73901c1b85e89e9e879f529d07fd564011f3443c693b32225c/analysis/)
- [HybridAnalysis](https://www.hybrid-analysis.com/sample/5a94ce69d7d3ec73901c1b85e89e9e879f529d07fd564011f3443c693b32225c?environmentId=2)
- RobotHash

[![](https://robohash.org/6e2c7ac99c050398518c06cfe913b59c)](https://robohash.org)

# Files

- .capinfos
    - Capinfos file
- .dnstop
    - DNS top file
- mitm.out
    - Mitm proxy interception file of http and https
- .mitm.weblog
    - This is the HTTP and HTTPS web log that includes Labels. This is the preferred file for web analysis.
    - This file includes a header with the columns names. There are two new columns defined by us:
        - Column id: This number is unique for all the weblogs generated __inside__ the same TCP connection. When a TCP connection is opened and several GET/POST, etc., requests are made inside it, all of them are assigned the same Id in this file.
        - Column timestamp_end: This is the timestamp when the weblog ended. If you use this with the id column you can compute the total duration of the TCP connection that generated __all__ the weblogs. Similar to the duration of a hypothetical CONNECT request if this would have been done using a proxy.
- .passivedns
    - Passive DNS file
- .pcap
    - Original pcap file
- .rrd
    - RRD file for graphs
- .weblogng
    - WEB log of http traffic only. Generated with justsniffer
- .exe.zip
    - Original malware file
- bro
    - Folder with all the bro output files
- .biargus
    - Argus binary file. Bidirectional flows, 3600s of report time.
- .binetflow
    - Argus text file with bidirectional flows. Report time 3600 secs.
- .uniargus
    - Argus binary file. Unidirectional flows, 5s of report time.
- .uninetflow
    - Argus text file with unidirectional flows. Report time 5 secs. TAB as column separator.

# IP Addresses
    - Infected host: 192.168.1.123
    - Default GW: 192.168.1.2

# Timeline

## Mon Jul  3 18:27:05 CEST 2017
started win13

## Mon Jul  3 18:31:28 CEST 2017
infected

## Mon Jul  3 18:33:02 CEST 2017
I opened the IE without any page.

## Mon Jul  3 18:35:31 CEST 2017
https://www.us.hsbc.com

## Mon Jul  3 18:43:03 CEST 2017
power off

# Disclaimer 
These files were generated in the Stratosphere Lab as part of the Malware Capture Facility Project in the CVUT University, Prague, Czech Republic.
The goal is to store long-lived real botnet traffic and to generate labeled netflows files.
Any question feel free to contact us:
Sebastian Garcia: sebastian.garcia@agents.fel.cvut.cz

You are free to use these files as long as you reference this project and the authors as follows:
Garcia, Sebastian. Malware Capture Facility Project. Retrieved from https://stratosphereips.org
