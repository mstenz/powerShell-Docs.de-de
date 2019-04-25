---
title: Erstellung der XML-Schema-Datei für einen Management OData-Webdienst | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e83c9d9-6d06-4247-94d9-e3bfd4013b11
caps.latest.revision: 4
ms.openlocfilehash: a806d012097d107b6cc35710b9a93f2b27dd1ace
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080729"
---
# <a name="authoring-the-xml-schema-file-for-a-management-odata-web-service"></a><span data-ttu-id="59d8b-102">Erstellen der XML-Schemadatei für einen Management OData-Webdienst</span><span class="sxs-lookup"><span data-stu-id="59d8b-102">Authoring the XML schema file for a Management OData web service</span></span>

<span data-ttu-id="59d8b-103">Nachdem Sie die Ressourcen definiert Ihren Webdienst wird verfügbar gemacht (finden Sie unter [Erstellung der MOF-Schema-Datei für einen Management OData-Webdienst](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)), ordnen Sie diese Ressourcen die zugrunde liegende Windows PowerShell-Cmdlets, die die unterstützten implementieren. Vorgänge für jede Ressource durch Erstellen einer XML-Datei, die entspricht, der [Ressourcenschema Zuordnung](./resource-mapping-schema.md).</span><span class="sxs-lookup"><span data-stu-id="59d8b-103">After you define the resources your web service will expose (see [Authoring the MOF schema file for a Management OData web service](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)), you map those resources to the underlying Windows PowerShell cmdlets that implement the supported operations for each resource by creating an XML file that conforms to the [Resource Mapping Schema](./resource-mapping-schema.md).</span></span> <span data-ttu-id="59d8b-104">Die XML-Datei gibt auch die URLs, die vom Client verwendet werden, auf die Ressourcen zugreifen.</span><span class="sxs-lookup"><span data-stu-id="59d8b-104">The XML file also specifies the URLs that are used by the client to access the resources.</span></span>

## <a name="mappng-resources-to-urls"></a><span data-ttu-id="59d8b-105">Mappng Ressourcen zu URLs</span><span class="sxs-lookup"><span data-stu-id="59d8b-105">Mappng resources to URLs</span></span>

<span data-ttu-id="59d8b-106">Der erste Teil der XML-Datei ordnet die Ressourcen, die definiert, in der MOF-Schemadatei zu den URLs, die verwendet werden, um darauf zuzugreifen.</span><span class="sxs-lookup"><span data-stu-id="59d8b-106">The first part of the XML file maps the resources defined in the MOF schema file to the URLs that are used to access them.</span></span> <span data-ttu-id="59d8b-107">Das folgende Beispiel zeigt die Zuordnung.</span><span class="sxs-lookup"><span data-stu-id="59d8b-107">The following example shows that mapping.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<ResourceMetadata xmlns="http://schemas.microsoft.com/powershell-web-services/2010/09">
    <SchemaNamespace>PswsTest</SchemaNamespace>
    <ContainerName>PSWSEntityContainer</ContainerName>
    <Resources>
        <Resource>
            <RelativeUrl>Service</RelativeUrl>
            <Class>PswsTest_Service</Class>
        </Resource>
        <Resource>
            <RelativeUrl>Process</RelativeUrl>
            <Class>PswsTest_Process</Class>
        </Resource>
    </Resources>
