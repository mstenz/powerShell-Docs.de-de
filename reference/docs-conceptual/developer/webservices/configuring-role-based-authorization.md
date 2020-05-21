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
ms.openlocfilehash: 2c9d6040b7a9c17dc5204c8eb835fd69780f62c5
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83564256"
---
# <a name="configuring-role-based-authorization"></a>Konfigurieren der rollenbasierten Autorisierung

In diesem Thema wird veranschaulicht, wie Sie die rollenbasierte Autorisierungs Richtlinie für die Beispiel Implementierung der [Microsoft. Management. odata. customauthorization](/dotnet/api/Microsoft.Management.Odata.CustomAuthorization) -Schnittstelle konfigurieren, die unter [Implementieren der benutzerdefinierten Autorisierung für die IIS-Erweiterung "Management odata](./implementing-custom-authorization-for-a-management-odata-web-service.md)" beschrieben

In diesem Beispiel konfigurieren Sie eine XML-Datei, die von der beispielverwaltungs-odata-Anwendung verwendet wird, um die Autorisierungs Richtlinie zu definieren. Sie erstellen zwei Rollen und ordnen verschiedene Windows PowerShell-Module zu, die Workflows mit diesen Rollen enthalten. Das Schema, das die XML-Datei definiert, wird unter [rollenbasiertes Autorisierungs Konfigurations Schema](./role-based-authorization-configuration-schema.md)aufgelistet.

## <a name="modifying-the-rbacconfigurationxml-file"></a>Ändern der Datei "rbacconfiguration. xml"

Mit dieser Datei wird die Autorisierungs Richtlinie für die Anwendung definiert. Rollen werden mithilfe von `Group` Knoten definiert. Ein `Group` Knoten definiert die Windows PowerShell-Befehle, die Benutzer ausführen können, die dieser Gruppe zugewiesen sind. Benutzer werden Gruppen mithilfe von- `User` Knoten zugewiesen.

In diesen Beispielen fügen Sie dem Knoten Administrator ein Modul hinzu `Group` und fügen jeder Gruppe einen Benutzer hinzu.

#### <a name="adding-a-module-to-a-group-node"></a>Hinzufügen eines Moduls zu einem Gruppenknoten

1. Erstellen Sie eine Datei mit dem Namen **rbacconfiguration. XML** in einem Text-Editor. Diese Datei sollte im Haupt Anwendungsverzeichnis für Ihren Webdienst gespeichert werden. Fügen Sie den folgenden Text in die Datei ein.

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

2. Die Datei enthält zwei `Group` Knoten. Diese stellen die beiden Rollen dar, die in diesem Beispiel verwendet werden, `NonAdminGroup` und die `AdminGroup` Rollen.

   Fügen Sie direkt nach dem schließenden `Cmdlets` Tag im ersten `Group` Knoten den folgenden XML-Code hinzu:

   ```xml
   <Modules>
           <Module>C:\Windows\System32\WindowsPowerShell\v1.0\Modules\ServerManager\ServerManager.psd1</Module>
         </Modules>
   ```

#### <a name="adding-a-user-to-a-group-node"></a>Hinzufügen eines Benutzers zu einem Gruppenknoten

1. Öffnen Sie die Datei " **rbacconfiguration. XML** " in einem Text-Editor. Diese Datei befindet sich im Ordner C: \\ \inetpub\wwwroot\mudata, wenn Sie den Endpunkt Namen vor der Installation nicht geändert haben.

2. Fügen Sie direkt nach dem schließenden Tag im- `Users` Knoten den folgenden XML-Code hinzu:

   ```xml
   <User Name="UserName" GroupName="AdminGroup" AuthenticationType="Basic" DomainName="DomainName"/>
   ```

3. Fügen Sie direkt nach dem im vorherigen Schritt hinzugefügten XML-Code den folgenden XML-Code hinzu:

   ```xml
   <User Name="UserName" GroupName="NonAdminGroup" AuthenticationType="Basic" DomainName="DomainName"/>
   ```
