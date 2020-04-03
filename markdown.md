CovApp open-sourcing FAQ

This document is published here: https://www.d4l.io/blog/covapp-faq/. The link must never change as it’s linked to from GitHub.


MD content as of 3 April, 2020, 12:30 

---
title: CovApp open-sourcing FAQ
cover: Open-Sourcing.png
author: peter-osburg
category: blog
metadescription: "Get your questions answered about the customization and configuration of the open-sourced coronavirus app."
ogImage: Open-Sourcing.png
releasedate: 2020-04-02
draft: false
---
 
## Answers for the coronavirus app (CovApp) open-sourcing
 
## For which scenarios is the CovApp intended?
 
CovApp is intended for use in the following scenarios:
- Using the CovApp and querying SARS-CoV-2-related symptoms, people check whether there is a recommended course of action for them and whether they have to investigate suspected illnesses.
 - Using the answers as a medical history, admission staff can receive the information from the questionnaire during the admission process. Staff can then transfer the information to the clinical system.
 
**IMPORTANT:** The CovApp doesn't provide diagnostic services. The app serves to simplify the procedures in care.
 
## For which users is the CovApp intended?
 
The CovApp user is primarily the patient. To support the admission process in the form of taking a medical history, the admission staff is an additional user. The staff ensures that the patient’s answers are transferred to the clinical system.
 
## How does the CovApp support clinical processes?
 
The CovApp offers everyone a way to assess whether they may have been infected with SARS-CoV-2 by answering a questionnaire.
The answers to this questionnaire are provided in the form of a machine-readable QR code. This code can be transferred to a clinical system using a suitable QR code scanner. This workflow supports and accelerates the process of assessing medical history information.
In addition to the QR code, the questions and their associated answers can be displayed as a list and can be printed out.
 
## Where are answers in the questionnaire saved?
 
The answers to the questionnaire are saved on the device of the user. Answers can be reused later if users open the CovApp on the same device.
From a technical perspective, the questionnaire and the answers are stored in the local storage of the web browser using cookies. This means that deleting cookies also deletes all answers.
 
## How is the questionnaire developed?
 
The CovApp questionnaire was developed in cooperation with the [Robert Koch Institute](https://www.rki.de/) (RKI). Together with the RKI, we continuously evaluate the questions and expand and adapt them as needed.
 
## Can I use the CovApp myself?
 
Yes, we offer the CovApp open-source solution on [GitHub](https://github.com/d4l-data4life/covapp). You find the source code and documentation there. If you follow the instructions, you can customize the application and offer it to your patients to support your admission process.
 
## Which requirements must be met?
 
The CovApp is a web app. No data is stored on servers, which means that all data is processed on the client side and stored if necessary. The CovApp is written in the [TypeScript](https://en.wikipedia.org/wiki/TypeScript) programming language, which is based on JavaScript. The hardware requirement therefore consists of providing a static web server.
 
Keep in mind that the CovApp must be available on the internet to provide access for patients who aren’t within your network infrastructure. You can find details on installing and configuring the CovApp on [GitHub](https://github.com/d4l-data4life/covapp).
 
After users complete the questionnaire, the CovApp generates a QR code that can be read by a QR code scanner. To transfer the data to the clinical system, the respective interfaces must be implemented on the customer side. Since the QR code is based on a minimal XML structure, you need the description of the XML structure, which we provide, to implement a potential mapping function.
 
## Which deliverables are provided by Data4Life?
 
**Source code** 
You can find the CovApp source code on [GitHub](https://github.com/d4l-data4life/covapp).
The source code is subject to the open-source license MIT. You can find the [license terms here](https://github.com/d4l-data4life/covapp/blob/master/LICENSE).
 
**XML description** 
The description of the generated XML can be provided in the following ways:
- As a Microsoft Excel file which contains all information in table form (including IDs, questions, possible answers)
 
We also offer a graphical representation of the [decision tree](https://github.com/d4l-data4life/covapp/tree/master/src/custom/docs) for download.
 
 
**i.s.h.med-specific deliverables** 
The Charité offers implementations that support the development of an interface for reading the QR code, and converting it into a parameterizable medical document (PMD). For more information, see [I work with i.s.h.med, is there anything I must consider?](#i-work-with-ishmed-is-there-anything-i-must-consider)
 
## Can I customize the CovApp?
 
Yes, the CovApp offers different configuration options for the content and the user interface. You can customize the following:
 
- Texts on the start page, disclaimer page, imprint, and privacy policy
 - Logo
 
- Colors
 
You can find a technical description on how to adapt these elements on [GitHub](https://github.com/d4l-data4life/covapp).
 
**IMPORTANT:** Custom changes to the questionnaire or the implementation of the decision tree aren't recommended and aren't officially supported. Any changes could be overwritten by future CovApp updates.
 
## I work with i.s.h.med, is there anything I must consider?
 
The requirements for running the CovApp are independent of your hospital information system (HIS).
For the i.s.h.med HIS, we offer solutions that have been developed together with Charité.
In this case, you can obtain a parameterizable medical document (PMD) in the form of the medical history sheet. You can use this document, together with a transformation implementation that’s also offered, to transfer the XML data directly into the corresponding PMD.
 
If you have questions regarding the implementations and how you can make use of them, please contact [Peter Heumann](mailto:peter.heumann@charite.de) of Charité - Universitätsmedizin Berlin.
 
## Is CovApp backwards-compatible?
 
We ensure backward compatibility by defining the version number of the questionnaire. The version number is also incorporated into the XML structure containing the answers, also encoded as the QR code.
 
These are the rules for changing the questionnaire:
 
- Retain the sequence of questions
 
- Retain the sequence of answers
 
- Retain the technical values of answers, like IDs
 
- Add new questions and new answers only after existing ones
 
- If questions are no longer needed, they aren’t displayed and their related values aren’t transmitted to the XML structure
 
---
 
### About gender-neutral language
 
We try to avoid gender-specific word forms and formulations. As appropriate for context and readability, we may use feminine or masculine word forms to refer to all genders.
 
