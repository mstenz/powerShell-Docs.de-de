---
title: Hinzufügen von Windows PowerShell-Aktivitäten zur Visual Studio-Toolbox | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c8ef289-0659-42d1-9976-044b144201eb
caps.latest.revision: 6
ms.openlocfilehash: ecd23d3eb722137bdda0498fc71e0e966c57a589
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83561188"
---
# <a name="adding-windows-powershell-activities-to-the-visual-studio-toolbox"></a>Hinzufügen von Windows PowerShell-Aktivitäten zur Visual Studio-Toolbox

Bevor Sie einen PowerShell-Workflow mithilfe von Workflow-Designer erstellen, müssen Sie die PowerShell-Aktivitäten zunächst der Toolbox in einem Konsolen Anwendungsprojekt von Visual Studio Workflow hinzufügen. Im folgenden Verfahren wird gezeigt, wie die Aktivitäten aus der Microsoft. PowerShell. Core. Activities-Assembly der Visual Studio-Toolbox hinzugefügt werden.

### <a name="adding-windows-powershell-activities-to-the-toolbox"></a>Hinzufügen von Windows PowerShell-Aktivitäten zur Toolbox

1. Erstellen Sie in Visual Studio ein neues Projekt für eine Workflow Konsolenanwendung.

2. Klicken Sie im Menü **Ansicht** auf **Toolbox**.

3. Fügen Sie eine neue Registerkarte in der Toolbox hinzu, indem Sie mit der rechten Maustaste in die Toolbox klicken und auf **Registerkarte hinzufügen**klicken und der neuen Registerkarte einen Namen wie "PowerShell-Aktivitäten" geben.

   Durch das Hinzufügen einer Registerkarte können Sie die PowerShell-Aktivitäten getrennt von anderen Tools in der Toolbox gruppieren.

4. Klicken Sie auf der Registerkarte neue Toolbox auf **Elemente auswählen...**. Das Dialogfeld **Toolbox Elemente auswählen** wird angezeigt.

5. Klicken Sie im Dialogfeld **Toolbox Elemente auswählen** auf die Registerkarte **System. Activities** .

6. Klicken Sie auf **Durchsuchen**.

7. Navigieren Sie zum Ordner%windir%\Microsoft.net\assembly\ GAC_MSIL \Microsoft.PowerShell.Core.activities\v4.0_3.0.0.0__31bf3856ad364e, und doppelklicken Sie auf Microsoft. PowerShell. Core. Activities. dll.

8. Klicken Sie auf **OK**. Die von der Microsoft. PowerShell. Core. Activities-Assembly definierten Aktivitäten sind jetzt in der Toolbox verfügbar.

## <a name="see-also"></a>Weitere Informationen

[Schreiben Sie einen Windows PowerShell-Workflow](./writing-a-windows-powershell-workflow.md)

[Erstellen eines Workflows mit Windows PowerShell-Aktivitäten](./creating-a-workflow-with-windows-powershell-activities.md)
