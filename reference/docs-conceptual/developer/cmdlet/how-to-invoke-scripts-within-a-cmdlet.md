---
title: Aufrufen von Skripts in einem Cmdlet | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cc0bc6ce-48a5-4d9c-927e-636bca743e9f
caps.latest.revision: 9
ms.openlocfilehash: 7dcb8bc20ab56225764854f9dc6fdfd858ed7451
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364409"
---
# <a name="how-to-invoke-scripts-within-a-cmdlet"></a>Aufrufen von Skripts in einem Cmdlet

Dieses Beispiel zeigt, wie ein Skript aufgerufen wird, das für ein Cmdlet bereitgestellt wird. Das Skript wird vom Cmdlet ausgeführt, und die Ergebnisse werden an das Cmdlet als Sammlung von [System. Management. Automation. psobject](/dotnet/api/System.Management.Automation.PSObject) -Objekten zurückgegeben.

## <a name="to-invoke-a-script-block"></a>So rufen Sie einen Skriptblock auf

1. Mit dem Befehl wird überprüft, ob ein Skriptblock für das Cmdlet bereitgestellt wurde. Wenn ein Skriptblock angegeben wurde, ruft der Befehl den Skriptblock mit den erforderlichen Parametern auf.

    ```csharp
    if (script != null)
    {
      WriteDebug("Executing script block.");

      // Invoke the script block with the required arguments.
      Collection<PSObject> PSObjects =
                     script.Invoke(
                                   line,
                                   simpleMatch,
                                   caseSensitive
                                  );
    ```

2. Anschließend durchläuft das Skript die zurückgegebene Auflistung von [System. Management. Automation. psobject](/dotnet/api/System.Management.Automation.PSObject) -Objekten und führt die erforderlichen Vorgänge aus.

    ```c
    foreach (PSObject psObject in psObjects)
    {
      if (LanguagePrimitives.IsTrue(psObject))
      {
        result = new MatchInfo();
        result.Line = line;
        result.IgnoreCase = !caseSensitive;

        break;
      }
    }

    ```

## <a name="see-also"></a>Weitere Informationen

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
