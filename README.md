# SRGenerator

SRGenerator, short for the Snort Rule Suggester, is a command-line tool that can be used to detect potentially malicious network traffic. 

# About

**SRGenerator** was created to detect four types of potentially malicious network activity by analyzing a network capture file, or pcap: SSH brute-forcing, FTP brute-forcing, network host-scanning, and port-scanning activity. Upon detection of one or more of these behaviors, SRG alerts the user by printing a summary of the triggering behavior. SRG also suggests an appropriate **Snort** rule for users to implement, allowing them to detect, alert, and log similar activity in the future.

**Snort** is a popular, easy-to-use network intrusion detection system (IDS) can be used as a straight packet sniffer like tcpdump, a packet logger (useful for network traffic debugging, etc), or as a full blown network intrusion prevention system. The rules provided assume use of Snort as an NIDS.

# Features

* Reads pcap files from the command line
* Provides a count of packets in file
* Provides a color-coded summary table of layer 3 traffic recorded in the file including: source IP, destination IP, and number of packets sent in each conversation
* Detects and alerts to potential SSH brute-force traffic (source port 22)
* Detects and alerts to potential FTP brute-force traffic (source port 21)
* Detects and alerts to port scanning activity on a single host 
* Detects and alerts to network scanning activity on multiple hosts
* Generates and prints a Snort rule for each instance described above
* Outputs a .rules file of the recommended rules for easy implementation and use with Snort (see notes section for additional detail)
* Error-checking

# Tech

SRG was built in Python 3 using sys, subprocess, and counter modules, as well as [PrettyTable](https://pypi.org/project/prettytable/), as seen in the SRGenerator.py. The script reads the provided packet capture (pcap) using TShark, the command line tool for [Wireshark](https://www.wireshark.org/download.html).

# Installation & Usage

Clone the SRG repo into your desired working directory; make `SRGenerator.py` executable: `chmod +x`

Run the script on a pcap as follows:

```
$ ./SRGenerator.py <path/yourfile.pcap>
```

**Sample output: Pcap Summary**

![Screenshot1](https://github.com/morrisseyt/SRG--Snort-Rule-Generator/blob/main/images/snortsuggester_output_table.png)

**Sample output: Alert**

![Screenshot2](https://github.com/morrisseyt/SRG--Snort-Rule-Generator/blob/main/images/snortsuggester_output_alert.png)

**Sample output: snort .rules file**

![Screenshot3](https://github.com/morrisseyt/SRG--Snort-Rule-Generator/blob/main/images/Sample.rules.png)

# Notes

SIDs (or Snort IDs) provided for reach rule generated by a given pcap will always start from 1,000,000 for each file created. Running a new pcap without renaming and saving the previously generated .rules file will overwrite the previous file. SIDs provided in the .rules file should be reviewed prior to implementation to ensure alignment with exisiting organizational policies and protocols.

# Contributors

[@morrisseyt](https://github.com/morrisseyt)
[@pwalt08](https://github.com/pwalt08)
[@jcrio](https://github.com/jcrio)

# References & Further Reading

* [Wireshark](https://www.wireshark.org/download.html)
* [TShark](https://www.wireshark.org/docs/man-pages/tshark.html)
* [Snort](https://www.snort.org/)
* [Pcaps: Links and samples](https://gitlab.com/wireshark/wireshark/-/wikis/SampleCaptures)
* Brute Force attacks
* Another link
* More to read
* Check this out too

# Process Art

![logo](https://github.com/morrisseyt/SRG--Snort-Rule-Generator/blob/main/images/SRGLogo.png)

# License





