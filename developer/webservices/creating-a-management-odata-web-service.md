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
# <a name="creating-a-management-odata-web-service"></a>Erstellen eines Management OData-Webdiensts

Management ODATA IIS-Erweiterung ist eine Infrastruktur zum Erstellen einer ASP.NET Web-Dienstendpunkt, der die Verwaltungsdaten, der Zugriff erfolgt über Windows PowerShell-Cmdlets und Skripts, als OData-Web-Service-Entitäten verfügbar macht. Dies geschieht, die von OData-Anforderungen verarbeiten und konvertieren sie in einer Windows PowerShell-Aufrufs. Auf dieser Infrastruktur zum Erstellen von Endpunkten, die bestimmte Gruppen von Verwaltungsdaten verfügbar zu machen, können Produktteams erstellen.

Herunterladen und Installieren der [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) Beispiel. Führen Sie die Anweisungen zum Bereitstellen des Webdiensts ein. Dieser Webdienst macht Dienste und Prozesse, Create, Read, Update und Delete (CRUD) Vorgänge verfügbar. CRUD-Anforderungen an den Webdienst aufrufen, Windows PowerShell-Befehle, die die angeforderten Vorgänge auszuführen. Eine Zuordnung zwischen der CRUD-Vorgänge und die zugrunde liegenden Windows PowerShell-Befehle wird von zwei Schemadateien "," schema.mof "und" Datei "Schema.xml" implementiert. Die Datei "schema.mof" verwendet die [Distributed Management Task Force](https://www.dmtf.org/) (DMTF) MOF (Managed Object)-Standard. Die Datei "schema.xml" verwendet ein XML-Schema, das beschrieben ist [Ressourcenschema Zuordnung](./resource-mapping-schema.md).

> [!IMPORTANT]
> Bevor Sie Management ODATA IIS-Erweiterung für Windows Server 2008 R2 SP1 aktivieren müssen die folgenden Features aktiviert werden.
>
> 1.  IIS-WebServerRole
> 2.  IIS-WebServer
> 3.  IIS-HttpTracing
> 4.  IIS-ManagementOData

## <a name="steps-for-creating-a-management-odata-web-service"></a>Schritte zum Erstellen eines Management-OData-Webdiensts

Die folgenden Themen beschreiben das Erstellen und Bereitstellen eines Webdiensts Management OData.

- [Hinzufügen von Ressourcen zu einem Management OData-Webdienst](./adding-resources-to-a-management-odata-web-service.md)

- [Implementieren von benutzerdefinierten Autorisierung für einen Management OData-Webdienst](./implementing-custom-authorization-for-a-management-odata-web-service.md)

- [Implementieren von SessionConfiguration für einen Management OData-Webdienst](./implementing-sessionconfiguration-for-a-management-odata-web-service.md)

- [Erstellen der MOF-Schema-Datei für einen Management OData-Webdienst](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

- [Erstellung der XML-Schema-Datei für einen Management OData-Webdienst](./authoring-the-xml-schema-file-for-a-management-odata-web-service.md)

- [Erstellen die Datei "Web.config" für einen Management OData-Webdienst](./authoring-the-web-config-file-for-a-management-odata-web-service.md)

- [Bereitstellen eines Webdiensts Management OData](./deploying-a-management-odata-web-service.md)

- [Zuordnen von Management OData-Entitäten](./associating-management-odata-entities.md)

## <a name="see-also"></a>Weitere Informationen

[Schemadateien für Management ODATA IIS-Erweiterung](./management-odata-iis-extension-schema-files.md)
