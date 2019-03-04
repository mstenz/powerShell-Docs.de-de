---
title: Erstellen einen OData-Web-Management-Dienst | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 06b1b050-0bf7-48f5-ba05-43f489d597c0
caps.latest.revision: 10
ms.openlocfilehash: 476fce9fc087b870bad93a9204a820c5a84df99e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856626"
---
# <a name="creating-a-management-odata-web-service"></a><span data-ttu-id="2a786-102">Erstellen eines Management OData-Webdiensts</span><span class="sxs-lookup"><span data-stu-id="2a786-102">Creating a Management OData Web Service</span></span>

<span data-ttu-id="2a786-103">Management ODATA IIS-Erweiterung ist eine Infrastruktur zum Erstellen einer ASP.NET Web-Dienstendpunkt, der die Verwaltungsdaten, der Zugriff erfolgt über Windows PowerShell-Cmdlets und Skripts, als OData-Web-Service-Entitäten verfügbar macht.</span><span class="sxs-lookup"><span data-stu-id="2a786-103">Management ODATA IIS Extension is an infrastructure for creating an ASP.NET web service end point that exposes your management data, accessed through Windows PowerShell cmdlets and scripts, as OData Web service entities.</span></span> <span data-ttu-id="2a786-104">Dies geschieht, die von OData-Anforderungen verarbeiten und konvertieren sie in einer Windows PowerShell-Aufrufs.</span><span class="sxs-lookup"><span data-stu-id="2a786-104">It does that by processing OData requests and converting them into a Windows PowerShell invocation.</span></span> <span data-ttu-id="2a786-105">Auf dieser Infrastruktur zum Erstellen von Endpunkten, die bestimmte Gruppen von Verwaltungsdaten verfügbar zu machen, können Produktteams erstellen.</span><span class="sxs-lookup"><span data-stu-id="2a786-105">Product teams can build on top of this infrastructure to create endpoints that expose specific sets of management data.</span></span>

