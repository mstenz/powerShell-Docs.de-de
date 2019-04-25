---
title: Windows PowerShell-Referenz – Neuigkeiten
ms.date: 09/13/2016
ms.topic: article
ms.openlocfilehash: 364d081ddf2f87ceeaa47732266a35f4a126246f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080525"
---
# <a name="whats-new"></a>Neues

Windows PowerShell 2.0 bietet die folgenden neuen Features für die Verwendung, beim Schreiben von Cmdlets, Anbietern und Hosten von Anwendungen.

## <a name="modules"></a>Module

Sie können jetzt Verpacken und Verteilen von Windows PowerShell-Lösungen mithilfe von Modulen. Module können Sie Partitionen, organisieren und abstrahieren von Ihren Windows PowerShell-Code in eigenständige, wieder verwendbaren Einheiten. Weitere Informationen zu Modulen finden Sie in das Schreiben eines Windows PowerShell-Moduls.

## <a name="the-powershell-class"></a>Die PowerShell-Klasse

Die PowerShell-Klasse bietet es sich um eine einfachere Lösung zum Erstellen von Anwendungen, die als hostanwendungen, die Befehle programmgesteuert ausführen. Diese Klasse können Sie zum Erstellen einer Pipeline von Befehlen geben den Runspace, der verwendet wird, um die Befehle auszuführen, und geben Sie die Befehle aufrufen, synchron oder asynchron.

## <a name="the-runspacepool-class"></a>Die RunspacePool-Klasse

Runspace-Pools können Sie mehreren Runspaces mithilfe eines einzelnen Aufrufs zu erstellen. Die Methode CreateRunspacePool bietet mehrere Überladungen, die zum Erstellen von Runspaces, die die gleichen Funktionen, z. B. die gleichen Host, den anfänglichen Sitzungsstatus und die Verbindungsinformationen verwendet werden können.

## <a name="the-initialsessionstate-class"></a>Die InitialSessionState-Klasse

Die InitialSessionState-Klasse können Sie eine Status-Sitzungskonfiguration zu erstellen, die verwendet wird, wenn ein Runspace geöffnet wird. Sie können eine benutzerdefinierte Konfiguration verwenden, eine Standardkonfiguration, die die Befehlen Mshshort enthält und eine Konfiguration, dessen Befehle beschränkt sind, basierend auf den Funktionen der Sitzung, zu erstellen.

## <a name="remote-runspaces"></a>Remote runspaces

Sie können jetzt erstellen Runspaces, die geöffnet werden, können auf den Remotecomputern können Sie auf dem Remotecomputer Befehle ausführen und die Ergebnisse lokal erfassen. Um einen Remoterunspace erstellen zu können, müssen Sie Informationen über die Remoteverbindung angeben, wenn den Runspace zu erstellen. Siehe Beispiele für die CreateRunspace und CreateRunspacePool-Methoden. Informationen für die Verbindung wird durch die RunspaceConnectionInfo-Klasse definiert.

## <a name="private-runspace-elements"></a>Private Runspace-Elemente

Sie können jetzt Runspaces erstellen, dessen Elemente öffentlich oder privat sind. Dadurch können Sie zum Erstellen von Runspaces, dessen Elemente mit dem Runspace verfügbar sind, jedoch sind nicht für den Benutzer verfügbar. Finden Sie unter der ConstrainedSessionStateEntry-Klasse, um herauszufinden, welche Elemente der Runspace private vorgenommen werden können.

## <a name="runspace-threading-modes-and-apartment-state"></a>Threading-Modi und Apartmentzustand Runspace

Sie können jetzt angeben, wie Threads erstellt und verwendet werden, beim Ausführen der Befehle in einem Runspace. Siehe die System.Management.Automation.Runspaces.Runspace.ThreadOptions und System.Management.Automation.Runspaces.RunspacePool.ThreadOptions.

Sie erhalten nun den Apartmentzustand des Threads, die zum Ausführen von Befehlen in einem Runspace verwendet werden. Siehe die System.Management.Automation.Runspaces.Runspace.ApartmentState und System.Management.Automation.Runspaces.RunspacePool.ApartmentState.

