---
title: Erstellen eines odata-Webdiensts für die Verwaltung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 06b1b050-0bf7-48f5-ba05-43f489d597c0
caps.latest.revision: 10
ms.openlocfilehash: f903c99300a34c0dfbed598738e96142588d69d9
ms.sourcegitcommit: 17d798a041851382b406ed789097843faf37692d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/20/2020
ms.locfileid: "83691490"
---
# <a name="creating-a-management-odata-web-service"></a><span data-ttu-id="d01d2-102">Erstellen eines Management OData-Webdiensts</span><span class="sxs-lookup"><span data-stu-id="d01d2-102">Creating a Management OData Web Service</span></span>

<span data-ttu-id="d01d2-103">Die IIS-Erweiterung für die Verwaltung von odata ist eine Infrastruktur zum Erstellen eines ASP.NET-Webdienst-Endpunkts, der Ihre Verwaltungsdaten verfügbar macht. der Zugriff erfolgt über Windows PowerShell-Cmdlets und-Skripts als odata-Webdienst</span><span class="sxs-lookup"><span data-stu-id="d01d2-103">Management ODATA IIS Extension is an infrastructure for creating an ASP.NET web service end point that exposes your management data, accessed through Windows PowerShell cmdlets and scripts, as OData Web service entities.</span></span> <span data-ttu-id="d01d2-104">Dies geschieht, indem odata-Anforderungen verarbeitet und in einen Windows PowerShell-Aufruf umgewandelt werden.</span><span class="sxs-lookup"><span data-stu-id="d01d2-104">It does that by processing OData requests and converting them into a Windows PowerShell invocation.</span></span> <span data-ttu-id="d01d2-105">Produktteams können auf dieser Infrastruktur aufbauen, um Endpunkte zu erstellen, die bestimmte Sätze von Verwaltungsdaten verfügbar machen.</span><span class="sxs-lookup"><span data-stu-id="d01d2-105">Product teams can build on top of this infrastructure to create endpoints that expose specific sets of management data.</span></span>

