---
title: Erstellen eines Workflows mit Windows PowerShell-Aktivitäten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb55971a-4ea4-4c51-aeff-4e0bb05a51b2
caps.latest.revision: 6
ms.openlocfilehash: 65d04c526ef7aa112da82adb924c0789731f3850
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853466"
---
# <a name="creating-a-workflow-with-windows-powershell-activities"></a>Erstellen eines Workflows mit Windows PowerShell-Aktivitäten

Sie können einen Windows PowerShell-Workflow erstellen, durch Auswählen von Aktivitäten in der Visual Studio-Toolbox und ziehen sie an das Workflow-Designer-Fenster. Informationen zum Hinzufügen von Windows PowerShell-Aktivitäten zu Visual Studio-Toolbox finden Sie unter [Hinzufügen von Windows PowerShell-Aktivitäten, die Visual Studio-Toolbox](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md).

Die folgenden Verfahren wird beschrieben, wie zum Erstellen eines Workflows, die sie mit einer Domäne verknüpft werden, wenn sie nicht bereits verknüpft sind, und klicken Sie dann erneut den Status überprüft überprüft den Domänenstatus einer Gruppe von Benutzer angegebenen Computer.

### <a name="setting-up-the-project"></a>Einrichten des Projekts

1. Führen Sie die Verfahren in [Hinzufügen von Windows PowerShell-Aktivitäten, die Visual Studio-Toolbox](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md) erstellen ein Workflowprojekt und Hinzufügen von Aktivitäten aus der [Microsoft.Powershell.Activities](/dotnet/api/Microsoft.PowerShell.Activities) und [ Microsoft.Powershell.Management.Activities](/dotnet/api/Microsoft.PowerShell.Management.Activities) Assemblys zur Toolbox.

2. System.Management.Automation, Microsoft.PowerShell.Activities, System.Management, Microsoft.PowerShell.Management.Activities und Microsoft.PowerShell.Commands.Management als referenzassemblys, dem Projekt hinzufügen.

### <a name="adding-activities-to-the-workflow"></a>Hinzufügen von Aktivitäten zu Workflows

1. Hinzufügen einer **Sequenz** -Aktivität zum Workflow.

2. Erstellen Sie ein Argument mit dem Namen `ComputerName` mit Argumenttyp `String[]`. Dieses Argument stellt den Namen der Computer zu überprüfen und zu verknüpfen.

3. Erstellen Sie ein Argument mit dem Namen `DomainCred` des Typs [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential). Dieses Argument stellt die Anmeldeinformationen für die Domäne für ein Domänenkonto an, die zum Hinzufügen eines Computers zur Domäne berechtigt ist.

4. Erstellen Sie ein Argument mit dem Namen `MachineCred` des Typs [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential). Dieses Argument stellt die Anmeldeinformationen eines Administrators auf den Computern, um zu überprüfen und zu verknüpfen.

5. Hinzufügen einer **ParallelForEach** Aktivität innerhalb der **Sequenz** Aktivität. Geben Sie `comp` und `ComputerName` in den Textfeldern, damit die Elemente die Schleife durchläuft die `ComputerName` Array.

6. Hinzufügen einer **Sequenz** Aktivität in den Text der der **ParallelForEach** Aktivität. Legen Sie die **"DisplayName"** Eigenschaft der Sequenz, die `JoinDomain`.

7. Hinzufügen einer **GetWmiObject** Aktivität, um die **JoinDomain** Sequenz.

8. Bearbeiten der Eigenschaften der **GetWmiObject** Aktivität wie folgt.

   |Eigenschaft|Wert|
   |--------------|-----------|
   |**Klasse**|"Win32_ComputerSystem"|
   |**PSComputerName**|{Comp}|
   |**PSCredential**|MachineCred|

9. Hinzufügen einer **AddComputer** Aktivität, um die **JoinDomain** nach dem Sequenzieren der **GetWmiObject** Aktivität.

10. Bearbeiten der Eigenschaften der **AddComputer** Aktivität wie folgt.

    |Eigenschaft|Wert|
    |--------------|-----------|
    |**ComputerName**|{Comp}|
    |**DomainCredential**|DomainCred|

11. Hinzufügen einer **RestartComputer** Aktivität, um die **JoinDomain** nach dem Sequenzieren der **AddComputer** Aktivität.

12. Bearbeiten der Eigenschaften der **RestartComputer** Aktivität wie folgt.

    |Eigenschaft|Wert|
    |--------------|-----------|
    |**ComputerName**|{Comp}|
    |**Anmeldeinformationen**|MachineCred|
    |**für**|Microsoft.PowerShell.Commands.WaitForServiceTypes.PowerShell|
    |**Force**|Wahr|
    |Wartezeit|Wahr|
    |PSComputerName|{""}|

13. Hinzufügen einer **GetWmiObject** Aktivität, um die **JoinDomain** nach dem Sequenzieren der **RestartComputer** Aktivität. Bearbeiten der Eigenschaften, um die vorherige entsprechen **GetWmiObject** Aktivität.

    Wenn Sie die Verfahren abgeschlossen haben, sollte das Workflow-Designer-Fenster wie folgt aussehen.

    ![JoinDomain XAML im Workflow-Designer](../media/joindomainworkflow.png)
    ![JoinDomain XAML im Workflow-Designer](../media/joindomainworkflow.png "JoinDomainWorkflow")