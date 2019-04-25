---
title: Allgemeine Workflowparameter | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d5891467-8e13-484d-b7af-32e6bffab35d
caps.latest.revision: 4
ms.openlocfilehash: b2e8f272a82ee03de306fd8eac45e109142f6284
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080406"
---
# <a name="common-workflow-parameters"></a>Allgemeine Workflowparameter

Eine Workflow-Aktivität, die aus einem Windows PowerShell-Cmdlet generiert definiert eine Reihe von Parametern, die gerade üblich, alle Aktivitäten. Beim Erstellen, damit Erstellern von Workflows, Aktivitäten anpassen können, kann eine Teilmenge dieser Parameter angegeben werden. Einer anderen Teilmenge dieser Parameter kann vom Benutzer angegeben werden, wenn die Aktivität aufgerufen.

Die allgemeinen Workflowparameter sind wie folgt in verschiedene Kategorien gruppiert.

## <a name="connectivity-parameters"></a>Konnektivitätsparameter

|Name|Type|Beschreibung|Kann vom Benutzer zum Zeitpunkt der Ausführung werden angegeben?|Kann vom workflowautor beim Erstellen werden angegeben?|Kann vom workflowautor bei der Instanziierung werden angegeben?|
|----------|----------|-----------------|-----------------------------------------------------|------------------------------------------------------------|-----------------------------------------------------------|
|PSComputerName|String[]|Eine Liste von Computernamen für die Aufträge zu starten.|Ja|Ja|Ja|
|PSCredential|[System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential)|Anmeldeinformationen für die Verwendung für die Anmeldung bei den Computern, die anhand des PSComputerName-Parameters. Dieser Parameter ist nur gültig, wenn PSComputerName angegeben wird.|Ja|Ja|Ja|
|PSPort|UInt32|Der Port, mit dem der Workflow ausgeführt werden.|Ja|Ja|Ja|
|PSUseSSL|Boolescher Wert|Verwenden Sie Secure Sockets Layer (SSL)-Protokoll zum Herstellen einer sicheren Verbindung mit dem Remotecomputer zum Ausführen des Workflows.|Ja|Ja|Ja|
|PSConfigurationName|Zeichenfolge|Die Sitzungskonfiguration verwendet, um den Workflow auszuführen.|Ja|Ja|Ja|
|PSApplicationName|Zeichenfolge|Die Anwendung-Namensteil des Verbindungs-URI für die Ausführung des Workflows. Verwenden Sie diesen Parameter nur, wenn Sie nicht den ConnectionURI-Parameter verwenden.|Ja|Ja|Ja|
|PSThrottleLimit|UInt32|Die maximale Anzahl gleichzeitiger Verbindungen, die für die workflowausführung hergestellt werden kann.|Ja|TBD|Ja|
|PSConnectionURI|String[]|Ein Array von vollqualifizierten URIs, die die Endpunkte für die interaktive Sitzungen verwendet, um die workflowausführung angeben.|Ja|Ja|Ja|
|PSAllowRedirection|Boolescher Wert|Gibt an, ob die Umleitung dieser Verbindung an einen alternativen URI für den Workflow zu ermöglichen.|Ja|Ja|Ja|
|PSSessionOption|[System.Management.Automation.Remoting.Pssessionoption](/dotnet/api/System.Management.Automation.Remoting.PSSessionOption)|Erweiterte Optionen für die Sitzung, die zum Ausführen des Workflows verwendet.|Ja|Ja|Ja|
|PSAuthentication|[System.Management.Automation.Runspaces.Authenticationmechanism](/dotnet/api/System.Management.Automation.Runspaces.AuthenticationMechanism)|Der Wert der [System.Management.Automation.Runspaces.Authenticationmechanism](/dotnet/api/System.Management.Automation.Runspaces.AuthenticationMechanism) Enumeration, der angibt, den Authentifizierungsmechanismus verwendet, um die Anmeldeinformationen des Benutzers zu authentifizieren.|Ja|Ja|Ja|
|PSCertificateThumbprint|Zeichenfolge|Die digitale öffentliches Schlüsselzertifikat (X509) eines Benutzerkontos mit der Berechtigung zum Ausführen des Workflows.|Ja|Ja|Ja|

### <a name="behavior-parameters"></a>Parameter zum Verhalten