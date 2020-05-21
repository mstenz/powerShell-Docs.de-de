---
title: Erstellen der XML-Schema Datei für einen odata-Webdienst für die Verwaltung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e83c9d9-6d06-4247-94d9-e3bfd4013b11
caps.latest.revision: 4
ms.openlocfilehash: 7ccdeeb2833b79cabc7c77d1a400e0c9132b2dcd
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83561463"
---
# <a name="authoring-the-xml-schema-file-for-a-management-odata-web-service"></a><span data-ttu-id="83d02-102">Erstellen der XML-Schemadatei für einen Management OData-Webdienst</span><span class="sxs-lookup"><span data-stu-id="83d02-102">Authoring the XML schema file for a Management OData web service</span></span>

<span data-ttu-id="83d02-103">Nachdem Sie die Ressourcen definiert haben, die vom Webdienst verfügbar gemacht werden (siehe [Erstellen der MOF-Schema Datei für einen Management odata-Webdienst](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)), ordnen Sie diese Ressourcen den zugrunde liegenden Windows PowerShell-Cmdlets zu, die die unterstützten Vorgänge für jede Ressource implementieren, indem Sie eine XML-Datei erstellen, die dem Ressourcen Zuordnungs [Schema](./resource-mapping-schema.md)entspricht.</span><span class="sxs-lookup"><span data-stu-id="83d02-103">After you define the resources your web service will expose (see [Authoring the MOF schema file for a Management OData web service](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)), you map those resources to the underlying Windows PowerShell cmdlets that implement the supported operations for each resource by creating an XML file that conforms to the [Resource Mapping Schema](./resource-mapping-schema.md).</span></span> <span data-ttu-id="83d02-104">Die XML-Datei gibt auch die URLs an, die vom Client für den Zugriff auf die Ressourcen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="83d02-104">The XML file also specifies the URLs that are used by the client to access the resources.</span></span>

## <a name="mappng-resources-to-urls"></a><span data-ttu-id="83d02-105">Mappng Ressourcen an URLs</span><span class="sxs-lookup"><span data-stu-id="83d02-105">Mappng resources to URLs</span></span>

<span data-ttu-id="83d02-106">Der erste Teil der XML-Datei ordnet die in der MOF-Schema Datei definierten Ressourcen den URLs zu, die für den Zugriff verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="83d02-106">The first part of the XML file maps the resources defined in the MOF schema file to the URLs that are used to access them.</span></span> <span data-ttu-id="83d02-107">Das folgende Beispiel zeigt die Zuordnung.</span><span class="sxs-lookup"><span data-stu-id="83d02-107">The following example shows that mapping.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<ResourceMetadata xmlns="https://schemas.microsoft.com/powershell-web-services/2010/09">
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

## <a name="mapping-cmdlets-to-crud-operations"></a><span data-ttu-id="83d02-108">Mapping von Cmdlets zu CRUD-Vorgängen</span><span class="sxs-lookup"><span data-stu-id="83d02-108">Mapping cmdlets to CRUD operations</span></span>

<span data-ttu-id="83d02-109">Anschließend geben Sie die Cmdlets an, die den CRUD-Vorgängen (erstellen, lesen, aktualisieren und löschen) entsprechen, die von den Ressourcen unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="83d02-109">You then specify the cmdlets that correspond to the CRUD (create, read, update, and delete) operations that the resources support.</span></span> <span data-ttu-id="83d02-110">Im Management odata- [Ressourcen Zuordnungsschema](./resource-mapping-schema.md)werden die CRUD-Vorgänge wie folgt zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="83d02-110">In the Management OData [Resource Mapping Schema](./resource-mapping-schema.md), the CRUD operations are mapped as follows.</span></span>

|<span data-ttu-id="83d02-111">CRUD-Befehl</span><span class="sxs-lookup"><span data-stu-id="83d02-111">CRUD command</span></span>|<span data-ttu-id="83d02-112">XML-Element</span><span class="sxs-lookup"><span data-stu-id="83d02-112">XML element</span></span>|
|------------------|-----------------|
|<span data-ttu-id="83d02-113">Erstellen</span><span class="sxs-lookup"><span data-stu-id="83d02-113">Create</span></span>|<span data-ttu-id="83d02-114">Erstellen</span><span class="sxs-lookup"><span data-stu-id="83d02-114">Create</span></span>|
|<span data-ttu-id="83d02-115">Lesen</span><span class="sxs-lookup"><span data-stu-id="83d02-115">Read</span></span>|<span data-ttu-id="83d02-116">Abfrage</span><span class="sxs-lookup"><span data-stu-id="83d02-116">Query</span></span>|
|<span data-ttu-id="83d02-117">Update</span><span class="sxs-lookup"><span data-stu-id="83d02-117">Update</span></span>|<span data-ttu-id="83d02-118">Aktualisieren</span><span class="sxs-lookup"><span data-stu-id="83d02-118">Update</span></span>|
|<span data-ttu-id="83d02-119">Löschen</span><span class="sxs-lookup"><span data-stu-id="83d02-119">Delete</span></span>|<span data-ttu-id="83d02-120">Löschen</span><span class="sxs-lookup"><span data-stu-id="83d02-120">Delete</span></span>|

<span data-ttu-id="83d02-121">Das folgende Beispiel zeigt die Zuordnungen für die Erstellungs-, Lese-und Aktualisierungs Vorgänge für die `Service` Ressource.</span><span class="sxs-lookup"><span data-stu-id="83d02-121">The following example shows the mappings for the Create, Read, and Update operations on the `Service` resource.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="83d02-122">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="83d02-122">See Also</span></span>

[<span data-ttu-id="83d02-123">Erstellen der MOF-Schemadatei für einen Management OData-Webdienst</span><span class="sxs-lookup"><span data-stu-id="83d02-123">Authoring the MOF schema file for a Management OData web service</span></span>](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

[<span data-ttu-id="83d02-124">Schema für Ressourcenzuordnung</span><span class="sxs-lookup"><span data-stu-id="83d02-124">Resource Mapping Schema</span></span>](./resource-mapping-schema.md)

[<span data-ttu-id="83d02-125">Erstellen eines Management OData-Webdiensts</span><span class="sxs-lookup"><span data-stu-id="83d02-125">Creating a Management OData Web Service</span></span>](./creating-a-management-odata-web-service.md)
