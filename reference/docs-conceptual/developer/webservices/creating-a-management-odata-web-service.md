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
# <a name="creating-a-management-odata-web-service"></a>Erstellen eines Management OData-Webdiensts

Die IIS-Erweiterung für die Verwaltung von odata ist eine Infrastruktur zum Erstellen eines ASP.NET-Webdienst-Endpunkts, der Ihre Verwaltungsdaten verfügbar macht. der Zugriff erfolgt über Windows PowerShell-Cmdlets und-Skripts als odata-Webdienst Dies geschieht, indem odata-Anforderungen verarbeitet und in einen Windows PowerShell-Aufruf umgewandelt werden. Produktteams können auf dieser Infrastruktur aufbauen, um Endpunkte zu erstellen, die bestimmte Sätze von Verwaltungsdaten verfügbar machen.

Laden Sie das Beispiel [ptauscht-rolebasedplugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) herunter, und installieren Sie es. Befolgen Sie die Anweisungen zum Bereitstellen des Webdiensts. Dieser Webdienst macht Dienste und Prozesse über Vorgänge zum Erstellen, lesen, aktualisieren und löschen (CRUD) verfügbar. CRUD-Anforderungen, die an den Webdienst gerichtet werden, rufen Windows PowerShell-Befehle auf, die die angeforderten Vorgänge ausführen. Eine Zuordnung zwischen den CRUD-Vorgängen und den zugrunde liegenden Windows PowerShell-Befehlen wird durch zwei Schema Dateien ("Schema. mof" und "Schema. xml") implementiert. Die Datei "Schema. mof" [verwendet den](https://www.dmtf.org/) MOF-Standard (DMTF) Managed Object (DMTF). Die Datei "Schema. xml" verwendet ein XML-Schema, das unter [Ressourcen Zuordnung Schema](./resource-mapping-schema.md)beschrieben wird.

> [!IMPORTANT]
> Bevor Sie die Verwaltungs-odata-IIS-Erweiterung unter Windows Server 2008 R2 SP1 aktivieren, müssen die folgenden Funktionen aktiviert werden.
>
> 1. IIS-WebServerRole
> 2. IIS-WebServer
> 3. IIS-HttpTracing
> 4. IIS-managementodata

## <a name="steps-for-creating-a-management-odata-web-service"></a>Schritte zum Erstellen eines odata-Webdiensts für die Verwaltung

In den folgenden Themen wird beschrieben, wie Sie einen odata-Webdienst für die Verwaltung erstellen und bereitstellen.

- [Hinzufügen von Ressourcen zu einem Management OData-Webdienst](./adding-resources-to-a-management-odata-web-service.md)

- [Implementieren der benutzerdefinierten Autorisierung für einen Management OData-Webdienst](./implementing-custom-authorization-for-a-management-odata-web-service.md)

- [Implementieren von SessionConfiguration für einen Management OData-Webdienst](./implementing-sessionconfiguration-for-a-management-odata-web-service.md)

- [Erstellen der MOF-Schemadatei für einen Management OData-Webdienst](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

- [Erstellen der XML-Schemadatei für einen Management OData-Webdienst](./authoring-the-xml-schema-file-for-a-management-odata-web-service.md)

- [Erstellen der Web.config-Schemadatei für einen Management OData-Webdienst](./authoring-the-web-config-file-for-a-management-odata-web-service.md)

- [Bereitstellen eines Management OData-Webdiensts](./deploying-a-management-odata-web-service.md)

- [Zuordnen von Management OData-Entitäten](./associating-management-odata-entities.md)

## <a name="see-also"></a>Weitere Informationen

[Verwaltungs-odata-IIS-Erweiterungs Schema Dateien](./management-odata-iis-extension-schema-files.md)
