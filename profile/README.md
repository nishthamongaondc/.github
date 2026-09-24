<p align="middle">
<img src="./ONDC-Logo.png" height="150px" width="300px"></p>

# ONDC - Open Network for Digital Commerce

ONDC is an ambitious initiative to democratize digital commerce by creating a decentralized network of buyer apps and seller apps through an interoperable protocol specification.

## Overview

This comprehensive guide is designed to walk you through the process of integrating your digital commerce platform with the Open Network for Digital Commerce (ONDC). By following these steps, you'll enable seamless interoperability with the decentralized network, allowing your platform to leverage the benefits of ONDC.

## Table of Contents

1. [Getting Started](#getting-started)
2. [Quick Start Guide](#quick-start-guide)
3. [The Protocol](#the-protocol)
4. [Subscription Process](#subscription-process)
5. [Signing and Verification](#signing-and-verification)
6. [Subscription Utilities](#subscription-utilities)
7. [Enabled Domains](#enabled-domains)
8. [Reference Applications](#reference-applications)
9. [Product Requirement Documents (PRDs)](#product-requirement-documents)
10. [Gateway and Registry Endpoints](#gateway-and-registry-endpoints)
11. [Network Observability for Production](#network-observability-for-production)
12. [Catalog and Store Rejection](#catalog-and-store-rejection)
13. [City and State codes](#city-and-state-codes)
14. [Technical support](#technical-support)
15. [Workbench](#workbench)
16. [Latest Updates](#latest-updates)
17. [Release Calendar](#release-calendar)

## Getting Started

The [ONDC Web Portal](https://portal.ondc.org/) serves as a self-service platform that streamlines interaction between ONDC and its network participants across their entire lifecycle. "Network player" encompasses network participants, ecosystem partners, and other entities engaged with ONDC. The portal provides access to a range of services for network players, such as self-service onboarding, self-monitored compliance, and self-monitored operations. Creating an account on ONDC Web Portal is mandatory for starting your integration with ONDC.

## Quick Start Guide

[ONDC Integration Guide](https://docs.google.com/presentation/d/1HPRXk3lVYKmyAFcApgukZuwHhIZ_VlqR/edit#slide=id.g27b2e3e34a2_28_199) is a roadmap designed to illuminate key resources and navigate through the integration journey.

# The Protocol

**[Beckn](https://www.youtube.com/watch?v=gefmygtzZR8&t=1s)** is an open protocol that allows local businesses across any industry to be discovered and engaged by any beckn-enabled application. **Beckn protocol** is a collection of open specifications consisting of protocol APIs, message formats, network design and reference architectures to allow any two entities to execute commercial transactions without being on the same platform.

**ONDC** has provided the network extension layer over the Beckn Protocol (base layer). Over the base layer, the network extension layer comprises **model specifications** customised to the ONDC context that have been adopted in order to facilitate transactions over the network. For a detailed understanding of the ONDC network architecture, please refer to our [Tech Briefing Presentation](https://docs.google.com/presentation/d/17mJ_zPjEYPagc5PZuw7FS3Ftcc-Gop4U6536wStRSag/edit#slide=id.g1204a6ff419_0_56) and [Video](https://drive.google.com/file/d/1WuHCc59C45LClpbiIPomPMuTeClRZw7h/view).

### Subscription Process

To enroll in the ONDC network, Network Participants (NP) must be added to the registry. The complete process is documented [here](https://github.com/ONDC-Official/developer-docs/blob/main/registry/Onboarding%20of%20Participants.md). The steps for an NP to onboard onto the ONDC Registry (Staging/Pre Production, Production) are outlined as follows:

#### 1. Staging / Pre-Production Registry
- Obtain whitelisting for the subscriber ID.
- NP Portal invokes Admin APIs
- Keys are not validated upfront
- Direct subscription allowed
- DNS TXT record NOT required

#### 2. Production Registry
Participants will have to:
1. Generate DNS TXT record
2. Host DNS record
3. Portal will call admin subscription API

> **Note:** Steps involving DNS TXT record apply only to the Production environment. Staging/Pre-Prod support direct subscription without DNS validation.

### Signing and Verification

When communicating over HTTP using Beckn APIs, the subscribers need to authenticate themselves to perform transactions with other subscribers. Due to the commercial nature of the transactions, every request/callback pair is considered to be a "contract" between two parties. Therefore, it is imperative that all requests and callbacks are digitally signed by the sender and subsequently verified by the receiver.

The complete process is documented [here](https://github.com/ONDC-Official/developer-docs/blob/main/registry/signing-verification.md).

> [!TIP]
> **Stuck somewhere?**
> Refer to [these frequently asked questions and answers](https://docs.google.com/document/d/15Dpy02lqtcU9tslyMqaI4UtnD2rtwnjAbn1narO0364/edit?usp=sharing)!

## Subscription utilities

- Signing and Verification : This tool is designed to support and aid ONDC Network Participants in constructing their own crypto libraries essential for engaging with the ONDC Network. It encompasses tasks such as key generation, signing, verification, encryption, and decryption.
  - [Java](https://github.com/ONDC-Official/reference-implementations/tree/main/utilities/signing_and_verification/java/ondc-crypto-utility-master)
  - [NodeJS](https://github.com/ONDC-Official/reference-implementations/tree/main/utilities/signing_and_verification/node)
  - [Python](https://github.com/ONDC-Official/reference-implementations/tree/main/utilities/signing_and_verification/python)
  - [GoLang](https://github.com/ONDC-Official/reference-implementations/tree/main/utilities/signing_and_verification/golang)
  - [PHP](https://github.com/ONDC-Official/reference-implementations/tree/main/utilities/signing_and_verification/php)
- [Subscription process](https://github.com/ONDC-Official/reference-implementations/tree/main/utilities/on_subscibe-service) : This tool aids ONDC Network Participants during the subscription process for the registry (Staging, Pre Prod, Prod). It includes the implementation of the /on_subscribe API in both NodeJS and Python.

## Gateway and Registry Endpoints

| **Environment**    | **Endpoint For** | **URL**                                                                                                 |
| ------------------------ | ---------------------- | ------------------------------------------------------------------------------------------------------------- |
| **Pre-Production** | Gateway                | [`https://preprod.gateway.ondc.org/search`](https://preprod.gateway.ondc.org/search)                           |
|                          | Registry               | [`https://preprod.registry.ondc.org/v2.0/lookup`](https://preprod.registry.ondc.org/v2.0/lookup)               |
| **Production**     | Gateway                | [`https://prod.gateway.ondc.org/search`](https://prod.gateway.ondc.org/search)                                 |
|                          | Registry               | [`https://prod.registry.ondc.org/v2.0/lookup`](https://prod.registry.ondc.org/v2.0/lookup)                     |


## Enabled Domains

Network Participants are requested to refer to the list **[here](https://docs.google.com/spreadsheets/d/1Plny0C_4WwffquU6otDhuaVoVkuBd2XuyBKVr5oDDqY/edit?usp=sharing)** for ONDC defined domains and respective codes, across all environments (Staging, Pre-production and Production). The list will be updated as and when required.

_Below are links to the **comprehensive developer guide and model implementations** for the enabled domains._

---

- ### Retail (RET)

This domain encompasses subcategories such as **grocery (RET10), food and beverages (RET11), fashion (RET12), electronics (RET14), home & decor (RET15), beauty and personal care (RET13)**, etc. It facilitates seamless transactions in both **B2C** and **B2B** modes, offering a comprehensive shopping experience for consumers and businesses alike.

> 💡**Latest Updates**
> [Click here to find out the latest updates!](#latest-updates)

#### B2C

| **Domain** | **API Contract / Developer Guide** | **Test Scenarios** | **Mock Server / Sandbox / Reference Application** | **FAQs** | Additional docs |
| ----------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------- |
| **B2C Retail 1.2.5 <br />(Latest)** | -[API Contract v1.2.5](https://docs.google.com/document/d/1E2OyVXh34YNEVOnS4rO3nPVoqTO3RsG2uh-BqnSrqgY) <br /> - [Retail Developer Guide](https://ondc-official.github.io/ONDC-RET-Specifications/) <br /> - *Select version: draft-b2c-1.2.5* <br /> - [Taxonomy](https://docs.google.com/spreadsheets/d/1APAvavF_BNbTA89benAlGtv0GuFvpn2b6XXi4lSdTTw/) | [B2C Test Scenarios](https://docs.google.com/document/d/1w_zncAQzShrTilhv_vaXwB9TNhjzTUZAn_rqQZTeV4U/edit?tab=t.0#heading=h.8vb55kulnjae) | NA | NA | [Click here](https://docs.google.com/spreadsheets/d/1IBKoUypLsV4nTMyo-mLk0xeLYAhvkYbT_dlW1pDO1ys/edit?gid=0#gid=0) |
| **B2C Retail 1.2.0** | -[API Contract v1.2.0](https://docs.google.com/document/d/1brvcltG_DagZ3kGr1ZZQk4hG4tze3zvcxmGV4NMTzr8/edit) <br /> - [Retail Developer Guide](https://ondc-official.github.io/ONDC-RET-Specifications/) <br /> - *Select version: draft-1.x* <br /> - [Taxonomy](https://docs.google.com/spreadsheets/d/1APAvavF_BNbTA89benAlGtv0GuFvpn2b6XXi4lSdTTw/edit?gid=0#gid=0) | [B2C Test Scenarios](https://docs.google.com/spreadsheets/d/1JZV6ZQzXcHUsOwegGtArX3DdIXYIy3gxkhQ00q7kICc/edit#gid=1367601795) | [ONDC Workbench](#workbench) | [B2C Retail FAQs](https://docs.google.com/document/d/1Zb2XzrAUGGdthFqV5tRWxIzQf8XjaW22ev_lqfr3PbI/edit#heading=h.iz6kq888kevy) | |
<!-- | **B2C Exports** | -[Retail Developer Guide](https://ondc-official.github.io/ONDC-RET-Specifications/) <br /> - *Select version: b2c_exports_2.0* <br /> - [Taxonomy](https://drive.google.com/drive/folders/1ZdhZh7wzl4C2452zMYh7wlAvCH-x1b2R) | NA | [Sandbox](https://mock.ondc.org/) | NA | |                                                                                                               | -->

> 💡 It is important to implement **Catalog & Store Rejection Framework** for the **Retail B2C** domain.
> The documentation is available [here](#catalog-and-store-rejection).
<!--
#### B2B

| **Domain** | **API Contract / Developer Guide** | **Test Scenarios** | **Mock Server / Reference Application** | **FAQs** |
| -------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------ | --------------------------------------------- | -------------- |
| **B2B Retail** | -[API Contract v2.0.2](https://github.com/ONDC-Official/ONDC-RET-Specifications/tree/release-2.0.2) <br />- [Retail Developer Guide](https://ondc-official.github.io/ONDC-RET-Specifications/) <br /> - *Select version: release-2.0.2* <br />- [Taxonomy](https://drive.google.com/drive/folders/1ZdhZh7wzl4C2452zMYh7wlAvCH-x1b2R) | [B2B Test Case Scenarios](https://docs.google.com/document/d/10ouiTKLY4dm1KnXCuhFwK38cYd9_aDQ30bklkqnPRkM/edit) | [Sandbox](https://mock.ondc.org/) | NA |
-->

#### eB2B and Inventory Less

| **Domain** | **API Contract / Developer Guide** | **Test Scenarios** | **Mock Server / Reference Application** | **FAQs** |
| -------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------ | --------------------------------------------- | -------------- |
| **eB2B** | -[API Contract v1.2.5](https://docs.google.com/document/d/1CLz6Qn2v_xpTnKOfVOmIY2M_vATW0tiHt6nhORoG_KQ/edit?tab=t.ps0nbzcec4rq#heading=h.u54ymvtsljez) | NA | NA | NA |
| **INVL** | -[API Contract v1.2.5](https://docs.google.com/document/d/11lRZErGXPDHTJcP97NXIT7_VgzTGf4_Ixh_OMJS4eJ4/edit?tab=t.0#heading=h.dodo75ds4n33) | NA | NA | NA |

- ### Logistics

  This domain streamlines the **acquisition of on-network logistics** services, providing logistics buyers with a variety of choices for flexible solutions that suit their specific needs.

| **Domain** | **API Contract / Developer Guide** | **Test Scenarios** | **Mock Server / Sandbox / Reference Application** | **FAQs** |
| ----------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| **B2C Logistics** | -[B2C Logistics v1.2](https://docs.google.com/document/d/1CkfxtqyLbSQccJZyNmf9BSGzJBH13gcLOk_tywV-LBk/edit) | [Test Case Scenarios - B2C Logistics](https://docs.google.com/spreadsheets/d/1JZV6ZQzXcHUsOwegGtArX3DdIXYIy3gxkhQ00q7kICc/edit#gid=1670900093) | NA | [B2C Logistics FAQs](https://docs.google.com/document/d/17gCkt9gpnm8jA71gwEwtPPnvBo6szGeFyruvOaueL3c/edit) |
<!-- | **B2B Logistics for Truck based Delivery** | -[B2B Logistics for Truck based Delivery](https://docs.google.com/document/d/1Z-EJzPv6f80p50pAMGLetUnHzf1dSQ_gVvR4r6O1q88/edit?tab=t.0) | NA | NA | NA |
| **B2B Logistics** | -[B2B Logistics v2.0](https://github.com/ONDC-Official/ONDC-LOG-Specifications) <br /> - [Logistics Developer Guide](https://ondc-official.github.io/ONDC-LOG-Specifications/) <br />- *Select version: draft-2.x* | NA | [Sandbox](https://mock.ondc.org/) | NA | -->

- ### Financial Services (FIS)

  This domain facilitates easy access to a spectrum of financial solutions, covering loans, insurance, and investments.

| **Domain** | **API Contract / Developer Guide** | **Test Scenarios** | **Mock Server / Sandbox / Reference Application** | **FAQs** |
|------------|------------------------------------|--------------------|---------------------------------------------------|----------|
| **Financial Services** | - [PRD](https://drive.google.com/drive/folders/14eHd-AQm-lkyBoh6JZDk1kCuVQxvTMFE)<br>- [Financial Services Developer Guide](https://ondc-official.github.io/ONDC-FIS-Specifications/)<br><br>**Select version:**<br>- For Personal Loan: `release-FIS12-2.0.0`<br>- For Invoice-based Loan: `draft-FIS12-invoice-2.1.0`<br>- For Health Insurance: `draft-health`<br>- For Motor Insurance: `draft-motor`<br>- For Marine Insurance: `draft-marine`<br>- For Investments: `draft-FIS14-enhancements` | Refer to LogSubmission-UI in the developer guide | Refer to Sandbox-UI in the developer guide | [Financial Services FAQs](https://docs.google.com/document/d/1JH9zAK5S3po6GRv6BCdOddxYN6AzjgO57YQE8pVn6lQ/edit) |
| **Gift Cards** | - [API Specifications](https://docs.google.com/document/d/1iTCQd_jI3mRqgSiaeZBvxWL-G_wkE__xxW-Wua8arVE/edit) | NA | NA | NA |

- ### Travel & Tourism/ Mobility (TRV)

  This domain enables easy access to a range of travel-related services, covering On-demand Ride hailing with various transport modes, ticket booking without designated seat, airlines, hotels, intercity bus, entry ticket pass, etc.

| **Domain** | **API Contract / Developer Guide** | **Test Scenarios** | **Mock Server / Sandbox / Reference Application** | **FAQs** |
| ------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------ | ------------------------------------------------------- | -------------------------------------------------------------------------------------------------- |
| **Travel & Tourism / Mobility** | -[PRD](https://drive.google.com/drive/folders/14eHd-AQm-lkyBoh6JZDk1kCuVQxvTMFE) <br />- [Mobility Specifications Developer Guide](https://ondc-official.github.io/mobility-specification/) <br />**Select version:** <br />- For On-demand Ride Hailing: `release-TRV10-2.0.1` <br />- For Unreserved Ticket Booking (Metro/Intracity Bus): `release-TRV11-2.0.0` <br />- For Intercity Bus Ticket Booking: `draft-TRV12-intercity` <br />- For Airlines Booking: `draft-TRV12-airline` <br />- For Hotel Booking: `draft-TRV13-hotel` <br /> - For Unreserved Entry Pass (Heritage Sites, Museums, Concerts, etc.): `draft-TRV14-2.0.0` | Refer to LogSubmission-UI in the developer guide | Refer to Sandbox-UI in the developer guide | [Mobility FAQs](https://docs.google.com/document/d/138tJ_zzt5yIi46b3WsY2UeBU1rJeGXZTG4ivheT87CM/edit) |

<!-- - ### Services (SRV)

  This domain empowers individuals to effortlessly access a diverse array of services, covering skilled services like **home painting, chefs and consulations, auction of agricultural outputs, leasing farming machinery and tools, soil testing, assaying services, lab testing, subscriptions**, etc.

| **Domain** | **API Contract / Developer Guide** | **Test Scenarios** | **Mock Server / Sandbox / Reference Application** | **FAQs** |
| ------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------ | ------------------------------------------------------- | -------------------------------------------------------------------------------------------------- |
| **Services** | -[PRD](https://drive.google.com/drive/folders/14eHd-AQm-lkyBoh6JZDk1kCuVQxvTMFE) <br />- [v2.0.0](https://github.com/ONDC-Official/ONDC-SRV-Specifications) <br />- [Services Developer Guide](https://ondc-official.github.io/ONDC-SRV-Specifications/#) **Select version:** <br />- For Skilled Services: `release-services` <br />- For Auction of Agricultural Outputs: `draft-agri_bids_and_auction`- For Equipment Hiring (Leasing Farming Machinery and Tools): `draft-agri_equipment` <br />- For Soil Testing and Assaying Service: `draft-agri_services` <br />- For Healthcare Services (Lab Test Booking): `draft-healthcare` <br />- For Weighment Services: `draft-weighment` <br />- For Warehouse as a Service: `draft-warehouse` | NA | [Sandbox](https://mock.ondc.org/) | [Services FAQs](https://docs.google.com/document/d/1e_nGOnYb4ld1kxjhOHOsXXOms96aDd6txD8Wh2wl6tk/edit) |

- ### Media, Entertainment, Content (MEC)

| **Domain** | **API Contract/ Developer Guide** | **Test Scenarios** | **Mock Server/ Sandbox/ Reference Application** | **FAQs** |
| --------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------ | ----------------------------------------------------- | -------------- |
| **Media, Entertainment, Content (MEC)** | -[PRD](https://drive.google.com/drive/folders/14eHd-AQm-lkyBoh6JZDk1kCuVQxvTMFE) <br />- [v2.0.0](https://github.com/ONDC-Official/ONDC-MEC-Specifications/tree/draft-print_media) <br /> - [Media, Entertainment, Content Developer Guide](https://ondc-official.github.io/ONDC-MEC-Specifications/) | NA | NA | NA | -->

- ### Ancillary Services

  - **Issue & Grievance Management (IGM)** within the ONDC Network serves as a critical mechanism for resolving disputes and concerns among Network Participants (NPs).
  - **Reconciliation and Settlement Framework (RSF)** plays a pivotal role in maintaining a comprehensive trail of settlements between Network Participants.
 <!--  - **Rating**
  - **Score** -->

| **Domain** | **API Contract/ Developer Guide** | **Test Scenarios** | **Sandbox** | **Mock Server/ Reference Application** | **FAQs** |
| ---------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- |
| **IGM** | [Developer Guide v2.0.0](https://ondc-official.github.io/ONDC-NTS-Specifications/) `select version: draft-igm-2.0.0` <br />-[PRD](https://docs.google.com/document/d/1CBTOuFP4o6KqwYVPlN6H9ArUvygMjFiII-gSv4WXk4s/edit?usp=sharing) | [Test case scenarios - IGM](https://docs.google.com/document/d/1SGTCSzxNPtBvBpvtYf0I-MUxQCrYT_I-/edit?usp=sharing&ouid=100595989766867836454&rtpof=true&sd=true) | WIP | [Mock Server Reference](https://docs.google.com/document/d/1SGTCSzxNPtBvBpvtYf0I-MUxQCrYT_I-/edit?usp=sharing&ouid=100595989766867836454&rtpof=true&sd=true) | [IGM FAQs](https://docs.google.com/document/d/1-NULesI1Z6GQ9y4Z0loGEG5yfunX5u9woON-qxYH6w0/edit) |
<!-- | **RSF** | [Developer Guide v2.0.0](https://ondc-official.github.io/ONDC-NTS-Specifications/) `select version: draft-rsf-2.0.0` <br />-[PRD](https://docs.google.com/document/d/1Pj7e1MuObQeLczx_palbcliUPTkMRYA76esjrfAMT14/edit?usp=sharing) | [Test case scenarios - RSF 2.0](https://docs.google.com/document/d/1rHmQ8joTsT2HDmZdXhPlUKy5QSrJiQuEkTAjLDcNVoA/edit?usp=sharing) | [Refer to this document for testing](https://github.com/ONDC-Official/log-validation-utility) | [Mock Server Reference](https://docs.google.com/document/d/1rHmQ8joTsT2HDmZdXhPlUKy5QSrJiQuEkTAjLDcNVoA/edit?usp=sharing) | [RSF FAQs](https://docs.google.com/document/d/19TCvuwwvOklt9Ev-SKkcXRAdvh6Qyhl9tI1Z_YavHMk/edit) |
| **Rating** | [v1.2.0](https://docs.google.com/document/d/1VaafY8t47hjpoW6tdezGsPwLwxxaAaGc/edit) | NA | NA | NA | NA |
| **Score** | [v1.2.0](https://docs.google.com/document/d/126O1wFdA-IuwojiAuLzdpN36vjWfQg9KOA2zRd9-zTY/edit#heading=h.bifjra7hj5b0) | NA | NA | NA | NA |

- ### Open Network for Education and Skilling Transformation (ONEST)

| **Domain** | **API Contract/ Developer Guide** | **Test Scenarios** | **Mock Server/ Sandbox/ Reference Application** | **FAQs** |
| -------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------ | ----------------------------------------------------- | -------------- |
| **Work Opportunities (ONEST10)** | -[PRD](https://docs.google.com/document/d/1VydDAqtzjj1jDrJzX4hwZSlYyJsA_bSOJIKYTWxNSpQ/edit?tab=t.0#heading=h.gjdgxs) <br />- [v2.0.0](https://github.com/ONDC-Official/ONDC-ONEST-Specifications/tree/draft-ONEST10-2.0.0) <br /> - [Work Opportunities Developer Guide](https://ondc-official.github.io/ONDC-ONEST-Specifications) | Refer to LogSubmission-UI in the developer guide | Refer to Sandbox-UI in the developer guide | NA |
-->

## Reference Applications

Network Participants can validate, test, and debug their ONDC API integrations using the **[ONDC Workbench](#workbench)**, the self-service protocol compliance platform.

**Key Features**

- Sandbox environment for testing both positive and negative scenarios.
- Direct submission of logs to ONDC for verification.
- Supports scalability, security, and compliance testing.

See the [Workbench](#workbench) section for schema validation, scenario testing, and log submission. Network Participants must complete end-to-end testing before going live.

## Product Requirement Documents

- PRDs for different use cases are available [here](https://drive.google.com/drive/folders/14eHd-AQm-lkyBoh6JZDk1kCuVQxvTMFE).

## Catalog and Store Rejection

Refer to the following document for the Catalog and Store Rejection Report - Framework.

> [Catalog Rejection](https://docs.google.com/document/d/1y_kBhwSwyN2D39VucTtqEQdp7WSEGYMg/edit)

> [Swagger Document](https://ondc-official.github.io/catalog-rejection/)

## City and State codes

Refer to the following document for the City-Pincode mapping and State codes

> [City and State Codes](https://docs.google.com/spreadsheets/d/12A_B-nDtvxyFh_FWDfp85ss2qpb65kZ7/edit?usp=sharing&ouid=106289085575597209813&rtpof=true&sd=true)

## Network Observability for Production

Refer to the following document for the Network Observability API Schema Requirements for the Production Environment.

> [Network Observability](https://docs.google.com/document/d/1dP_QTLnI1T89mCcJVfbB0S1ZJ7Ej5y3o1Sr3nplserY/edit#heading=h.blfeo5vd64pc)


## Technical support
1. **Ticket Support**
   Tickets can be raised through the following channels:
   - **Email:** [ONDC Team](mailto:team@ondc.org)
   - **Support Portal:**
     - Registered organisations – Raise your queries [here](https://portal.ondc.org/admin). You may also refer to this video for guidance on [how to submit issues](https://drive.google.com/file/d/1VsZheSdC_hwuliRgptaoiNAlxuWVgeWr/view).
     - Unregistered users – Raise your queries [here](https://portal.ondc.org/guest-support-request).

2. **FAQ Support** : [FAQs](https://ondc-official.github.io/ONDC-FAQs/)

## Workbench

**Overview**

The ONDC Workbench is a self-service platform designed to accelerate and simplify the process of protocol compliance for network participants. It provides a suite of automated tools to validate, test, and debug your ONDC API integrations before going live.

**Key Features**

- **Schema Validation:** Instantly validate your API payloads against ONDC specifications, highlighting inconsistencies and missing fields to ensure strict protocol adherence.
- **Scenario Testing:** Simulate end-to-end transactions across various ONDC protocol flows, helping you verify your implementation against real-world scenarios and edge cases.
- **Comprehensive Reporting:** Receive detailed feedback and actionable reports to quickly identify and resolve issues.
- **Continuous Updates:** The tool is regularly updated to reflect the latest ONDC protocol changes and best practices.
- **Experience different scenarios:** Explore and test a variety of protocol flows.
- **Simulate and validate payloads:** Ensure your payloads meet ONDC requirements.
- **Debug API interactions:** Troubleshoot and refine your integration with real-time feedback.
- **Get support as you develop:** Access help and resources throughout your development journey.

**Access**

- **Workbench Portal:** [https://workbench.ondc.tech/home](https://workbench.ondc.tech/home)

**Support & Feedback**
- **Email:** [team@ondc.org](mailto:team@ondc.org)
- **Raise an Issue:** [ONDC Workbench Issues](https://github.com/ONDC-Official/automation-framework/issues)
- **Daily Community Call:** Join for queries or clarifications, 10:00 – 11:00 AM IST: [Google Meet Link](https://meet.google.com/bpo-pwwh-fja)

## Latest Updates

| Domain  | Item                    | Date       | Link                                                                                                                                                                                                                |
| ------- | ----------------------- | ---------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| General | Workbench Tool Launched | 09/07/2025 | [Workbench](https://workbench.ondc.tech/home) – Schema Validation & Scenario Testing tools now available. Feedback: team@ondc.org or [GitHub Issues](https://github.com/ONDC-Official/automation-framework/issues) |
| Retail  | [Updated] Reason Code   | 12/06/2025 | [Reason codes](https://docs.google.com/spreadsheets/d/1_qAtG6Bu2we3AP6OpXr4GVP3X-32v2xNRNSYQhhR6kA/edit?gid=814799303#gid=814799303)                                                                                   |
| Retail  | Force Cancellation      | 12/06/2025 | [API Contract](https://docs.google.com/document/d/1E2OyVXh34YNEVOnS4rO3nPVoqTO3RsG2uh-BqnSrqgY/edit?tab=t.sikbh4ktl6u5#heading=h.qjm7bixfaobb)                                                                         |
| Retail  | Feature List            | 12/06/2025 | [Feature List](https://docs.google.com/spreadsheets/d/1tINL6xyYXG1mKjvnO9Mtzr_MRMHiRzTVqJbyyQyHEgQ/edit?gid=147707807#gid=147707807)                                                                                   |
| Retail  | Lookup API Update       | 12/06/2025 | [FAQ Draft v0.2](https://docs.google.com/document/d/1Tj_tcex65WjLKflt9a8cxp2L4kNFLTpbgXHk5J2EpaY/edit?tab=t.0#heading=h.hzrjpor3fbt1)                                                                                  |
| Retail  | New Contract - eB2B     | 26/02/2026 | [API Contract v1.2.5](https://docs.google.com/document/d/1CLz6Qn2v_xpTnKOfVOmIY2M_vATW0tiHt6nhORoG_KQ/edit?tab=t.ps0nbzcec4rq#heading=h.u54ymvtsljez)                                                                  |
| Retail  | New Contract - Inventory Less | 26/02/2026 | [API Contract v1.2.5](https://docs.google.com/document/d/11lRZErGXPDHTJcP97NXIT7_VgzTGf4_Ixh_OMJS4eJ4/edit?tab=t.0#heading=h.dodo75ds4n33)                                                                             |

### Stay Informed About Product and Feature Updates

To receive notifications regarding product updates and new feature releases, please provide your email address and domain [here](https://docs.google.com/forms/d/e/1FAIpQLSci6dEcPwf2drUnb3yWt4aHLmfrkzE3GDMv8wvbyNMh8_3mnw/viewform).

## Release Calendar

Minor releases (e.g., bug fixes) will be scheduled around the 15th of each month, while major releases (including new features and patches) will take place at the end of the month.
