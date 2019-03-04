---
title: Konfigurieren der rollenbasierten Autorisierung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2933a6ca-fe92-4ba2-97ee-ef0f0d5fdfcf
caps.latest.revision: 8
ms.openlocfilehash: b73284adb4bf228510bf8134aa4c6a10561b7ea2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859596"
---
# <a name="configuring-role-based-authorization"></a>Konfigurieren der rollenbasierten Autorisierung

In diesem Thema wird veranschaulicht, wie Sie zum Konfigurieren der rollenbasierten Autorisierung-Richtlinie für die beispielimplementierung von der [Microsoft.Management.Odata.Customauthorization](/dotnet/api/Microsoft.Management.Odata.CustomAuthorization) Schnittstelle, die in beschriebenen [Implementieren von benutzerdefinierten Autorisierung für Management OData IIS-Erweiterung](./implementing-custom-authorization-for-a-management-odata-web-service.md).

In diesem Beispiel konfigurieren Sie eine XML-Datei, die von der beispielanwendung für Management OData zum Definieren der Autorisierungsrichtlinie verwendet wird. Sie erstellen zwei Rollen und Zuordnen von anderen Windows PowerShell-Module, die Workflows mit diesen Rollen enthalten. Das Schema, das die XML-Datei definiert wird am [Role-Based Authorization-Konfigurationsschema](./role-based-authorization-configuration-schema.md).

## <a name="modifying-the-rbacconfigurationxml-file"></a>Ändern der Datei RBacConfiguration.xml

Diese Datei definiert die Autorisierungsrichtlinie für die Anwendung. Rollen werden mit definiert `Group` Knoten. Ein `Group` Knoten definiert, die Windows PowerShell-Befehle, die dieser Gruppe zugewiesenen Benutzer ausführen können. Benutzer werden mithilfe von Gruppen zugewiesen `User` Knoten.

In diesen Beispielen, fügen Sie ein Modul an den Administrator `Group` Knoten, und fügen Sie für jede Gruppe einen Benutzer hinzu.

#### <a name="adding-a-module-to-a-group-node"></a>Hinzufügen eines Moduls zu einem Gruppenknoten

1. Erstellen Sie eine Datei mit dem Namen **RBacConfiguration.xml** in einem Text-Editor. Diese Datei sollte in main Anwendungsverzeichnis für Ihren Webdienst gespeichert werden. Fügen Sie den folgenden Text in der Datei.

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <RbacConfiguration>
     <Groups>
       <!--Group consists of the following:
         Name:  Name of the group
         UserName (Optional): Windows Identity user name
         Password (Optional): Password of the Windows user name
         DomainName (Optional): Domain for the user. For local machine account either do not include them or give the machine name. Do not give empty string
         MapIncomingUser (Optional): Boolean value indicating whether to execute cmdlet in the context of network client.

         User credentials and MapIncomingUser=true are exclusive.
       -->
       <Group Name="NonAdminGroup" MapIncomingUser="true">
         <Cmdlets>
           <Cmdlet>Get-Service</Cmdlet>
           <Cmdlet>Set-Service</Cmdlet>
           <Cmdlet>Get-Process</Cmdlet>
           <Cmdlet>Get-Item</Cmdlet>
           <Cmdlet>New-Item</Cmdlet>
           <Cmdlet>Get-Command</Cmdlet>
           <Cmdlet>ConvertTo-Xml</Cmdlet>
           <Cmdlet>ConvertTo-Json</Cmdlet>
           <Cmdlet>ConvertFrom-Json</Cmdlet>
         </Cmdlets>
       </Group>
       <Group Name="AdminGroup" MapIncomingUser="true">
         <Cmdlets>
           <Cmdlet>Get-Service</Cmdlet>
           <Cmdlet>Get-Process</Cmdlet>
           <Cmdlet>Get-Item</Cmdlet>
           <Cmdlet>New-Item</Cmdlet>
           <Cmdlet>Get-Command</Cmdlet>
           <Cmdlet>ConvertTo-Xml</Cmdlet>
           <Cmdlet>ConvertTo-Json</Cmdlet>
           <Cmdlet>ConvertFrom-Json</Cmdlet>
         </Cmdlets>
         <Modules>
           <Module>C:\Windows\System32\WindowsPowerShell\v1.0\Modules\ServerManager\ServerManager.psd1</Module>
         </Modules>
       </Group>
     </Groups>
     <Users>
       <!-- User consists of the following :
         Name: Name of the user. If a user is from a cer
         AuthenticationType: Authentication type used.
         DomainName (Optional): Domain for the user
       -->
       <User Name="localNonAdmin" AuthenticationType="Basic" GroupName="NonAdminGroup" />
       <User Name="localAdmin" AuthenticationType="Basic" GroupName="AdminGroup" />
     </Users>
   </RbacConfiguration>
   ```

2. Die Datei enthält zwei `Group` Knoten. Diese repräsentieren die beiden Rollen, die in diesem Beispiel verwendet die `NonAdminGroup` und `AdminGroup` Rollen.

   Direkt nach dem schließenden `Cmdlets` Tag in der ersten `Group` Knoten fügen die folgende XML hinzu:

   ```xml
   <Modules>
           <Module>C:\Windows\System32\WindowsPowerShell\v1.0\Modules\ServerManager\ServerManager.psd1</Module>
         </Modules>
   ```

#### <a name="adding-a-user-to-a-group-node"></a>Hinzufügen eines Benutzers zu einem Gruppenknoten

1. Öffnen der **RBacConfiguration.xml** -Datei in einem Text-Editor. Diese Datei befindet sich im Ordner "C:"\\\inetpub\wwwroot\Modata, wenn Sie den Namen des Endpunkts vor der Installation nicht geändert haben.

2. Direkt nach dem schließenden Tag in die `Users` Knoten fügen die folgende XML hinzu:

   ```xml
   <User Name="UserName" GroupName="AdminGroup" AuthenticationType="Basic" DomainName="DomainName"/>
   ```

3. Fügen Sie direkt nach der XML-Code im vorherigen Schritt hinzugefügt haben hinzu, den folgenden XML-Code:

   ```xml
   <User Name="UserName" GroupName="NonAdminGroup" AuthenticationType="Basic" DomainName="DomainName"/>
   ```