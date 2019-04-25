---
title: Hinzufügen von Windows PowerShell-Aktivitäten zu Visual Studio-Toolbox | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c8ef289-0659-42d1-9976-044b144201eb
caps.latest.revision: 6
ms.openlocfilehash: 2a8372d937fc3c959f7d829bb52495048423d506
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080474"
---
# <a name="adding-windows-powershell-activities-to-the-visual-studio-toolbox"></a>Hinzufügen von Windows PowerShell-Aktivitäten zur Visual Studio-Toolbox

Bevor Sie ein PowerShell-Workflow mit Workflow-Designer erstellen, müssen Sie zuerst die PowerShell-Aktivitäten zur Toolbox in ein Visual Studio Workflow-Konsolenanwendungsprojekt hinzufügen. Das folgende Verfahren veranschaulicht das Hinzufügen die Aktivitäten aus der Assembly Microsoft.PowerShell.Core.Activities zur Visual Studio-Toolbox.

### <a name="adding-windows-powershell-activities-to-the-toolbox"></a>Hinzufügen von Windows PowerShell-Aktivitäten zur Toolbox

1. Erstellen Sie ein neues Workflow-Konsolenanwendungsprojekt in Visual Studio.

2. Auf der **Ansicht** Menü klicken Sie auf **Toolbox**.

3. Fügen Sie eine neue Registerkarte in der Toolbox hinzu, indem Sie mit der rechten Maustaste in die Toolbox, und auf **Registerkarte hinzufügen**, und benennen Sie der neuen Registerkarte wie"PowerShell".

   Hinzufügen einer Registerkarte können Sie die PowerShell-Aktivitäten, die getrennt von anderen Tools in der Toolbox zu gruppieren.

4. Klicken Sie auf die neue Werkzeugkasten-Registerkarte, auf **Elemente auswählen...** . Die **Toolboxelemente** Dialogfeld wird angezeigt.

5. In der **Toolboxelemente** Dialogfeld klicken Sie auf die **System.Activities** Registerkarte.

6. Klicken Sie auf **Durchsuchen**.

7. Navigieren Sie zum Ordner %WINDIR%\Microsoft.NET\assembly\GAC_MSIL\Microsoft.PowerShell.Core.Activities\v4.0_3.0.0.0__31bf3856ad364e, und doppelklicken Sie auf Microsoft.PowerShell.Core.Activities.dll.

8. Klicken Sie auf **OK**. Die von der Microsoft.PowerShell.Core.Activities-Assembly definierten Aktivitäten sind jetzt in der Toolbox verfügbar.

## <a name="see-also"></a>Weitere Informationen

[Schreiben eines PowerShell-Workflows](./writing-a-windows-powershell-workflow.md)

[Erstellen eines Workflows mit Windows PowerShell-Aktivitäten](./creating-a-workflow-with-windows-powershell-activities.md)