---
title: Sicherheitsparameter | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e199bba3-90d3-41ca-9d78-cb502e58508d
caps.latest.revision: 6
ms.openlocfilehash: c8b3f907a80d1f6125a5ac04236245503db76ed0
ms.sourcegitcommit: ce46e5098786e19d521b4bf948ff62d2b90bc53e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251301"
---
# <a name="security-parameters"></a>Sicherheitsparameter

Die folgende Tabelle enthält die empfohlenen Namen und die Funktionen für Parameter verwendet, um Informationen zur Sicherheit für einen Vorgang, z. B. Parameter bereitzustellen, die Zertifikatinformationen Schlüssel und Berechtigungen angeben.

|Parameter|Funktion|
|---|---|
|**ACL**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, um die Steuerungsebene für den Zugriff des Schutzes für einen Katalog oder für einen Uniform Resource Identifier (URI) angeben.|
|**CertFile**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, damit der Benutzer den Namen einer Datei angeben kann, die einen der folgenden enthält:<br>– Ein Base64- oder Distinguished Encoding Rules (DER) codierten x. 509-Zertifikat<br>– Eine Public Key Cryptography Standards (PKCS) #12-Datei, die mindestens ein Zertifikat und den Schlüssel enthält|
|**CertIssuerName**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter oder, damit der Benutzer den Namen des Ausstellers ein Zertifikat angeben kann, damit der Benutzer eine Teilzeichenfolge angeben kann.|
|**CertRequestFile**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, um den Namen einer Datei angeben, die eine Base64- oder DER-codiertes PKCS #10-zertifikatanforderung enthält.|
|**CertSerialNumber**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, um die fortlaufende Zahl angeben, die von der Zertifizierungsstelle ausgestellt wurde.|
|**CertStoreLocation**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, damit der Benutzer den Speicherort des Zertifikatspeichers angeben kann. Der Speicherort ist in der Regel einen Dateipfad an.|
|**CertSubjectName**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, oder, damit der Benutzer den Aussteller eines Zertifikats angeben kann, damit der Benutzer eine Teilzeichenfolge angeben kann.|
|**CertUsage**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, um die Schlüsselverwendung oder die erweiterte Schlüsselverwendung angeben. Der Schlüssel kann als ein wenig, einer kurzen Wartezeit einen Objektbezeichner (OID), zu maskieren oder eine Zeichenfolge dargestellt werden.|
|**Anmeldeinformationen**<br>Datentyp: [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential)|Implementieren Sie diesen Parameter, sodass das Cmdlet automatisch den Benutzer für einen Benutzernamen oder Kennwort fordert. Eine Eingabeaufforderung für beide wird angezeigt, wenn Sie ein vollständigen Satz von Anmeldeinformationen nicht direkt bereitgestellt wird.|
|**CSPName**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, damit der Benutzer den Namen des das Zertifikats-Dienstanbieter (CSP) angeben kann.|
|**CSPType**<br>Datentyp: Ganze Zahl|Implementieren Sie diesen Parameter, damit der Benutzer den Typ des CSP angeben kann.|
|**Gruppe**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, damit der Benutzer auf eine Auflistung von Prinzipalen für den Zugriff angeben kann. Weitere Informationen finden Sie unter der Beschreibung der **Principal** Parameter.|
|**KeyAlgorithm**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, damit der Benutzer den schlüsselgenerierungsalgorithmus für die Sicherheit angeben kann.|
|**KeyContainerName**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, damit der Benutzer den Namen des Schlüsselcontainers angeben kann.|
|**KeyLength**<br>Datentyp: Ganze Zahl|Implementieren Sie diesen Parameter, damit der Benutzer die Länge des Schlüssels in Bits angeben kann.|
|**Vorgang**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, sodass der Benutzer eine Aktion angeben kann, die auf einem geschützten Objekt ausgeführt werden können.|
|**Principal**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, damit der Benutzer eine eindeutige identifizierbare Entität für den Zugriff angeben kann.|
|**Berechtigungen**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, sodass die Benutzer über die Berechtigung angeben können, die ein Cmdlet zum Ausführen eines Vorgangs für eine bestimmte Entität muss.|
|**Berechtigungen**<br>Datentyp: Array von Berechtigungen|Implementieren Sie diesen Parameter, damit der Benutzer die Rechte angeben kann, die ein Cmdlet führen Sie den Vorgang für einen bestimmten Eintrag.|
|**Rolle**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, sodass eine Reihe von Vorgängen für die Benutzer angeben können, die von einer Entität ausgeführt werden können.|
|**SaveCred**<br>Datentyp: SwitchParameter|Implementieren Sie diesen Parameter, sodass Anmeldeinformationen, die zuvor vom Benutzer gespeichert wurden verwendet werden, wenn der Parameter angegeben wird.|
|**Bereich**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, damit der Benutzer die Gruppe der geschützten Objekte für das Cmdlet angeben kann.|
|**SID**<br>Datentyp: Zeichenfolge|Implementieren Sie diesen Parameter, sodass einen eindeutigen Bezeichner für die Benutzer angeben können, der einen Prinzipal darstellt.|
|**Trusted**<br>Datentyp: SwitchParameter|Implementieren Sie diesen Parameter, sodass Vertrauensebenen unterstützt werden, wenn der Parameter angegeben wird.|
|**TrustLevel**<br>Datentyp: Schlüsselwort|Implementieren Sie diesen Parameter, sodass die Vertrauensebene für die Benutzer angeben können, die unterstützt wird. Beispielsweise enthalten die möglichen Werte Internet, Intranet und Fulltrust.|

## <a name="see-also"></a>Weitere Informationen

[Cmdlet-Parameter](./cmdlet-parameters.md)

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