```

## <a name="mapping-cmdlets-to-crud-operations"></a><span data-ttu-id="59d8b-108">Zuordnen von Cmdlets zu CRUD-Vorgänge</span><span class="sxs-lookup"><span data-stu-id="59d8b-108">Mapping cmdlets to CRUD operations</span></span>

<span data-ttu-id="59d8b-109">Geben Sie dann die Cmdlets, die die CRUD-Vorgänge entsprechen (erstellen, lesen, aktualisieren und löschen) Vorgänge, die die Ressourcen zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="59d8b-109">You then specify the cmdlets that correspond to the CRUD (create, read, update, and delete) operations that the resources support.</span></span> <span data-ttu-id="59d8b-110">Im OData-Management [Ressourcenschema Zuordnung](./resource-mapping-schema.md), die CRUD-Vorgänge wie folgt zugeordnet sind.</span><span class="sxs-lookup"><span data-stu-id="59d8b-110">In the Management OData [Resource Mapping Schema](./resource-mapping-schema.md), the CRUD operations are mapped as follows.</span></span>

|<span data-ttu-id="59d8b-111">CRUD-Befehl</span><span class="sxs-lookup"><span data-stu-id="59d8b-111">CRUD command</span></span>|<span data-ttu-id="59d8b-112">XML-element</span><span class="sxs-lookup"><span data-stu-id="59d8b-112">XML element</span></span>|
|------------------|-----------------|
|<span data-ttu-id="59d8b-113">Erstellen</span><span class="sxs-lookup"><span data-stu-id="59d8b-113">Create</span></span>|<span data-ttu-id="59d8b-114">Erstellen</span><span class="sxs-lookup"><span data-stu-id="59d8b-114">Create</span></span>|
|<span data-ttu-id="59d8b-115">Lesen</span><span class="sxs-lookup"><span data-stu-id="59d8b-115">Read</span></span>|<span data-ttu-id="59d8b-116">Abfrage</span><span class="sxs-lookup"><span data-stu-id="59d8b-116">Query</span></span>|
|<span data-ttu-id="59d8b-117">Update</span><span class="sxs-lookup"><span data-stu-id="59d8b-117">Update</span></span>|<span data-ttu-id="59d8b-118">Update</span><span class="sxs-lookup"><span data-stu-id="59d8b-118">Update</span></span>|
|<span data-ttu-id="59d8b-119">„Löschen“</span><span class="sxs-lookup"><span data-stu-id="59d8b-119">Delete</span></span>|<span data-ttu-id="59d8b-120">„Löschen“</span><span class="sxs-lookup"><span data-stu-id="59d8b-120">Delete</span></span>|

<span data-ttu-id="59d8b-121">Das folgende Beispiel zeigt die Zuordnungen für das Erstellen, Lese- und Aktualisierungsvorgänge für die `Service` Ressource.</span><span class="sxs-lookup"><span data-stu-id="59d8b-121">The following example shows the mappings for the Create, Read, and Update operations on the `Service` resource.</span></span>

```xml
<ClassImplementations>
        <Class>
            <Name>PswsTest_Service</Name>
            <CmdletImplementation>
                <Query>
                    <Cmdlet>Get-Service</Cmdlet>
                        <FieldParameterMap>
                            <Field>
                                <FieldName>ServiceName</FieldName>
                                <ParameterName>Name</ParameterName>
                            </Field>
                        </FieldParameterMap>
                        <ParameterSets>
                            <ParameterSet>
                                <Name>Default</Name>
                                <Parameter><Name>Name</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>ComputerName</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>Include</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>Exclude</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>ErrorVariable</Name></Parameter>
                                <Parameter><Name>WarningVariable</Name></Parameter>
                                <Parameter><Name>OutVariable</Name></Parameter>
                                <Parameter><Name>OutBuffer</Name></Parameter>
                            </ParameterSet>
                            <ParameterSet>
                                <Name>DisplayName</Name>
                                <Parameter><Name>DisplayName</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>ComputerName</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>Include</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>Exclude</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>ErrorVariable</Name></Parameter>
                                <Parameter><Name>WarningVariable</Name></Parameter>
                                <Parameter><Name>OutVariable</Name></Parameter>
                                <Parameter><Name>OutBuffer</Name></Parameter>
                            </ParameterSet>
                            <ParameterSet>
                                <Name>InputObject</Name>
                                <Parameter><Name>ComputerName</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>Include</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>Exclude</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>ErrorVariable</Name></Parameter>
                                <Parameter><Name>WarningVariable</Name></Parameter>
                                <Parameter><Name>OutVariable</Name></Parameter>
                                <Parameter><Name>OutBuffer</Name></Parameter>
                        </ParameterSet>
                    </ParameterSets>
                </Query>
                <Update>
                    <Cmdlet>Set-Service</Cmdlet>
                    <FieldParameterMap>
                        <Field>
                            <FieldName>ServiceName</FieldName>
                            <ParameterName>Name</ParameterName>
                        </Field>
                    </FieldParameterMap>
                    <ParameterSets>
                        <ParameterSet>
                            <Name>Name</Name>
                            <Parameter><Name>ComputerName</Name><Type>System.String[]</Type></Parameter>
                            <Parameter><Name>Name</Name></Parameter>
                            <Parameter><Name>DisplayName</Name></Parameter>
                            <Parameter><Name>Description</Name></Parameter>
                            <Parameter><Name>Status</Name></Parameter>
                            <Parameter><Name>ErrorVariable</Name></Parameter>
                            <Parameter><Name>WarningVariable</Name></Parameter>
                            <Parameter><Name>OutVariable</Name></Parameter>
                            <Parameter><Name>OutBuffer</Name></Parameter>
                        </ParameterSet>
                        <ParameterSet>
                            <Name>InputObject</Name>
                            <Parameter><Name>ComputerName</Name><Type>System.String[]</Type></Parameter>
                            <Parameter><Name>DisplayName</Name></Parameter>
                            <Parameter><Name>Description</Name></Parameter>
                        </ParameterSet>
                    </ParameterSets>
                </Update>
                <Create>
                    <Cmdlet>New-Service</Cmdlet>
                    <FieldParameterMap>
                        <Field>
                            <FieldName>ServiceName</FieldName>
                            <ParameterName>Name</ParameterName>
                        </Field>
                    </FieldParameterMap>
                    <ParameterSets>
                        <ParameterSet>
                            <Name>__AllParameterSets</Name>
                            <Parameter><Name>BinaryPathName</Name></Parameter>
                            <Parameter><Name>Name</Name></Parameter>
                            <Parameter><Name>DisplayName</Name></Parameter>
                            <Parameter><Name>Description</Name></Parameter>
                            <Parameter><Name>DependsOn</Name></Parameter>
                            <Parameter><Name>ErrorVariable</Name></Parameter>
                            <Parameter><Name>WarningVariable</Name></Parameter>
                            <Parameter><Name>OutVariable</Name></Parameter>
                            <Parameter><Name>OutBuffer</Name></Parameter>
                        </ParameterSet>
                    </ParameterSets>
                </Create>
            </CmdletImplementation>
        </Class>
```

## <a name="see-also"></a><span data-ttu-id="59d8b-122">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="59d8b-122">See Also</span></span>

[<span data-ttu-id="59d8b-123">Erstellen der MOF-Schema-Datei für einen Management OData-Webdienst</span><span class="sxs-lookup"><span data-stu-id="59d8b-123">Authoring the MOF schema file for a Management OData web service</span></span>](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

[<span data-ttu-id="59d8b-124">Resource-Mapping-Schema</span><span class="sxs-lookup"><span data-stu-id="59d8b-124">Resource Mapping Schema</span></span>](./resource-mapping-schema.md)

[<span data-ttu-id="59d8b-125">Erstellen einen OData-Web-Management-Dienst</span><span class="sxs-lookup"><span data-stu-id="59d8b-125">Creating a Management OData Web Service</span></span>](./creating-a-management-odata-web-service.md)