<span data-ttu-id="d01d2-106">Laden Sie das Beispiel [ptauscht-rolebasedplugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) herunter, und installieren Sie es.</span><span class="sxs-lookup"><span data-stu-id="d01d2-106">Download and install the [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) sample.</span></span> <span data-ttu-id="d01d2-107">Befolgen Sie die Anweisungen zum Bereitstellen des Webdiensts.</span><span class="sxs-lookup"><span data-stu-id="d01d2-107">Follow the instructions to deploy the web service.</span></span> <span data-ttu-id="d01d2-108">Dieser Webdienst macht Dienste und Prozesse über Vorgänge zum Erstellen, lesen, aktualisieren und löschen (CRUD) verfügbar.</span><span class="sxs-lookup"><span data-stu-id="d01d2-108">This web service exposes Services and Processes through Create, Read, Update, and Delete (CRUD) operations.</span></span> <span data-ttu-id="d01d2-109">CRUD-Anforderungen, die an den Webdienst gerichtet werden, rufen Windows PowerShell-Befehle auf, die die angeforderten Vorgänge ausführen.</span><span class="sxs-lookup"><span data-stu-id="d01d2-109">CRUD requests made to the web service invoke  Windows PowerShell commands that perform the requested operations.</span></span> <span data-ttu-id="d01d2-110">Eine Zuordnung zwischen den CRUD-Vorgängen und den zugrunde liegenden Windows PowerShell-Befehlen wird durch zwei Schema Dateien ("Schema. mof" und "Schema. xml") implementiert.</span><span class="sxs-lookup"><span data-stu-id="d01d2-110">A mapping between the CRUD operations and the underlying Windows PowerShell commands is implemented by two schema files, schema.mof and schema.xml.</span></span> <span data-ttu-id="d01d2-111">Die Datei "Schema. mof" [verwendet den](https://www.dmtf.org/) MOF-Standard (DMTF) Managed Object (DMTF).</span><span class="sxs-lookup"><span data-stu-id="d01d2-111">The schema.mof file uses the [Distributed Management  Task Force](https://www.dmtf.org/) (DMTF) Managed Object (MOF) standard.</span></span> <span data-ttu-id="d01d2-112">Die Datei "Schema. xml" verwendet ein XML-Schema, das unter [Ressourcen Zuordnung Schema](./resource-mapping-schema.md)beschrieben wird.</span><span class="sxs-lookup"><span data-stu-id="d01d2-112">The schema.xml file uses an XML schema that is described in [Resource Mapping Schema](./resource-mapping-schema.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d01d2-113">Bevor Sie die Verwaltungs-odata-IIS-Erweiterung unter Windows Server 2008 R2 SP1 aktivieren, müssen die folgenden Funktionen aktiviert werden.</span><span class="sxs-lookup"><span data-stu-id="d01d2-113">Before you enabling Management ODATA IIS Extension on Windows Server 2008 R2 SP1, the following features must be enabled.</span></span>
>
> 1. <span data-ttu-id="d01d2-114">IIS-WebServerRole</span><span class="sxs-lookup"><span data-stu-id="d01d2-114">IIS-WebServerRole</span></span>
> 2. <span data-ttu-id="d01d2-115">IIS-WebServer</span><span class="sxs-lookup"><span data-stu-id="d01d2-115">IIS-WebServer</span></span>
> 3. <span data-ttu-id="d01d2-116">IIS-HttpTracing</span><span class="sxs-lookup"><span data-stu-id="d01d2-116">IIS-HttpTracing</span></span>
> 4. <span data-ttu-id="d01d2-117">IIS-managementodata</span><span class="sxs-lookup"><span data-stu-id="d01d2-117">IIS-ManagementOData</span></span>

## <a name="steps-for-creating-a-management-odata-web-service"></a><span data-ttu-id="d01d2-118">Schritte zum Erstellen eines odata-Webdiensts für die Verwaltung</span><span class="sxs-lookup"><span data-stu-id="d01d2-118">Steps for creating a Management OData web service</span></span>

<span data-ttu-id="d01d2-119">In den folgenden Themen wird beschrieben, wie Sie einen odata-Webdienst für die Verwaltung erstellen und bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="d01d2-119">The following topics describe how to create and deploy a Management OData web service.</span></span>

- [<span data-ttu-id="d01d2-120">Hinzufügen von Ressourcen zu einem Management OData-Webdienst</span><span class="sxs-lookup"><span data-stu-id="d01d2-120">Adding Resources to a Management OData Web Service</span></span>](./adding-resources-to-a-management-odata-web-service.md)

- [<span data-ttu-id="d01d2-121">Implementieren der benutzerdefinierten Autorisierung für einen Management OData-Webdienst</span><span class="sxs-lookup"><span data-stu-id="d01d2-121">Implementing Custom Authorization for a Management OData web service</span></span>](./implementing-custom-authorization-for-a-management-odata-web-service.md)

- [<span data-ttu-id="d01d2-122">Implementieren von SessionConfiguration für einen Management OData-Webdienst</span><span class="sxs-lookup"><span data-stu-id="d01d2-122">Implementing SessionConfiguration for a Management OData web service</span></span>](./implementing-sessionconfiguration-for-a-management-odata-web-service.md)

- [<span data-ttu-id="d01d2-123">Erstellen der MOF-Schemadatei für einen Management OData-Webdienst</span><span class="sxs-lookup"><span data-stu-id="d01d2-123">Authoring the MOF schema file for a Management OData web service</span></span>](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

- [<span data-ttu-id="d01d2-124">Erstellen der XML-Schemadatei für einen Management OData-Webdienst</span><span class="sxs-lookup"><span data-stu-id="d01d2-124">Authoring the XML schema file for a Management OData web service</span></span>](./authoring-the-xml-schema-file-for-a-management-odata-web-service.md)

- [<span data-ttu-id="d01d2-125">Erstellen der Web.config-Schemadatei für einen Management OData-Webdienst</span><span class="sxs-lookup"><span data-stu-id="d01d2-125">Authoring the Web.config file for a Management OData web service</span></span>](./authoring-the-web-config-file-for-a-management-odata-web-service.md)

- [<span data-ttu-id="d01d2-126">Bereitstellen eines Management OData-Webdiensts</span><span class="sxs-lookup"><span data-stu-id="d01d2-126">Deploying a Management OData web service</span></span>](./deploying-a-management-odata-web-service.md)

- [<span data-ttu-id="d01d2-127">Zuordnen von Management OData-Entitäten</span><span class="sxs-lookup"><span data-stu-id="d01d2-127">Associating Management OData Entities</span></span>](./associating-management-odata-entities.md)

## <a name="see-also"></a><span data-ttu-id="d01d2-128">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="d01d2-128">See Also</span></span>

[<span data-ttu-id="d01d2-129">Verwaltungs-odata-IIS-Erweiterungs Schema Dateien</span><span class="sxs-lookup"><span data-stu-id="d01d2-129">Management ODATA IIS Extension Schema Files</span></span>](./management-odata-iis-extension-schema-files.md)
