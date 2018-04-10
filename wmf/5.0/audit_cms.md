---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 2704af76f038c03066f44ff36f8fb276f3a7d916
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2018
---
# <a name="cryptographic-message-syntax-cms-cmdlets"></a><span data-ttu-id="19894-102">CMS-Cmdlets (Cryptographic Message Syntax, Syntax verschlüsselter Nachrichten)</span><span class="sxs-lookup"><span data-stu-id="19894-102">Cryptographic Message Syntax (CMS) cmdlets</span></span>

<span data-ttu-id="19894-103">Der CMS-Cmdlets unterstützen die Ver- und Entschlüsselung von Inhalten mithilfe des IETF-Standardformats für kryptografisch geschützte Nachrichten, wie unter [RFC5652](https://tools.ietf.org/html/rfc5652) dokumentiert.</span><span class="sxs-lookup"><span data-stu-id="19894-103">The Cryptographic Message Syntax cmdlets support encryption and decryption of content using the IETF standard format for cryptographically protecting messages as documented by [RFC5652](https://tools.ietf.org/html/rfc5652).</span></span>

```powershell
Get-CmsMessage [-Content] <string>
Get-CmsMessage [-Path] <string>
Get-CmsMessage [-LiteralPath] <string>
Protect-CmsMessage [-To] <CmsMessageRecipient[]> [-Content] <string> [[-OutFile] <string>]
Protect-CmsMessage [-To] <CmsMessageRecipient[]> [-Path] <string> [[-OutFile] <string>]
Protect-CmsMessage [-To] <CmsMessageRecipient[]> [-LiteralPath] <string> [[-OutFile] <string>]
Unprotect-CmsMessage [-EventLogRecord] <EventLogRecord> [[-To] <CmsMessageRecipient[]>] [-IncludeContext]
Unprotect-CmsMessage [-Content] <string> [[-To] <CmsMessageRecipient[]>] [-IncludeContext]
Unprotect-CmsMessage [-Path] <string> [[-To] <CmsMessageRecipient[]>] [-IncludeContext]
Unprotect-CmsMessage [-LiteralPath] <string> [[-To] <CmsMessageRecipient[]>] [-IncludeContext]
```

<span data-ttu-id="19894-104">Der CMS-Verschlüsselungsstandard implementiert die Verschlüsselung mit öffentlichem Schlüssel, bei der die Schlüssel zum Verschlüsseln von Inhalten (der *öffentliche Schlüssel*) und zum Entschlüsseln von Inhalten (der *private Schlüssel*) getrennt sind.</span><span class="sxs-lookup"><span data-stu-id="19894-104">The CMS encryption standard implements public key cryptography, where the keys used to encrypt content (the *public key*) and the keys used to decrypt content (the *private key*) are separate.</span></span>

<span data-ttu-id="19894-105">Ihr öffentlicher Schlüssel kann umfassend freigegeben werden, da seine Daten nicht vertraulich sind.</span><span class="sxs-lookup"><span data-stu-id="19894-105">Your public key can be shared widely, and is not sensitive data.</span></span> <span data-ttu-id="19894-106">Wenn Inhalte mit diesem öffentlichen Schlüssel verschlüsselt sind, können sie nur mit Ihrem privaten Schlüssel entschlüsselt werden.</span><span class="sxs-lookup"><span data-stu-id="19894-106">If any content is encrypted with this public key, only your private key can decrypt it.</span></span> <span data-ttu-id="19894-107">Weitere Informationen finden Sie unter [Public-Key-Verschlüsselungsverfahren](https://en.wikipedia.org/wiki/Public-key_cryptography).</span><span class="sxs-lookup"><span data-stu-id="19894-107">For more information, see [Public-key cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography).</span></span>

<span data-ttu-id="19894-108">Um in PowerShell erkannt zu werden, benötigen Verschlüsselungszertifikate einen eindeutigen Schlüsselverwendungsbezeichner zum Kennzeichnen als Datenverschlüsselungszertifikate (wie die Bezeichner für „Codesignatur“ und „Verschlüsselte E-Mail“).</span><span class="sxs-lookup"><span data-stu-id="19894-108">To be recognized in PowerShell, encryption certificates require a unique key usage identifier (EKU) to identify them as data encryption certificates (like the identifiers for 'Code Signing', 'Encrypted Mail').</span></span>

<span data-ttu-id="19894-109">Hier ein Beispiel zum Erstellen eines Zertifikats, das sich gut für die Verschlüsselung von Dokumenten eignet:</span><span class="sxs-lookup"><span data-stu-id="19894-109">Here is an example of creating a certificate that is good for Document Encryption:</span></span>

```powershell
(Change the text in **Subject** to your name, email, or other identifier), and put in a file (i.e.: DocumentEncryption.inf):
[Version]
Signature = "$Windows NT$"
[Strings]
szOID\_ENHANCED\_KEY\_USAGE = "2.5.29.37"
szOID\_DOCUMENT\_ENCRYPTION = "1.3.6.1.4.1.311.80.1"
[NewRequest]
Subject = "<cn=me@somewhere.com>"
MachineKeySet = false
KeyLength = 2048
KeySpec = AT\_KEYEXCHANGE
HashAlgorithm = Sha1
Exportable = true
RequestType = Cert
KeyUsage = "CERT\_KEY\_ENCIPHERMENT\_KEY\_USAGE | CERT\_DATA\_ENCIPHERMENT\_KEY\_USAGE"
ValidityPeriod = "Years"
ValidityPeriodUnits = "1000"
[Extensions]
%szOID\_ENHANCED\_KEY\_USAGE% = "{text}%szOID\_DOCUMENT\_ENCRYPTION%"
```

<span data-ttu-id="19894-110">Führen Sie dann Folgendes aus:</span><span class="sxs-lookup"><span data-stu-id="19894-110">Then run:</span></span>
```powershell
certreq -new DocumentEncryption.inf DocumentEncryption.cer
```

<span data-ttu-id="19894-111">Nun können Sie Inhalte ver- und entschlüsseln:</span><span class="sxs-lookup"><span data-stu-id="19894-111">And you can now encrypt and decrypt content:</span></span>

```powershell
$protected = "Hello World" | Protect-CmsMessage -To "\*me@somewhere.com\*[](mailto:*leeholm@microsoft.com*)"
$protected
-----BEGIN CMS-----
MIIBqAYJKoZIhvcNAQcDoIIBmTCCAZUCAQAxggFQMIIBTAIBADA0MCAxHjAcBgNVBAMMFWxlZWhv
bG1AbWljcm9zb2Z0LmNvbQIQQYHsbcXnjIJCtH+OhGmc1DANBgkqhkiG9w0BAQcwAASCAQAnkFHM
proJnFy4geFGfyNmxH3yeoPvwEYzdnsoVqqDPAd8D3wao77z7OhJEXwz9GeFLnxD6djKV/tF4PxR
E27aduKSLbnxfpf/sepZ4fUkuGibnwWFrxGE3B1G26MCenHWjYQiqv+Nq32Gc97qEAERrhLv6S4R
G+2dJEnesW8A+z9QPo+DwYU5FzD0Td0ExrkswVckpLNR6j17Yaags3ltNVmbdEXekhi6Psf2MLMP
TSO79lv2L0KeXFGuPOrdzPAwCkV0vNEqTEBeDnZGrjv/5766bM3GW34FXApod9u+VSFpBnqVOCBA
DVDraA6k+xwBt66cV84OHLkh0kT02SIHMDwGCSqGSIb3DQEHATAdBglghkgBZQMEASoEEJbJaiRl
KMnBoD1dkb/FzSWAEBaL8xkFwCu0e1ZtDj7nSJc=
-----END CMS-----

$protected | Unprotect-CmsMessage
Hello World
```

<span data-ttu-id="19894-112">Parameter des Typs **CMSMessageRecipient** unterstützen Bezeichner in den folgenden Formaten:</span><span class="sxs-lookup"><span data-stu-id="19894-112">Any parameter of type **CMSMessageRecipient** supports identifiers in the following formats:</span></span>
- <span data-ttu-id="19894-113">Tatsächliches Zertifikat (wie vom Zertifikatanbieter abgerufen)</span><span class="sxs-lookup"><span data-stu-id="19894-113">An actual certificate (as retrieved from the certificate provider)</span></span>
- <span data-ttu-id="19894-114">Pfad zu einer Datei mit dem Zertifikat</span><span class="sxs-lookup"><span data-stu-id="19894-114">Path to the a file containing the certificate</span></span>
- <span data-ttu-id="19894-115">Pfad zu einem Verzeichnis mit dem Zertifikat</span><span class="sxs-lookup"><span data-stu-id="19894-115">Path to a directory containing the certificate</span></span>
- <span data-ttu-id="19894-116">Fingerabdruck des Zertifikats (dient zum Nachschlagen im Zertifikatspeicher)</span><span class="sxs-lookup"><span data-stu-id="19894-116">Thumbprint of the certificate (used to look in the certificate store)</span></span>
- <span data-ttu-id="19894-117">Name des Antragstellers des Zertifikats (dient zum Nachschlagen im Zertifikatspeicher)</span><span class="sxs-lookup"><span data-stu-id="19894-117">Subject name of the certificate (used to look in the certificate store)</span></span>

<span data-ttu-id="19894-118">Um Verschlüsselungszertifikate für Dokumente beim Zertifikatanbieter anzuzeigen, können Sie den dynamischen Parameter **-DocumentEncryptionCert** verwenden:</span><span class="sxs-lookup"><span data-stu-id="19894-118">To view document encryption certificates in the certificate provider, you can use the **-DocumentEncryptionCert** dynamic parameter:</span></span>

```powershell
dir -DocumentEncryptionCert
```