---
title: Cmdlet-Klassendeklaration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell SDK], declaring
- declaring cmdlets [PowerShell SDK]
ms.assetid: 1fcc4c5e-0c75-496c-a712-5f844e310576
caps.latest.revision: 14
ms.openlocfilehash: 3e410087438ac99526049f99e5c768c017a29848
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854446"
---
# <a name="cmdlet-class-declaration"></a>Deklaration der Cmdlet-Klasse

Microsoft .NET Framework-Klasse ist als ein Cmdlet deklariert, durch Angabe der **Cmdlet** -Attribut als Metadaten für die Klasse. (Die **Cmdlet** -Attribut ist das einzige erforderliche Attribut für alle Cmdlets). Bei Angabe der **Cmdlet** -Attribut, müssen Sie das Verb-Substantiv-Paar, das das-Cmdlet für den Benutzer identifiziert angeben. Und Sie müssen die Windows PowerShell-Funktionen, die das Cmdlet unterstützt beschreiben. Weitere Informationen über die Syntax zum Deklarieren, die verwendet wird, an die **Cmdlet** Attribut, finden Sie unter [Cmdlet Attributdeklaration](./cmdlet-attribute-declaration.md).

> [!NOTE]
> Die **Cmdlet** Attribut wird definiert, indem die [System.Management.Automation.Cmdletattribute](/dotnet/api/System.Management.Automation.CmdletAttribute) Klasse. Die Eigenschaften dieser Klasse entsprechen den Parametern der Deklaration aus, die verwendet werden, wenn Sie das Attribut deklarieren.

## <a name="nouns"></a>Nomen

Das Nomen "des Cmdlets" gibt an, die Ressourcen, die auf denen das Cmdlet ausgeführt wird. Das Nomen unterscheidet Ihre Cmdlets von anderen Cmdlets.

Nomen im Cmdlet-Namen muss spezifisch, und im Fall von generischen Nomen, z. B. *Server*, es wird empfohlen, ein kurzes Präfix hinzufügen, das die Ressource von anderen ähnlichen Ressourcen unterscheidet. Ist Sie ein Cmdlet-Namen, die ein Substantiv mit einem Präfix enthält z. B. `Get-SQLServer`. Die Kombination aus einem bestimmten Nomen verbunden mit einem allgemeineren Verb ermöglicht den Benutzer schnell das-Cmdlet, durch die Aktion, und klicken Sie dann das Cmdlet mit der Ressourcen zu identifizieren, während die Vermeidung der mehrfachen Ausführung unnötige Cmdlet-Namen.

Eine Liste der Sonderzeichen, die in der Cmdlet-Namen verwendet werden können, finden Sie unter [Entwicklungsrichtlinien erforderlich](./required-development-guidelines.md).

## <a name="verbs"></a>Verben

Wenn Sie ein Verb angeben, erfordern die Richtlinien für die Entwicklung Sie eine der vordefinierten bereitgestellten, die von Windows PowerShell-Verben verwenden. Mithilfe einer dieser vordefinierten Verben, sorgt Sie Konsistenz zwischen den Cmdlets, die Sie schreiben und die Cmdlets, die von Microsoft und von anderen Benutzern geschrieben werden. Beispielsweise wird das Verb "Get" für Cmdlets verwendet, die Daten abrufen.

Weitere Informationen zu Richtlinien für die Verben, finden Sie unter [Cmdlet Verbnamen](./approved-verbs-for-windows-powershell-commands.md). Eine Liste der Sonderzeichen, die in der Cmdlet-Namen verwendet werden können, finden Sie unter [Entwicklungsrichtlinien erforderlich](./required-development-guidelines.md).

## <a name="supporting-windows-powershell-functionality"></a>Unterstützung von Windows PowerShell-Funktionen

Die **Cmdlet** Attribut auch können Sie angeben, dass Ihr Cmdlet einige gemeinsame Funktionen unterstützt, die von Windows PowerShell bereitgestellt wird. Dies schließt Unterstützung für allgemeine Funktionen wie z. B. Benutzer-Feedback-Bestätigung (als Unterstützung für die ShouldProcess-Funktion bezeichnet) und Unterstützung für Transaktionen. (Unterstützung für Transaktionen wurde in Windows PowerShell 2.0 eingeführt).

Weitere Informationen über die Syntax zum Deklarieren, die verwendet wird, an die **Cmdlet** Attribut, finden Sie unter [Cmdlet Attributdeklaration](./cmdlet-attribute-declaration.md).

## <a name="cmdlet-class-definition"></a>Cmdlet-Klassendefinition

Der folgende Code ist die Definition für eine GetProc Cmdlet-Klasse. Beachten Sie, Pascal-Schreibweise verwendet wird, und dass der Name der Klasse die Verb- und des-Cmdlets enthält.

[!code-csharp[GetProcessSample01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs#L33-L34 "GetProcessSample01.cs")]

## <a name="pascal-casing"></a>Pascal-Schreibweise

Wenn Sie Cmdlets Namen verwenden, verwenden Sie die Pascal-Schreibweise zur Groß-und Kleinschreibung. Z. B. die `Get-Item` und `Get-ItemProperty` Cmdlets anzuzeigen, die richtige Vorgehensweise Groß/Kleinschreibung zu verwenden, wenn Sie Cmdlets benennen.

## <a name="see-also"></a>Weitere Informationen

[System.Management.Automation.Cmdletattribute](/dotnet/api/System.Management.Automation.CmdletAttribute)

[CmdletAttribute-Deklaration](./cmdlet-attribute-declaration.md)

[-Cmdlet Verbnamen](./approved-verbs-for-windows-powershell-commands.md)

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
