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
# <a name="configuring-role-based-authorization"></a><span data-ttu-id="7bfdd-102">Konfigurieren der rollenbasierten Autorisierung</span><span class="sxs-lookup"><span data-stu-id="7bfdd-102">Configuring Role-based Authorization</span></span>

<span data-ttu-id="7bfdd-103">In diesem Thema wird veranschaulicht, wie Sie zum Konfigurieren der rollenbasierten Autorisierung-Richtlinie für die beispielimplementierung von der [Microsoft.Management.Odata.Customauthorization](/dotnet/api/Microsoft.Management.Odata.CustomAuthorization) Schnittstelle, die in beschriebenen [Implementieren von benutzerdefinierten Autorisierung für Management OData IIS-Erweiterung](./implementing-custom-authorization-for-a-management-odata-web-service.md).</span><span class="sxs-lookup"><span data-stu-id="7bfdd-103">This topic demonstrates how to configure the role-based authorization policy for the sample implementation of the [Microsoft.Management.Odata.Customauthorization](/dotnet/api/Microsoft.Management.Odata.CustomAuthorization) interface described in [Implementing Custom Authorization for Management OData IIS Extension](./implementing-custom-authorization-for-a-management-odata-web-service.md).</span></span>

<span data-ttu-id="7bfdd-104">In diesem Beispiel konfigurieren Sie eine XML-Datei, die von der beispielanwendung für Management OData zum Definieren der Autorisierungsrichtlinie verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="7bfdd-104">In this example, you will configure an XML file that is used by the sample Management OData application to define the authorization policy.</span></span> <span data-ttu-id="7bfdd-105">Sie erstellen zwei Rollen und Zuordnen von anderen Windows PowerShell-Module, die Workflows mit diesen Rollen enthalten.</span><span class="sxs-lookup"><span data-stu-id="7bfdd-105">You will create two roles and associate different Windows PowerShell modules that contain workflows with those roles.</span></span> <span data-ttu-id="7bfdd-106">Das Schema, das die XML-Datei definiert wird am [Role-Based Authorization-Konfigurationsschema](./role-based-authorization-configuration-schema.md).</span><span class="sxs-lookup"><span data-stu-id="7bfdd-106">The schema that defines the XML file is listed at [Role-Based Authorization Configuration Schema](./role-based-authorization-configuration-schema.md).</span></span>

## <a name="modifying-the-rbacconfigurationxml-file"></a><span data-ttu-id="7bfdd-107">Ändern der Datei RBacConfiguration.xml</span><span class="sxs-lookup"><span data-stu-id="7bfdd-107">Modifying the RBacConfiguration.xml File</span></span>

<span data-ttu-id="7bfdd-108">Diese Datei definiert die Autorisierungsrichtlinie für die Anwendung.</span><span class="sxs-lookup"><span data-stu-id="7bfdd-108">This file defines the authorization policy for the application.</span></span> <span data-ttu-id="7bfdd-109">Rollen werden mit definiert `Group` Knoten.</span><span class="sxs-lookup"><span data-stu-id="7bfdd-109">Roles are defined by using `Group` nodes.</span></span> <span data-ttu-id="7bfdd-110">Ein `Group` Knoten definiert, die Windows PowerShell-Befehle, die dieser Gruppe zugewiesenen Benutzer ausführen können.</span><span class="sxs-lookup"><span data-stu-id="7bfdd-110">A `Group` node defines the Windows PowerShell commands that users assigned to that group can run.</span></span> <span data-ttu-id="7bfdd-111">Benutzer werden mithilfe von Gruppen zugewiesen `User` Knoten.</span><span class="sxs-lookup"><span data-stu-id="7bfdd-111">Users are assigned to groups by using `User` nodes.</span></span>

<span data-ttu-id="7bfdd-112">In diesen Beispielen, fügen Sie ein Modul an den Administrator `Group` Knoten, und fügen Sie für jede Gruppe einen Benutzer hinzu.</span><span class="sxs-lookup"><span data-stu-id="7bfdd-112">In these examples, you will add a module to the Administrator `Group` node, and add a user to each group.</span></span>

