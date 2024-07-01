tags: #DF
 
# Searching and Sorting

links: [[706 DF TOC - Mobile Forensics|DF TOC - Mobile Forensics]] - [[themes/000 Index|Index]]

---

## History

In the pre-smartphone era, crime scenes often involved various separate devices such as:

- Phones
- PDAs
- Cameras
- Pagers

Early market leaders in mobile technology included Nokia and Motorola, with Blackberry emerging later. These devices lacked USB connectivity, relying instead on RS232 serial connections and proprietary cables. Some forensic analysis utilized JTAG interfaces. During this period, there was no encryption, but data formats and protocols were proprietary.

The amount of data available on these devices was minimal compared to today's standards. Typical data included:

- Call history
- Simple phone book entries
- SMS messages
- Configuration data
- SIM card information

Both the phone and the SIM card had their own memory storage, requiring forensic examiners to extract and analyze data from multiple sources.

## Sim card

A SIM card is essentially a standard smartcard that adheres to the ISO 7816-3 interface. It is used for authentication, identification, and data storage in mobile devices. SIM stands for Subscriber Identity Module, and it includes variants like eSIM. One key identifier stored on the SIM card is the IMSI (International Mobile Subscriber Identity).

Data storage on SIM cards is limited, with capacity typically measured in kilobytes. Stored data often includes a simple phone book (names and numbers), SMS text messages, and the last number dialed.

## Smartphone Challenges

Smartphone forensics presents distinct challenges compared to computer forensics. Key issues include:

- **Device Unlocking:** User authentication methods such as PINs, passwords, biometrics.
- **Device Decryption:** Accessing encrypted storage often requires advanced techniques like chip-off.
- **Device Lockdown:** Features like secure elements, enclaves, and KNOX increase difficulty.
- **Proprietary Interfaces and Protocols:** Unique physical interfaces and communication protocols hinder standardization.
- **Proprietary File Formats:** Specialized formats require tailored forensic tools.
- **Non-removable Batteries:** Prevents easy power cycling during examinations.
- **Active Radios:** Requires Faraday cages or bags to disable communications.
- **Manufacturer Control:** Manufacturers have significant control over device functionalities and updates, complicating forensic procedures.

## Tools and companies

### Tools and Products

Mobile forensic tools can be divided into physical appliances and software solutions. These tools facilitate both physical and logical acquisitions of data from mobile devices. Key components include:

- **Acquisition Software:** Extracts data from devices.
- **Analysis Software:** Examines and interprets extracted data.
- **Forensic Acquisition Cable Kits:** Provide necessary connections for data extraction.
- **Mobile Malware Analysis:** An expanding field focusing on identifying and understanding mobile malware.
- **Biometrics:** Tools that handle data from fingerprints and facial recognition, addressing issues like fake, forced, or tricked authentication methods (e.g., "Alternate Appearance" on iPhones).

### Mobile Forensic Companies

Companies in the mobile forensics sector engage in extensive technology development, often relying on in-house research and reverse engineering to understand devices and software. They license proprietary technology and sometimes purchase exploits to enhance their capabilities.

- **Product Sales:** Companies tend to be secretive about their tools' capabilities, often restricting sales to law enforcement to prevent competitors from analyzing their products.
- **Acquisition as a Service:** Some companies offer services where devices are sent in for data acquisition, and results are provided back to the customer.

## Artifacts

Mobile forensic tools can extract a wide range of artifacts from smartphones, including:

- **Call History:** Records of incoming, outgoing, and missed calls.
- **SMS Texts and Emails:** Messages sent and received via SMS and email applications.
- **Apps and App Data:** Information and data from installed applications.
- **Media Files:** Photos, videos, and audio recordings stored on the device.
- **User Content:** Purchased or downloaded content like music, books, and movies.
- **Geo-location Data:** GPS, cell tower, WiFi, and telemetry data providing location history.
- **Logs and Configuration Data:** Operating system and application logs, device settings, and configuration files.
- **Bluetooth Device History:** Records of connected Bluetooth devices.
- **WiFi Hotspot History:** Information on previously connected WiFi networks.
- **Cell Tower Connection History:** Data on past cell tower connections.

The extent of data recovery depends on the specific phone model and its configuration.

## Evolution

Mobile forensics has evolved beyond traditional mobile phones to include various devices, adapting existing forensic products to meet new challenges. Key developments include:

- **Diverse Devices:** Expansion to include iPads, tablets, drones, and IoT devices.
- **Vendor Pressure:** Increasing demand for vendors to provide decryption capabilities.
- **Telemetry Focus:** Greater emphasis on extracting telemetry data from apps.
- **Cloud Data Integration:** Inclusion of data stored in cloud services.
- **Linked Device Evidence:** Gathering evidence from interconnected devices such as cars and computers.
- **Third-party Evidence:** Using geolocation data from non-involved people or objects, like AirTags, for investigative purposes.

---
links: [[706 DF TOC - Mobile Forensics|DF TOC - Mobile Forensics]] - [[themes/000 Index|Index]]