<span data-ttu-id="2a786-106">Herunterladen und Installieren der [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) Beispiel.</span><span class="sxs-lookup"><span data-stu-id="2a786-106">Download and install the [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) sample.</span></span> <span data-ttu-id="2a786-107">Führen Sie die Anweisungen zum Bereitstellen des Webdiensts ein.</span><span class="sxs-lookup"><span data-stu-id="2a786-107">Follow the instructions to deploy the web service.</span></span> <span data-ttu-id="2a786-108">Dieser Webdienst macht Dienste und Prozesse, Create, Read, Update und Delete (CRUD) Vorgänge verfügbar.</span><span class="sxs-lookup"><span data-stu-id="2a786-108">This web service exposes Services and Processes through Create, Read, Update, and Delete (CRUD) operations.</span></span> <span data-ttu-id="2a786-109">CRUD-Anforderungen an den Webdienst aufrufen, Windows PowerShell-Befehle, die die angeforderten Vorgänge auszuführen.</span><span class="sxs-lookup"><span data-stu-id="2a786-109">CRUD requests made to the web service invoke  Windows PowerShell commands that perform the requested operations.</span></span> <span data-ttu-id="2a786-110">Eine Zuordnung zwischen der CRUD-Vorgänge und die zugrunde liegenden Windows PowerShell-Befehle wird von zwei Schemadateien "," schema.mof "und" Datei "Schema.xml" implementiert.</span><span class="sxs-lookup"><span data-stu-id="2a786-110">A mapping between the CRUD operations and the underlying Windows PowerShell commands is implemented by two schema files, schema.mof and schema.xml.</span></span> <span data-ttu-id="2a786-111">Die Datei "schema.mof" verwendet die [Distributed Management Task Force](https://www.dmtf.org/) (DMTF) MOF (Managed Object)-Standard.</span><span class="sxs-lookup"><span data-stu-id="2a786-111">The schema.mof file uses the [Distributed Management  Task Force](https://www.dmtf.org/) (DMTF) Managed Object (MOF) standard.</span></span> <span data-ttu-id="2a786-112">Die Datei "schema.xml" verwendet ein XML-Schema, das beschrieben ist [Ressourcenschema Zuordnung](./resource-mapping-schema.md).</span><span class="sxs-lookup"><span data-stu-id="2a786-112">The schema.xml file uses an XML schema that is described in [Resource Mapping Schema](./resource-mapping-schema.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2a786-113">Bevor Sie Management ODATA IIS-Erweiterung für Windows Server 2008 R2 SP1 aktivieren müssen die folgenden Features aktiviert werden.</span><span class="sxs-lookup"><span data-stu-id="2a786-113">Before you enabling Management ODATA IIS Extension on Windows Server 2008 R2 SP1, the following features must be enabled.</span></span>
>
> 1.  <span data-ttu-id="2a786-114">IIS-WebServerRole</span><span class="sxs-lookup"><span data-stu-id="2a786-114">IIS-WebServerRole</span></span>
> 2.  <span data-ttu-id="2a786-115">IIS-WebServer</span><span class="sxs-lookup"><span data-stu-id="2a786-115">IIS-WebServer</span></span>
> 3.  <span data-ttu-id="2a786-116">IIS-HttpTracing</span><span class="sxs-lookup"><span data-stu-id="2a786-116">IIS-HttpTracing</span></span>
> 4.  <span data-ttu-id="2a786-117">IIS-ManagementOData</span><span class="sxs-lookup"><span data-stu-id="2a786-117">IIS-ManagementOData</span></span>

## <a name="steps-for-creating-a-management-odata-web-service"></a><span data-ttu-id="2a786-118">Schritte zum Erstellen eines Management-OData-Webdiensts</span><span class="sxs-lookup"><span data-stu-id="2a786-118">Steps for creating a Management OData web service</span></span>

<span data-ttu-id="2a786-119">Die folgenden Themen beschreiben das Erstellen und Bereitstellen eines Webdiensts Management OData.</span><span class="sxs-lookup"><span data-stu-id="2a786-119">The following topics describe how to create and deploy a Management OData web service.</span></span>

- [<span data-ttu-id="2a786-120">Hinzufügen von Ressourcen zu einem Management OData-Webdienst</span><span class="sxs-lookup"><span data-stu-id="2a786-120">Adding Resources to a Management OData Web Service</span></span>](./adding-resources-to-a-management-odata-web-service.md)

- [<span data-ttu-id="2a786-121">Implementieren von benutzerdefinierten Autorisierung für einen Management OData-Webdienst</span><span class="sxs-lookup"><span data-stu-id="2a786-121">Implementing Custom Authorization for a Management OData web service</span></span>](./implementing-custom-authorization-for-a-management-odata-web-service.md)

- [<span data-ttu-id="2a786-122">Implementieren von SessionConfiguration für einen Management OData-Webdienst</span><span class="sxs-lookup"><span data-stu-id="2a786-122">Implementing SessionConfiguration for a Management OData web service</span></span>](./implementing-sessionconfiguration-for-a-management-odata-web-service.md)

- [<span data-ttu-id="2a786-123">Erstellen der MOF-Schema-Datei für einen Management OData-Webdienst</span><span class="sxs-lookup"><span data-stu-id="2a786-123">Authoring the MOF schema file for a Management OData web service</span></span>](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

- [<span data-ttu-id="2a786-124">Erstellung der XML-Schema-Datei für einen Management OData-Webdienst</span><span class="sxs-lookup"><span data-stu-id="2a786-124">Authoring the XML schema file for a Management OData web service</span></span>](./authoring-the-xml-schema-file-for-a-management-odata-web-service.md)

- [<span data-ttu-id="2a786-125">Erstellen die Datei "Web.config" für einen Management OData-Webdienst</span><span class="sxs-lookup"><span data-stu-id="2a786-125">Authoring the Web.config file for a Management OData web service</span></span>](./authoring-the-web-config-file-for-a-management-odata-web-service.md)

- [<span data-ttu-id="2a786-126">Bereitstellen eines Webdiensts Management OData</span><span class="sxs-lookup"><span data-stu-id="2a786-126">Deploying a Management OData web service</span></span>](./deploying-a-management-odata-web-service.md)

- [<span data-ttu-id="2a786-127">Zuordnen von Management OData-Entitäten</span><span class="sxs-lookup"><span data-stu-id="2a786-127">Associating Management OData Entities</span></span>](./associating-management-odata-entities.md)

## <a name="see-also"></a><span data-ttu-id="2a786-128">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="2a786-128">See Also</span></span>

[<span data-ttu-id="2a786-129">Schemadateien für Management ODATA IIS-Erweiterung</span><span class="sxs-lookup"><span data-stu-id="2a786-129">Management ODATA IIS Extension Schema Files</span></span>](./management-odata-iis-extension-schema-files.md)
