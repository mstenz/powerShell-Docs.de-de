---
title: Allgemeine Workflow Parameter | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d5891467-8e13-484d-b7af-32e6bffab35d
caps.latest.revision: 4
ms.openlocfilehash: c436ad017be72d97c26552c85d9fd212892ec731
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83557515"
---
# <a name="common-workflow-parameters"></a>Allgemeine Workflowparameter

Eine Workflow Aktivität, die von einem Windows PowerShell-Cmdlet generiert wird, definiert eine Reihe von Parametern, die für alle Aktivitäten gemeinsam sind. Eine Teilmenge dieser Parameter kann zum Zeitpunkt der Erstellung angegeben werden, damit Workflow Autoren Aktivitäten anpassen können. Eine andere Teilmenge dieser Parameter kann vom Benutzer angegeben werden, wenn die-Aktivität aufgerufen wird.

Die allgemeinen Workflow Parameter werden wie folgt in verschiedene Kategorien eingeteilt.

## <a name="connectivity-parameters"></a>Konnektivitätsparameter

|Name|Typ|Beschreibung|Kann vom Endbenutzer zur Ausführungszeit angegeben werden?|Kann vom Workflow Autor zum Zeitpunkt der Erstellung angegeben werden?|Kann vom Workflow Autor bei der Instanziierung angegeben werden?|
|----------|----------|-----------------|-----------------------------------------------------|------------------------------------------------------------|-----------------------------------------------------------|
|PSComputerName|String[]|Eine Liste von Computernamen, für die Aufträge gestartet werden sollen.|Ja|Ja|Ja|
|PSCredential|[System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential)|Die Anmelde Informationen für die Authentifizierung, die für die Anmeldung bei den durch den pscomputername-Parameter angegebenen Computern verwendet werden sollen. Dieser Parameter ist nur gültig, wenn pscomputername angegeben ist.|Ja|Ja|Ja|
|PSPort|UInt32|Der Port, der zum Ausführen des Workflows verwendet werden soll.|Ja|Ja|Ja|
|PSUseSSL|Boolean|Verwenden Sie Secure Sockets Layer (SSL)-Protokoll, um eine sichere Verbindung mit dem Remote Computer herzustellen, um den Workflow auszuführen.|Ja|Ja|Ja|
|PSConfigurationName|String|Die Sitzungs Konfiguration, die zum Ausführen des Workflows verwendet wird.|Ja|Ja|Ja|
|PSApplicationName|String|Der Anwendungs Namensteil des Verbindungs-URI für die Workflow Ausführung. Verwenden Sie diesen Parameter nur, wenn Sie nicht den ConnectionUri-Parameter verwenden.|Ja|Ja|Ja|
|PSThrottleLimit|UInt32|Die maximale Anzahl gleichzeitiger Verbindungen, die zum Ausführen des Workflows hergestellt werden können.|Ja|TBD|Ja|
|PSConnectionURI|String[]|Ein Array von voll qualifizierten URIs, die die Endpunkte für die interaktiven Sitzungen angeben, die zum Ausführen des Workflows verwendet werden.|Ja|Ja|Ja|
|PSAllowRedirection|Boolean|Gibt an, ob die Umleitung dieser Verbindung an einen alternativen URI zum Ausführen des Workflows zulässig ist.|Ja|Ja|Ja|
|PSSessionOption|[System. Management. Automation. Remoting. pssessionoption](/dotnet/api/System.Management.Automation.Remoting.PSSessionOption)|Erweiterte Optionen für die Sitzung, die zum Ausführen des Workflows verwendet wird.|Ja|Ja|Ja|
|PSAuthentication|[System. Management. Automation. Runspaces. authenticationmechanism](/dotnet/api/System.Management.Automation.Runspaces.AuthenticationMechanism)|Ein Wert der [System. Management. Automation. Runspaces. authenticationmechanism](/dotnet/api/System.Management.Automation.Runspaces.AuthenticationMechanism) -Enumeration, der den Authentifizierungsmechanismus angibt, der zum Authentifizieren der Anmelde Informationen des Benutzers verwendet wird.|Ja|Ja|Ja|
|PSCertificateThumbprint|String|Das digitale Zertifikat für öffentliche Schlüssel (X509) eines Benutzerkontos, das über die Berechtigung zum Ausführen des Workflows verfügt.|Ja|Ja|Ja|

### <a name="behavior-parameters"></a>Verhaltensparameter
