---
title: 'So wird''s gemacht: Verwenden von Profilen in Windows PowerShell ISE'
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: 0219626a-6da5-4acc-b630-d058e8b29cc6
translationtype: Human Translation
ms.sourcegitcommit: 3222a0ba54e87b214c5ebf64e587f920d531956a
ms.openlocfilehash: d934eac30da3d6a180d0dd92194eedbfd4cd8844

---

# So wird's gemacht: Verwenden von Profilen in Windows PowerShell ISE
In diesem Thema wird erklärt, wie Profile in Windows PowerShell® Integrated Scripting Environment (ISE) verwendet werden können. Es empfiehlt sich, dass Sie die Aufgaben in diesem Abschnitt erst ausführen, nachdem Sie [about_Profiles [v4]](https://technet.microsoft.com/en-us/library/e1d9e30a-70cc-4f36-949f-fc7cd96b4054) gelesen oder im Konsolenbereich „get-help about_profiles“ eingegeben und die **EINGABETASTE** gedrückt haben.

Ein Profil ist ein Windows PowerShell ISE-Skript, das automatisch ausgeführt wird, wenn Sie eine neue Sitzung starten.  Sie können ein oder mehrere Windows PowerShell-Profile für Windows PowerShell ISE erstellen und diese dazu verwenden, die Umgebung von Windows PowerShell oder Windows PowerShell ISE zu konfigurieren, um sie mit den Variablen, Aliasen, Funktionen sowie Farb- und Schriftartvoreinstellungen vorzubereiten, die Sie zur Verfügung haben möchten. Ein Profil wirkt sich auf jede Windows PowerShell ISE-Sitzung aus, die Sie starten.

> [!NOTE]
> Die Windows PowerShell-Ausführungsrichtlinie bestimmt, ob Sie Skripts ausführen und ein Profil laden dürfen. Die Standardausführungsrichtlinie, „Restricted“, verhindert das Ausführen jeglicher Skripts, einschließlich Profile. Wenn Sie die Richtlinie „Restricted“ verwenden, kann das Profil nicht geladen werden. Weitere Informationen zu Ausführungsrichtlinien finden Sie unter [about_Execution_Policies [v4]](https://technet.microsoft.com/en-us/library/347708dc-1515-4d74-978b-8334603472e6).

## Auswählen eines Profils, das in Windows PowerShell ISE verwendet werden soll
Windows PowerShell ISE unterstützt Profile für den aktuellen Benutzer sowie für alle Benutzer. Außerdem werden die Windows PowerShell-Profile unterstützt, die für alle Hosts gelten.

Das Profil, das Sie verwenden, wird durch die Verwendung der Windows PowerShell und Windows PowerShell ISE bestimmt.

-   Wenn Sie nur Windows PowerShell ISE verwenden, um Windows PowerShell auszuführen, speichern Sie alle ihre Elemente in einem ISE-spezifischen Profil, z.B. dem Profil „CurrentUserCurrentHost“ für Windows PowerShell ISE oder „AllUsersCurrentHost“ für Windows PowerShell ISE.

-   Wenn Sie mehrere Hostprogramme verwenden, um Windows PowerShell auszuführen, speichern Sie Ihre Funktionen, Aliase, Variablen und Befehle in einem Profil, das alle Hostprogramme betrifft, z.B. dem Profil „CurrentUserAllHosts“ oder „AllUsersAllHosts“. Speichern Sie ISE-spezifische Merkmale wie Anpassungen von Farbe und Schriftart im Profil „CurrentUserCurrentHost“ für Windows PowerShell ISE oder „AllUsersCurrentHost“ für Windows PowerShell ISE.

Die folgenden Profile sind Profile, die in Windows PowerShell ISE erstellt und verwendet werden können. Jedes Profil wird in seinem eigenen speziellen Pfad gespeichert.

|Profiltyp|Profilpfad|
|----------------|----------------|
|„Aktueller Benutzer, PowerShell ISE“|$profile.CurrentUserCurrentHost oder $profile|
|„Alle Benutzer, PowerShell ISE“|$profile.AllUsersCurrentHost|
|„Aktueller Benutzer, alle Hosts“|$profile.CurrentUserAllHosts|
|„Alle Benutzer, alle Hosts“|$profile.AllUsersAllHosts|

## So erstellen Sie ein neues Profil
Um ein neues „Aktueller Benutzer, PowerShell ISE“-Profil zu erstellen, führen Sie den folgenden Befehl aus:

```
if (!(test-path $profile )) 
{new-item -type file -path $profile -force}
```

Um ein neues „Alle Benutzer, PowerShell ISE“-Profil zu erstellen, führen Sie den folgenden Befehl aus:

```
if (!(test-path $profile.AllUsersCurrentHost)) 
{new-item -type file -path $profile.AllUsersCurrentHost -force}
```

Um ein neues „Aktueller Benutzer, alle Hosts“-Profil zu erstellen, führen Sie den folgenden Befehl aus:

```
if (!(test-path $profile.CurrentUserAllHosts)) 
{new-item -type file -path $profile.CurrentUserAllHosts -force}
```

Um ein neues „Alle Benutzer, alle Hosts“-Profil zu erstellen, geben Sie Folgendes ein:

```
if (!(test-path $profile.AllUsersAllHosts)) 
{new-item -type file -path $profile.AllUsersAllHosts-force}
```

## So bearbeiten Sie ein Profil

1.  Um das Profil zu öffnen, führen Sie den Befehl „psedit“ mit der Variablen aus, die das Profil angibt, das Sie bearbeiten möchten. Wenn Sie beispielsweise das „Aktueller Benutzer, PowerShell ISE“-Profil öffnen möchten, geben Sie Folgendes ein: `psEdit $profile`

2.  Fügen Sie dem Profil einige Elemente hinzu. Es folgen einige Beispiele, die Ihnen den Einstieg erleichtern sollen:

    -   Um die Standardhintergrundfarbe des Konsolenbereichs in Blau zu ändern, geben Sie Folgendes in die Profildatei ein: `$psISE.Options.OutputPaneBackground = 'blue'`. Weitere Informationen zu der Variablen „$psISE“ finden Sie unter [Referenz zum Windows PowerShell ISE-Objektmodell](https://technet.microsoft.com/en-us/library/e1a9e7d1-0fd5-47de-8d9b-f1be1ed13b0c).

    -   Geben Sie Folgendes in die Profildatei ein, um den Schriftgrad in 20 zu ändern: `$psISE.Options.FontSize =20`

3.  Um Ihre Profildatei zu speichern, klicken Sie im Menü **Datei** auf **Speichern**. Wenn Sie Windows PowerShell ISE das nächste Mal öffnen, werden Ihre Anpassungen angewendet.

## Weitere Informationen
[about_Profiles [v4]](https://technet.microsoft.com/en-us/library/e1d9e30a-70cc-4f36-949f-fc7cd96b4054)
[Verwenden der Windows PowerShell ISE](Using-the-Windows-PowerShell-ISE.md)




<!--HONumber=Aug16_HO4-->


