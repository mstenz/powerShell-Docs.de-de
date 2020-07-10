---
title: Methoden für erweiterte Typsystem Klassen
ms.date: 07/09/2020
ms.topic: conceptual
ms.openlocfilehash: 97c11093d2faeb2a73b349c479d6de34ae2ea788
ms.sourcegitcommit: d26e2237397483c6333abcf4331bd82f2e72b4e3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/10/2020
ms.locfileid: "86217935"
---
# <a name="ets-class-methods"></a>ETS-Klassen Methoden

ETS-Methoden sind Member, die Argumente annehmen, möglicherweise Ergebnisse zurückgeben und nicht auf der linken Seite eines Ausdrucks angezeigt werden können. Zu den Methoden, die in den ETS verfügbar sind, gehören Code, Windows PowerShell und Skript Methoden.

> [!NOTE]
> Aus Skripts wird auf Methoden mit der gleichen Syntax wie andere Member zugegriffen, wobei am Ende des Methoden namens Klammern hinzugefügt werden.

## <a name="code-methods"></a>Code Methoden

Eine Code Methode ist ein erweiterter Member, der in einer CLR-Sprache definiert ist. Sie bietet eine ähnliche Funktionalität wie eine Methode, die für ein Basisobjekt definiert ist. eine Code Methode kann jedoch dynamisch einem **psobject** -Objekt hinzugefügt werden. Damit eine Code Methode verfügbar wird, muss ein Entwickler die-Eigenschaft in einer CLR-Sprache schreiben, kompilieren und die resultierende Assembly versenden. Diese Assembly muss im Runspace verfügbar sein, in dem die Code Methode erwünscht ist. Beachten Sie, dass eine Implementierung der Code Methode Thread sicher sein muss. Der Zugriff auf diese Methoden erfolgt über [pscodemethod](/dotnet/api/system.management.automation.pscodemethod) -Objekte, die die folgenden öffentlichen Methoden und Eigenschaften bereitstellen.

- `PSCodeMethod.Copy`Method: erstellt eine exakte Kopie des **pscodemethod** -Objekts.
- `PSCodeMethod.Invoke(System.Object[])`Method: Ruft die zugrunde liegende Code Methode auf.
- `PSCodeMethod.ToString`Method: konvertiert das **pscodemethod** -Objekt in eine Zeichenfolge.
- `PSCodeMethod.CodeReference`Property: Ruft die zugrunde liegende Methode ab, auf der die Code Methode basiert.
- **Psmembership Info. isInstance** -Eigenschaft: Ruft einen **booleschen** Wert ab, der die Quelle des Members angibt.
- **Pscodemethod. Membership Type** -Eigenschaft: Ruft eine **psmembership Types. codemethod** -Enumerationskonstante ab, die diese Methode als Code Methode identifiziert.
- **PSMemberInfo.Name** Property: Ruft den Namen der zugrunde liegenden Code Methode ab.
- **Pscodemethod. overloaddefinitions** -Eigenschaft: Ruft eine Definition aller über Ladungen der zugrunde liegenden Code Methode ab.
- **Pscodemethod. typameofvalue** -Eigenschaft: Ruft den vollständigen Namen der Code Methode ab.
- **Psmembership Info. Value** -Eigenschaft: Ruft das **pscodemethod** -Objekt ab.

## <a name="windows-powershell-methods"></a>Windows PowerShell-Methoden

Eine PowerShell-Methode ist eine CLR-Methode, die für das Basisobjekt definiert ist oder über einen Adapter zugänglich gemacht wird. Der Zugriff auf diese Methoden erfolgt über **psmethod** -Objekte, die die folgenden öffentlichen Methoden und Eigenschaften bereitstellen.

- `PSMethod.Copy`Method: erstellt eine exakte Kopie des **psmethod** -Objekts.
- `PSMethod.Invoke(System.Object[])`Method: Ruft die zugrunde liegende Methode auf.
- `PSMethod.ToString`Method: konvertiert das **psmethod** -Objekt in eine Zeichenfolge.
- **Psmembership Info. isInstance** -Eigenschaft: Ruft einen **booleschen** Wert ab, der die Quelle des Members angibt.
- **Psmethod. Membership Type** -Eigenschaft: Ruft eine **psmembership Types. Method** -Enumerationskonstante ab, die diese Methode als PowerShell-Methode identifiziert.
- **PSMemberInfo.Name** -Eigenschaft: Ruft den Namen der zugrunde liegenden Methode ab.
- **Psmethod. overloaddefinitions** -Eigenschaft: Ruft die Definitionen aller über Ladungen der zugrunde liegenden Methode ab.
- **Psmethod. typameofvalue** -Eigenschaft: Ruft den ETS-Typ dieser Methode ab.
- **Psmembership Info. Value** -Eigenschaft: Ruft das **psmethod** -Objekt ab.

## <a name="script-methods"></a>Skript Methoden

Eine Skript Methode ist ein erweiterter Member, der in der PowerShell-Sprache definiert ist. Sie bietet eine ähnliche Funktionalität wie eine Methode, die für ein Basisobjekt definiert ist. eine Skript Methode kann jedoch dynamisch einem **psobject** -Objekt hinzugefügt werden. Der Zugriff auf diese Methoden erfolgt über [psscriptmethod](/dotnet/api/system.management.automation.psscriptmethod) -Objekte, die die folgenden öffentlichen Methoden und Eigenschaften bereitstellen.

- `PSScriptMethod.Copy`Method: erstellt eine exakte Kopie des **psscriptmethod** -Objekts.
- `PSScriptMethod.Invoke(System.Object[])`Method: Ruft die zugrunde liegende Skript Methode auf.
- `PSScriptMethod.ToString`Method: konvertiert das **psscriptmethod** -Objekt in eine Zeichenfolge.
- **Psmembership Info. isInstance** -Eigenschaft: Ruft einen **booleschen** Wert ab, der die Quelle des Members angibt.
- **Psscriptmethod. Membership Type** -Eigenschaft: Ruft eine **psmembership Types. ScriptMethod** -Enumerationskonstante ab, die diese Methode als Skript Methode identifiziert.
- **PSMemberInfo.Name** Property: Ruft den Namen der zugrunde liegenden Code Methode ab.
- **Psscriptmethod. overloaddefinitions** -Eigenschaft: Ruft die Definitionen aller über Ladungen der zugrunde liegenden Skript Methode ab.
- **Psscriptmethod. tytzameofvalue** -Eigenschaft: Ruft den ETS-Typ dieser Methode ab.
- **Psscriptmethod. Script** -Eigenschaft: Ruft das Skript ab, das verwendet wird, um die Methode aufzurufen.
- **Psmembership Info. Value** -Eigenschaft: Ruft das **psscriptmethod** -Objekt ab.
