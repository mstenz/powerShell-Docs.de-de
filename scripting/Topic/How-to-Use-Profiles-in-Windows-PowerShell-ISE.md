---
title: So wird's gemacht: Verwenden von Profilen in Windows PowerShell ISE
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0219626a-6da5-4acc-b630-d058e8b29cc6
---
# So wird's gemacht: Verwenden von Profilen in Windows PowerShell ISE
In diesem Thema wird erläutert, wie Profile in [!INCLUDE[ise_1](../Token/ise_1_md.md)] verwendet werden. Es empfiehlt sich, dass Sie die Aufgaben in diesem Abschnitt erst ausführen, nachdem Sie [about_Profiles [v4]](assetId:///e1d9e30a-70cc-4f36-949f-fc7cd96b4054) gelesen oder im Konsolenbereich „get-help about_profiles“ eingegeben und die **EINGABETASTE** gedrückt haben.

Ein Profil ist ein [!INCLUDE[ise_2](../Token/ise_2_md.md)]-Skript, das automatisch ausgeführt wird, wenn Sie eine neue Sitzung starten.  Sie können ein oder mehrere [!INCLUDE[wps_2](../Token/wps_2_md.md)]-Profile für [!INCLUDE[ise_2](../Token/ise_2_md.md)] erstellen und diese dazu verwenden, die Umgebung von [!INCLUDE[wps_2](../Token/wps_2_md.md)] oder [!INCLUDE[ise_2](../Token/ise_2_md.md)] zu konfigurieren, um sie mit den Variablen, Aliasen, Funktionen sowie Farb- und Schriftartvoreinstellungen vorzubereiten, die Sie verfügbar haben möchten. Ein Profil wirkt sich auf jede [!INCLUDE[ise_2](../Token/ise_2_md.md)]-Sitzung aus, die Sie starten.

> [!NOTE]
> Die [!INCLUDE[wps_2](../Token/wps_2_md.md)]-Ausführungsrichtlinie bestimmt, ob Sie Skripts ausführen und ein Profil laden dürfen. Die Standardausführungsrichtlinie, „Restricted“, verhindert das Ausführen jeglicher Skripts, einschließlich Profile. Wenn Sie die Richtlinie „Restricted“ verwenden, kann das Profil nicht geladen werden. Weitere Informationen zu Ausführungsrichtlinien finden Sie unter [about_Execution_Policies [v4]](assetId:///347708dc-1515-4d74-978b-8334603472e6).

## Auswählen eines Profils, das in Windows PowerShell ISE verwendet werden soll
[!INCLUDE[ise_2](../Token/ise_2_md.md)] unterstützt Profile für den aktuellen Benutzer sowie für alle Benutzer. Außerdem werden die [!INCLUDE[wps_2](../Token/wps_2_md.md)]-Profile unterstützt, die für alle Hosts gelten.

Das Profil, das Sie verwenden, richtet sich danach, wie Sie [!INCLUDE[wps_2](../Token/wps_2_md.md)] und [!INCLUDE[ise_2](../Token/ise_2_md.md)] verwenden.

-   Wenn Sie nur [!INCLUDE[ise_2](../Token/ise_2_md.md)] verwenden, um Windows PowerShell auszuführen, speichern Sie sämtliche ihrer Elemente in einem ISE-spezifischen Profil, z. B. das Profil „CurrentUserCurrentHost“ für [!INCLUDE[ise_2](../Token/ise_2_md.md)] oder das Profil „AllUsersCurrentHost“ für [!INCLUDE[ise_2](../Token/ise_2_md.md)].

-   Wenn Sie mehrere Hostprogramme verwenden, um Windows PowerShell auszuführen, speichern Sie Ihre Funktionen, Aliase, Variablen und Befehle in einem Profil, das alle Hostprogramme betrifft, z. B. das Profil „CurrentUserAllHosts“ oder „AllUsersAllHosts“. Speichern Sie ISE-spezifische Merkmale wie Anpassungen von Farbe und Schriftart im Profil „CurrentUserCurrentHost“ für [!INCLUDE[ise_2](../Token/ise_2_md.md)] oder im Profil „AllUsersCurrentHost“ für [!INCLUDE[ise_2](../Token/ise_2_md.md)].

Die folgenden Profile sind Profile, die in [!INCLUDE[ise_2](../Token/ise_2_md.md)] erstellt und verwendet werden können. Jedes Profil wird in seinem eigenen speziellen Pfad gespeichert.

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

    -   Um die Standardhintergrundfarbe des Konsolenbereichs in Blau zu ändern, geben Sie Folgendes in die Profildatei ein: `$psISE.Options.OutputPaneBackground = 'blue'`. Weitere Informationen zu der Variablen „$psISE“ finden Sie unter [Referenz zum Windows PowerShell ISE-Objektmodell](assetId:///e1a9e7d1-0fd5-47de-8d9b-f1be1ed13b0c).

    -   Um den Schriftgrad in 20 zu ändern, geben Sie Folgendes in die Profildatei ein: `$psISE.Options.FontSize =20`

3.  Um Ihre Profildatei zu speichern, klicken Sie im Menü **Datei** auf **Speichern**. Wenn Sie [!INCLUDE[ise_2](../Token/ise_2_md.md)] das nächste Mal öffnen, werden Ihre Anpassungen angewendet.

## Weitere Informationen
[about_Profiles [v4]](assetId:///e1d9e30a-70cc-4f36-949f-fc7cd96b4054)
[Verwenden der Windows PowerShell ISE](../Topic/Using-the-Windows-PowerShell-ISE.md)



<!--HONumber=Apr16_HO1-->


