README -- OpenAlertSystem (OAS)

Author : Umesh Kumar Mahur
Date   : 24th April 2015
Version: V_15.1
Licence: This is distributed under open source license. Anyone can freely use it and extend it and re-distribute.

OpenAlertSystem (OAS) is an open source alerting application. This can be used for any system.
OAS can generate alerts based on certain keywords (fixed and regular expression) from the application
log files. OAS reads the log files in real time (rolling logs) and generates an alarm as soon as it 
finds a match for the defined keywords.

The alerts are generated using SNMP protocol and thus these alerts can be monitored by any SNMP based
open-source alert viewing systems.

OAS has the capability to read from a fixed name log file or a pattern based log file. OAS also re-opens the
log file when the log file rolls and creates a new one. OAS can be extended to include alerting from DB 
or any other source as well.

Following environment variables need to be set before starting OASApp.
1) OAS_LOGDIR -- Points to the directory where log of OASApp is written.
2) OAS_CONFDIR -- Points to the directory where configuration files are placed.

OASApp need main config file "OAS.conf" to be present in OAS_CONFDIR.
This config file have following parameters
SNMPTARGET=113.128.161.197   # The host where alerts need to be sent
SYSTEM=APACHE                # Each system for which log file need to be monitored.
SYSTEM=BILLAPP               # There must be a corresponding config for each system
SYSTEM=TOMCATAPP             # in the same OAS_CONFDIR dir. Multiple SYSTEM can be defined.

Below is the format of system config file
SYSTEMID=11                  # System id to uniquely identify the system
LOGTYPE=FIXED                # FIXED - Fixed name file, NOTFIXED - Pattern based logs file name
LOGDIR=/tmp/test             # Dire where the log file need to be read
LOGFILE=kum.log              # Log file name or pattern
#KEYWORD=<Fixed keyword or regular expression>:<KEYWORD_ID>:<Severity>:<Alert Description>
#Multiple KEYWORDS can be defined
KEYWORD=20[0-9][0-9](1[3-9]|2[0-9]):1:info:Date is in wrong format
KEYWORD=slow response:2:Network speed on Apache is slowing down
KEYWORD=space error:3:critical:disk space is about to exhaust


