Document Author: Robert Mayer

Document Number: EF-INT-002, Rev. B

Release Date: 15 Dec 2016

Minimum Mandatory Revision: A

Revision History:

| Rev | Date        | Author   | Description                 | Mandatory |
|-----|-------------|----------|-----------------------------|-----------|
| -   | 10 Aug 2016 | R. Mayer | Initial Release, See AA-364 |           |
| A   | 16 Sep 2016 | R. Mayer | See AA-436                  | \*        |
| B   | 15 Dec 2016 | R. Mayer | See AA-634                  |           |

General
=======

The Building Automation Communication subsystem translates common communication requests from a standard, interoperable format (JSON or XML) to the vendor-specific BAS communication format (e.g. BACnet, oBIX, etc.). Each communication format is implemented via a plug-in style architecture. This document provides an overview of the services offered by the BAC framework. The services are offered exclusively as message-based exchanges, making them interoperable with a variety of endpoints.

The intended audience for this document are developers creating stack applications intending to operate internally to the Enterprise framework (applications to reside either on the cloud stack or on the gateway devices themselves). The capabilities are “internal only” – external-facing capability is provided via another related component.

Location
========

This component resides on the local gateway devices; services on the local gateways are accessible directly to other services residing on the local gateway, while cloud stack callers must address the local gateway node for the applicable instance of the component.

Reference Documents
===================

-   Refer to EF-INT-001 “Use of Messaging on the Enterprise Framework” for details about various communication styles and instructions on use of messaging to communicate.

-   Refer to EF-ARC-001 “Enterprise Framework Architecture Overview” for details about services located on the cloud and gateway service layers.

Services
========

ListBasNetworkFormats
---------------------

Description: returns a list of available BAS communication formats loaded into the specific operating instance of the service.

Type: request-response

Initial Release: 1.0; Minor updates in: 1.1

Input: (no parameters)

Output: a list of BAS network formats supported/loaded by the gateway device in question (see diagram below)

![ListBasNetworkFormats Diagram](/media/image1.emf)

CreateBasNetworkConnection
--------------------------

Description: creates and returns a new network connection using the supplied BAS plugin name. Configuration parameters are supplied (with default values) for further configuration of the connection.

Type: request-response

Initial Release: 1.0; Minor updates in: 1.1, 1.3, 2.0

Input: the type of network connection to create (the name of the plugin; use ListBasNetworkFormats to get acceptable input names)

Output: a new BasNetworkConnection object with default configuration parameters supplied

![CreateBasNetworkConnection Diagram](/media/image2.emf)