#### <a name="adding-a-module-to-a-group-node"></a><span data-ttu-id="7bfdd-113">Hinzufügen eines Moduls zu einem Gruppenknoten</span><span class="sxs-lookup"><span data-stu-id="7bfdd-113">Adding a Module to a Group Node</span></span>

1. <span data-ttu-id="7bfdd-114">Erstellen Sie eine Datei mit dem Namen **RBacConfiguration.xml** in einem Text-Editor.</span><span class="sxs-lookup"><span data-stu-id="7bfdd-114">Create a file named **RBacConfiguration.xml** in a text editor.</span></span> <span data-ttu-id="7bfdd-115">Diese Datei sollte in main Anwendungsverzeichnis für Ihren Webdienst gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="7bfdd-115">This file should be saved to the main application directory for your web service.</span></span> <span data-ttu-id="7bfdd-116">Fügen Sie den folgenden Text in der Datei.</span><span class="sxs-lookup"><span data-stu-id="7bfdd-116">Insert the following text in the file.</span></span>

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

2. <span data-ttu-id="7bfdd-117">Die Datei enthält zwei `Group` Knoten.</span><span class="sxs-lookup"><span data-stu-id="7bfdd-117">The file contains two `Group` nodes.</span></span> <span data-ttu-id="7bfdd-118">Diese repräsentieren die beiden Rollen, die in diesem Beispiel verwendet die `NonAdminGroup` und `AdminGroup` Rollen.</span><span class="sxs-lookup"><span data-stu-id="7bfdd-118">These represent the two roles used in this example, the `NonAdminGroup` and the `AdminGroup` roles.</span></span>

   <span data-ttu-id="7bfdd-119">Direkt nach dem schließenden `Cmdlets` Tag in der ersten `Group` Knoten fügen die folgende XML hinzu:</span><span class="sxs-lookup"><span data-stu-id="7bfdd-119">Directly after the closing `Cmdlets` tag in the first `Group` node, add the following XML:</span></span>

   ```xml
   <Modules>
           <Module>C:\Windows\System32\WindowsPowerShell\v1.0\Modules\ServerManager\ServerManager.psd1</Module>
         </Modules>
   ```

#### <a name="adding-a-user-to-a-group-node"></a><span data-ttu-id="7bfdd-120">Hinzufügen eines Benutzers zu einem Gruppenknoten</span><span class="sxs-lookup"><span data-stu-id="7bfdd-120">Adding a User to a Group Node</span></span>

1. <span data-ttu-id="7bfdd-121">Öffnen der **RBacConfiguration.xml** -Datei in einem Text-Editor.</span><span class="sxs-lookup"><span data-stu-id="7bfdd-121">Open the **RBacConfiguration.xml** file in a text editor.</span></span> <span data-ttu-id="7bfdd-122">Diese Datei befindet sich im Ordner "C:"\\\inetpub\wwwroot\Modata, wenn Sie den Namen des Endpunkts vor der Installation nicht geändert haben.</span><span class="sxs-lookup"><span data-stu-id="7bfdd-122">This file is located in the folder C:\\\inetpub\wwwroot\Modata  if you did not change the endpoint name before installation.</span></span>

2. <span data-ttu-id="7bfdd-123">Direkt nach dem schließenden Tag in die `Users` Knoten fügen die folgende XML hinzu:</span><span class="sxs-lookup"><span data-stu-id="7bfdd-123">Directly after the closing tag in the `Users` node, add the following XML:</span></span>

   ```xml
   <User Name="UserName" GroupName="AdminGroup" AuthenticationType="Basic" DomainName="DomainName"/>
   ```

3. <span data-ttu-id="7bfdd-124">Fügen Sie direkt nach der XML-Code im vorherigen Schritt hinzugefügt haben hinzu, den folgenden XML-Code:</span><span class="sxs-lookup"><span data-stu-id="7bfdd-124">Directly after the XML added in the previous step, add the following XML:</span></span>

   ```xml
   <User Name="UserName" GroupName="NonAdminGroup" AuthenticationType="Basic" DomainName="DomainName"/>
   ```