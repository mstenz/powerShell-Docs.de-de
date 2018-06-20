---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Grundlagen von Windows PowerShell
ms.assetid: 6b3cbbc8-060c-4877-b00b-7300dbbe4e28
ms.openlocfilehash: b21c6cd84ea29d5e8085ccf8df2a5a9199e1d859
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2018
ms.locfileid: "30950532"
---
# <a name="windows-powershell-basics"></a>Grundlagen von Windows PowerShell
Grafische Benutzeroberflächen basieren auf Grundkonzepten, die den meisten Computerbenutzern bekannt sind. Benutzer verlassen sich beim Ausführen von Aufgaben auf die Vertrautheit mit diesen Oberflächen. Betriebssysteme bieten Benutzern eine grafische Darstellung von Elementen, die durchsucht werden können, meist mit Einblendmenüs für den Zugriff auf bestimmte Funktionen und Kontextmenüs für den Zugriff auf kontextspezifische Funktionalität.

Eine Befehlszeilenschnittstelle (Command-Line Interface, CLI) wie Windows PowerShell muss einen anderen Ansatz zum Offenlegen von Informationen befolgen, da sie nicht über Menüs oder grafische Systeme verfügt, die dem Benutzer helfen. Sie müssen Namen von Befehlen kennen, bevor Sie sie verwenden können. Obwohl Sie komplexe Befehle eingeben können, die mit den Features in einer grafischen Umgebung äquivalent sind, müssen Sie sich mit den am häufigsten verwendeten Befehlen und deren Parametern vertraut machen.

Die meisten CLIs bieten keine Muster, die dem Benutzer helfen, die Schnittstelle zu erlernen. Da CLIs die ersten Betriebssystemshells waren, wurden viele Befehls- und Parameternamen nach dem Zufallsprinzip ausgewählt. Dabei erhielten kurze und knappe Befehlsnamen meist den Vorzug vor aussagekräftigeren Namen. Obwohl Hilfesystemen und Befehlsentwurfsstandards in die meisten CLIs integriert wurden, sind diese in der Regel auf Kompatibilität mit den frühesten Befehlen ausgelegt, sodass der Befehlssatz weiter von Entscheidungen geprägt ist, die vor Jahrzehnten getroffen wurden.

Windows PowerShell wurde so entwickelt, dass die historischen CLI-Kenntnisse der Benutzer weiter zum Tragen kommen. In diesem Kapitel beschäftigen wir uns mit einigen grundlegenden Tools und Konzepten, mit deren Hilfe Sie Windows PowerShell schnell erlernen können. Dazu gehören:

- Verwenden von [Get-Command](/powershell/module/Microsoft.PowerShell.Core/get-command)

- Verwenden von [cmd.exe](/windows-server/administration/windows-commands/cmd) und [UNIX-Befehlen](/windows/wsl/reference)

- [Verwenden der Vervollständigung mit der TAB-TASTE](../../core-powershell/console/using-tab-expansion.md)

- [Verwenden von „Get-Help“](./getting-detailed-help-information.md)