---
title: "Beispielvorlage für das Hochschreiben eines bekannten Problems oder einer Einschränkung"
contributor: 
translationtype: Human Translation
ms.sourcegitcommit: a952a27ec1695ce9951c352446194cf72d18f50a
ms.openlocfilehash: cfe0a6562743f1df81acb81e33c120cb67f9042c

---

>Hinweis: Vorschlag für einen aussagekräftigen Namen und eine Kurzbeschreibung bereitstellen

## Beispiel: Fehlerhafte „ExecutionPolicy“-Fehler ##
Unter Windows 7 kann die Verwendung von PowerShell-Modulen und DSC-Ressourcen zu Fehlern führen, die zu „ExecutionPolicy“ gemeldet werden.

### Lösung

Legen Sie als Lösung **ExecutionPolicy** auf **RemoteSigned** fest, indem Sie den folgenden Befehl mit erhöhten Rechten in einer PowerShell-Sitzung ausführen (Als Administrator ausführen):

```powershell
Set-ExecutionPolicy RemoteSigned
```



<!--HONumber=Aug16_HO3-->


