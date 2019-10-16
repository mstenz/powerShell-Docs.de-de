---
title: Erstellen der Datei "Web. config" für einen odata-Webdienst für die Verwaltung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d569f5d5-9746-40c0-be5e-f218bc4560f7
caps.latest.revision: 4
ms.openlocfilehash: f52953ee091f05df5f355719ecba788d3d5ee055
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359789"
---
# <a name="authoring-the-webconfig-file-for-a-management-odata-web-service"></a>Erstellen der Web.config-Schemadatei für einen Management OData-Webdienst

Bevor Sie den Management odata-Webdienst bereitstellen können, müssen Sie die Datei Web. config so konfigurieren, dass Sie auf die XML-Schema Dateien und die DLLs verweist, die [Microsoft. Management. odata. customauthorization](/dotnet/api/Microsoft.Management.Odata.CustomAuthorization) implementieren, und [ System. Management. Automation. Remoting. pssessionconfiguration](/dotnet/api/System.Management.Automation.Remoting.PSSessionConfiguration) -Schnittstellen.

## <a name="sample-config-file"></a>Beispielkonfigurationsdatei

Im folgenden finden Sie ein Beispiel dafür, wie die Web. config-Datei für Ihren Webdienst aussieht.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<configuration>
   <configSections>
      <section name="managementOdata" type="Microsoft.Management.Odata.Core.DSConfiguration, Microsoft.Management.OData, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL" />
   </configSections>
   <managementOdata schemaFileName="Schema.mof" resourceMappingFileName="Schema.xml">
      <customAuthorization type="Microsoft.Samples.Management.OData.RoleBasedPlugins.CustomAuthorization" assembly=".\Microsoft.Samples.Management.OData.RoleBasedPlugins.dll" />
      <powershell>
         <sessionConfiguration type="Microsoft.Samples.Management.OData.RoleBasedPlugins.SessionConfiguration" assembly=".\Microsoft.Samples.Management.OData.RoleBasedPlugins.dll" />
      </powershell>
      <commandInvocation enabled="true" />
      <wcfDataServicesConfig>
      </wcfDataServicesConfig>
   </managementOdata>
   <system.serviceModel>
      <behaviors>
         <serviceBehaviors>
            <behavior>
                  <serviceAuthorization serviceAuthorizationManagerType="Microsoft.Management.Odata.Core.CustomAuthorizationManager, Microsoft.Management.OData, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" />
            </behavior>
         </serviceBehaviors>
      </behaviors>
      <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />
   </system.serviceModel>
   <system.webServer>
      <security>
         <authentication>
            <anonymousAuthentication enabled="false" />
            <basicAuthentication enabled="true" />
            <windowsAuthentication enabled="false" />
         </authentication>
      </security>
  </system.webServer>
</configuration>

```

## <a name="see-also"></a>Weitere Informationen

[Implementieren einer benutzerdefinierten Autorisierung für einen Management-odata-Webdienst](./implementing-custom-authorization-for-a-management-odata-web-service.md)

[Implementieren von SessionConfiguration für einen Management-odata-Webdienst](./implementing-sessionconfiguration-for-a-management-odata-web-service.md)

[Erstellen der MOF-Schema Datei für einen Management odata-Webdienst](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

[Erstellen der XML-Schema Datei für einen Management odata-Webdienst](./authoring-the-xml-schema-file-for-a-management-odata-web-service.md)

[Erstellen eines odata-Webdiensts für die Verwaltung](./creating-a-management-odata-web-service.md)