## <a name="transaction-cmdlets"></a>Transaktions-cmdlets

Sie können nun Cmdlets erstellen, die innerhalb einer Transaktion verwendet werden können. Wenn ein Cmdlet in einer Transaktion verwendet wird, die Aktionen sind temporär, und sie akzeptiert oder abgelehnt wird, durch die Transaktions-Cmdlets von Windows PowerShell bereitgestellt werden können.

Weitere Informationen über Transaktionen finden Sie unter Vorgehensweise unterstützen Transaktionen.

## <a name="transaction-provider"></a>Transaction-Anbieter

Sie können jetzt Anbieter erstellen, die innerhalb einer Transaktion verwendet werden können. Ähnlich wie bei Cmdlets, wenn ein Anbieter in einer Transaktion verwendet wird, die Aktionen sind temporär, und sie akzeptiert oder abgelehnt wird, durch die Transaktions-Cmdlets von Windows PowerShell bereitgestellt werden können.

Weitere Informationen zum Angeben von Unterstützung für die Transaktion innerhalb einer Klasse finden Sie unter der System.Management.Automation.Provider.CmdletProviderAttribute.ProviderCapabilities-Eigenschaft.

## <a name="job-cmdlets"></a>Job-cmdlets

Sie können nun die Cmdlets schreiben, die ihre Aktionen als Auftrag ausgeführt werden können. Diese Aufträge werden im Hintergrund ohne Interaktion mit der aktuellen Sitzung ausgeführt. Weitere Informationen dazu, wie das Windows PowerShell-Aufträge unterstützt finden Sie unter Hintergrundaufträge.

## <a name="cmdlet-output-types"></a>Cmdlet-Ausgabetypen

Sie können jetzt .NET Framework-Typen angeben, die durch Ihre Cmdlets zurückgegeben werden, durch die OutputType-Attribut deklarieren, wenn Ihre Cmdlets schreiben. Dadurch können andere Benutzer zu bestimmen, welche Art von Objekten von einem Cmdlet zurückgegeben werden, anhand der OutputType-Eigenschaft des-Cmdlets.

## <a name="event-support"></a>Ereignisunterstützung

Sie können nun die Cmdlets schreiben, die Nutzung von Ereignissen und hinzufügen. Siehe PSEvent-Klasse.

## <a name="proxy-commands"></a>Proxy-Befehle

Sie können nun die Proxy-Befehle schreiben, mit denen ein anderer Befehl ausgeführt werden können. Ein Proxybefehl können Sie steuern, welche Funktion des Quell-Cmdlets für den Benutzer verfügbar ist. Beispielsweise können Sie einen Proxybefehl erstellen, der einen Parameter entfernt, der durch den Befehl "Quelle" bereitgestellt wird. Siehe ProxyCommand-Klasse.

## <a name="multiple-choice-prompts"></a>Mehrere aufforderungen der Auswahl

Sie können nun Anwendungen schreiben, die Anweisungen bereitstellen können, mit die den Benutzer mehrere Optionen auswählen können. Sehen Sie die IHostUISupportsMultipleChoiceSelection-Benutzeroberfläche

## <a name="interactive-sessions"></a>Interaktive Sitzungen

Sie können nun Anwendungen schreiben, die gestartet oder beendet eine interaktive Sitzung auf einem Remotecomputer befindet.
Sehen Sie die IHostSupportsInteractiveSession-Benutzeroberfläche.

## <a name="custom-cmdlet-help-for-providers"></a>Benutzerdefinierte Cmdlet-Hilfe für Anbieter

Sie können jetzt benutzerdefinierte Hilfethemen für die Anbieter-Cmdlets erstellen. Benutzerdefinierte Cmdlet-Hilfethemen können erklären, wie das Cmdlet funktioniert in der Anbieter Pfad und Dokument spezielle Features, einschließlich der dynamische Parameter, die der Anbieter das-Cmdlet hinzufügt.
