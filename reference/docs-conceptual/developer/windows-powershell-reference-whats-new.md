---
title: 'Windows PowerShell-Referenz: Neuerungen'
ms.date: 09/13/2016
ms.topic: article
ms.openlocfilehash: 364d081ddf2f87ceeaa47732266a35f4a126246f
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366089"
---
# <a name="whats-new"></a>Neues

Windows PowerShell 2,0 bietet die folgenden neuen Features zum Schreiben von Cmdlets, Anbietern und Host Anwendungen.

## <a name="modules"></a>Module

Sie können Windows PowerShell-Lösungen jetzt mithilfe von Modulen Verpacken und verteilen. Mit Modulen können Sie Ihren Windows PowerShell-Code in eigenständige, wiederverwendbare Einheiten partitionieren, organisieren und abstrahieren. Weitere Informationen zu Modulen finden Sie unterschreiben eines Windows PowerShell-Moduls.

## <a name="the-powershell-class"></a>Die PowerShell-Klasse

Die PowerShell-Klasse stellt eine einfachere Lösung zum Erstellen von Anwendungen bereit, die als Host Anwendungen bezeichnet werden, die Programm gesteuert Befehle ausführen. Mit dieser Klasse können Sie eine Pipeline von Befehlen erstellen, den zum Ausführen der Befehle verwendeten Runspace angeben und die Befehle synchron oder asynchron aufrufen.

## <a name="the-runspacepool-class"></a>Die runspacepool-Klasse

Mit Runspace-Pools können Sie mehrere Runspaces erstellen, indem Sie einen einzelnen-Befehl verwenden. Die Methode "samaterunspacepool" bietet mehrere über Ladungen, mit denen Runspaces erstellt werden können, die über dieselben Funktionen verfügen, z. b. den gleichen Host, den anfänglichen Sitzungs Status und die Verbindungsinformationen.

## <a name="the-initialsessionstate-class"></a>Die initialsessionstate-Klasse

Die initialsessionstate-Klasse ermöglicht es Ihnen, eine Sitzungs Zustands Konfiguration zu erstellen, die verwendet wird, wenn ein Runspace geöffnet wird. Sie können eine benutzerdefinierte Konfiguration erstellen, eine Standardkonfiguration, die die von mshshort bereitgestellten Befehle enthält, sowie eine Konfiguration, deren Befehle basierend auf den Funktionen der Sitzung eingeschränkt sind.

## <a name="remote-runspaces"></a>Remote-Runspaces

Sie können nun Runspaces erstellen, die auf Remote Computern geöffnet werden können, sodass Sie Befehle auf dem Remote Computer ausführen und die Ergebnisse lokal erfassen können. Um einen Remoterunspace zu erstellen, müssen Sie beim Erstellen des Runspace Informationen über die Remote Verbindung angeben. Beispiele finden Sie in den Methoden "up-Methode" und "kreaterunspacepool". Die Verbindungsinformationen werden von der runspaceconnectioninfo-Klasse definiert.

## <a name="private-runspace-elements"></a>Private Runspace-Elemente

Sie können nun Runspaces erstellen, deren Elemente öffentlich oder privat sind. Auf diese Weise können Sie Runspaces erstellen, deren Elemente für den Runspace verfügbar sind, aber für den Benutzer nicht verfügbar sind. Sehen Sie sich die Klasse "einschräninedsessionstateentry" an, um herauszufinden, welche Elemente des Runspace als privat fest gegeben werden können.

## <a name="runspace-threading-modes-and-apartment-state"></a>Runspace-Threading Modi und Apartment Zustand

Sie können jetzt angeben, wie Threads erstellt und verwendet werden, wenn Befehle in einem Runspace ausgeführt werden. Weitere Informationen finden Sie in den Eigenschaften "System. Management. Automation. Runspaces. Runspace. threadoptions" und "System. Management. Automation. Runspaces. runspacepool. threadoptions".

Nun können Sie den Apartment Zustand der Threads, die zum Ausführen von Befehlen in einem Runspace verwendet werden, erhalten. Weitere Informationen finden Sie in den Eigenschaften "System. Management. Automation. Runspaces. Runspace. ApartmentState" und "System. Management. Automation. Runspaces. runspacepool. ApartmentState".

