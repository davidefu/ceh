# Hacking IoT

## Perform footprinting using various footprinting techniques

- Gather information using online footprinting tools
<https://www.whois.com/whois/>
<https://www.exploit-db.com/google-hacking-database>
    "login" intitle:"scada login"
shodan
    port:1883 (MQTT)
    port:502 (ICS/SCADA)

## Capture and analyze IoT device traffic

- Capture and analyze IoT traffic using Wireshark
Publish message:
    Header Flags: Contains information regarding the MQTT control packet type.
    DUP flag: If the DUP flag is 0, it indicates the first attempt at sending this PUBLISH packet; if the flag is 1, itindicates a possible re-attempt at sending the message.
    QoS: Determines the assurance level of a message.
    Retain Flag: If the retain flag is set to 1, the server must store the message and its QoS, so it can cater tofuture subscriptions matching the topic.
    Topic Name: Contains a UTF-8 string that can also include forward slashes when it needs to be hierarchicallystructured.
    Message: Contains the actual data to be transmitted.
    Payload: Contains the message that is being published.