## <a name="transaction-cmdlets"></a>Transaktions-Cmdlets

Jetzt können Sie Cmdlets erstellen, die innerhalb einer Transaktion verwendet werden können. Wenn ein Cmdlet in einer Transaktion verwendet wird, sind seine Aktionen temporär, und Sie können von den von Windows PowerShell bereitgestellten Transaktions-Cmdlets akzeptiert oder abgelehnt werden.

Weitere Informationen zu Transaktionen finden Sie unter How to Support Transactions.

## <a name="transaction-provider"></a>Transaktions Anbieter

Sie können jetzt Anbieter erstellen, die innerhalb einer Transaktion verwendet werden können. Ähnlich wie bei-Cmdlets, wenn ein Anbieter in einer Transaktion verwendet wird, sind seine Aktionen temporär und können durch die von Windows PowerShell bereitgestellten Transaktions-Cmdlets akzeptiert oder abgelehnt werden.

Weitere Informationen zum Angeben der Unterstützung für Transaktionen innerhalb einer Anbieter Klasse finden Sie in der System. Management. Automation. Provider. cmdletproviderattribute. providerfunktionalitäten-Eigenschaft.

## <a name="job-cmdlets"></a>Auftrags-Cmdlets

Sie können jetzt Cmdlets schreiben, die ihre Aktion als Auftrag ausführen können. Diese Aufträge werden im Hintergrund ausgeführt, ohne mit der aktuellen Sitzung zu interagieren. Weitere Informationen darüber, wie Windows PowerShell Aufträge unterstützt, finden Sie unter Hintergrund Aufträge.

## <a name="cmdlet-output-types"></a>Cmdlet-Ausgabetypen

Sie können jetzt die .NET Framework Typen angeben, die von den Cmdlets zurückgegeben werden, indem Sie beim Schreiben der Cmdlets das OutputType-Attribut deklarieren. Dadurch können andere Typen von Objekten ermitteln, die von einem Cmdlet zurückgegeben werden, indem Sie sich die OutputType-Eigenschaft des Cmdlets ansehen.

## <a name="event-support"></a>Ereignis Unterstützung

Sie können jetzt Cmdlets schreiben, die Ereignisse hinzufügen und nutzen. Weitere Informationen finden Sie unter der Klasse "pEvent".

## <a name="proxy-commands"></a>Proxy Befehle

Sie können jetzt Proxy Befehle schreiben, mit denen ein anderer Befehl ausgeführt werden kann. Mit einem Proxy Befehl können Sie steuern, welche Funktionen des Quell-Cmdlets für den Benutzer verfügbar sind. Beispielsweise können Sie einen Proxy Befehl erstellen, der einen Parameter entfernt, der vom Quell Befehl bereitgestellt wird. Weitere Informationen finden Sie in der ProxyCommand-Klasse.

## <a name="multiple-choice-prompts"></a>Mehrere Auswahl Aufforderungen

Sie können jetzt Anwendungen schreiben, die Eingabe Aufforderungen bereitstellen, die es dem Benutzer ermöglichen, mehrere Optionen auszuwählen. Weitere Informationen finden Sie in der ihustuisupportsmultiplechoiceselection-Schnittstelle.

## <a name="interactive-sessions"></a>Interaktive Sitzungen

Sie können jetzt Anwendungen schreiben, mit denen eine interaktive Sitzung auf einem Remote Computer gestartet und beendet werden kann.
Weitere Informationen finden Sie in der ihostsupportsinteractivesession-Schnittstelle.

## <a name="custom-cmdlet-help-for-providers"></a>Hilfe zu benutzerdefinierten Cmdlets für Anbieter

Sie können jetzt angepasste Hilfe Themen für die Anbieter-Cmdlets erstellen. In den Hilfe Themen zu benutzerdefinierten Cmdlets kann erläutert werden, wie das Cmdlet im Anbieter Pfad und den speziellen Features funktioniert, einschließlich der dynamischen Parameter, die der Anbieter zum Cmdlet hinzufügt.
