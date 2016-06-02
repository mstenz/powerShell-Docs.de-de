---
title:  Installieren das Windows PowerShell SDK
ms.date:  2016-05-11
keywords:  powershell,cmdlet
description:  
ms.topic:  article
author:  jpjofre
manager:  dongill
ms.prod:  powershell
ms.assetid:  c3636b45-61aa-4720-85f0-58312c4fc8f9
---

# Installieren das Windows PowerShell SDK
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Das folgende Thema beschreibt, wie das PowerShell SDK in verschiedenen Versionen von Windows installiert wird.</para>
  </introduction>
  <section>
    <title>Installieren des Windows PowerShell 3.0 SDKs für Windows 8 und Windows Server 2012</title>
    <content>
      <para>Windows PowerShell 3.0 wird automatisch mit Windows 8 und Windows Server 2012 installiert. Darüber hinaus können Sie die Verweisassemblys für Windows PowerShell 3.0 als Teil des Windows 8 SDKs herunterladen und installieren. Diese Assemblys ermöglichen Ihnen das Schreiben von Cmdlets, Anbietern und Host-Programmen für Windows PowerShell 3.0. Wenn Sie das Windows SDK für Windows 8 installieren, werden die Windows PowerShell-Assemblys im Ordner „Verweisassembly“ unter „\Programme (x86)\Reference Assemblies\Microsoft\WindowsPowerShell\3.0“ automatisch installiert. Weitere Informationen finden Sie auf der <externalLink><linkText>Windows 8 SDK-Downloadsite</linkText><linkUri>http://msdn.microsoft.com/windows/hardware/hh852363.aspx</linkUri></externalLink>. Codebeispiele für Windows PowerShell stehen ebenfalls im Dev Center zur Verfügung. Weitere Informationen finden Sie auf der Seite „desktop code samples“ (Desktop-Codebeispiele) auf der <externalLink><linkText>Dev Center-Website</linkText><linkUri>http://code.msdn.microsoft.com/windowsdesktop/</linkUri></externalLink>. </para>
      <para>Darüber hinaus ist Windows PowerShell 3.0 abwärtskompatibel mit dem Windows PowerShell 2.0 SDK, das eine Reihe von Codebeispielen enthält. Weitere Informationen zum Herunterladen des Windows PowerShell 2.0 SDKs finden Sie nachstehend. (Beachten Sie, dass, während die 2.0-Codebeispiele mit Windows 8 und Windows PowerShell 3.0 kompatibel sind, Sie Windows PowerShell 2.0 auf einer Windows 8-Plattform nicht installieren können.) </para>
    </content>
  </section>
  <section>
    <title>Installieren des Windows PowerShell 3.0 SDKs für Windows 7 und Windows Server 2008 R2</title>
    <content>
      <para>Auf Windows 7 und Windows Server 2008 R2 wird PowerShell 2.0 automatisch installiert. Darüber hinaus können Sie PowerShell 3.0 auf diesen Systemen installieren. (Weitere Informationen finden Sie unter <link xlink:href="6fbb0409-5a54-48ec-95e6-7f8b7d8c4969">Installieren von Windows PowerShell</link>.) Wie oben beschrieben, können Sie das Windows 8 SDK auch unter Windows 7 und Windows Server 2008 R2 installieren.</para>
    </content>
  </section>
  <section>
    <title>Installieren des Windows PowerShell 2.0 SDKs für Windows 7, Vista, XP, Server 2003 und Server 2008</title>
    <content>
      <para>Das <token>mshshort</token>-2.0 SDK stellt die Verweisassemblys bereit, die zum Schreiben von Cmdlets, Anbietern und Hostinganwendungen erforderlich sind, und bietet C#-Beispielcode, der als Ausgangspunkt verwendet werden kann, wenn Sie mit dem Schreiben von Code beginnen. </para>
      <para>Gehen Sie zum Installieren dieses SDKs auf <externalLink><linkText>Windows PowerShell 2.0 SDK</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=184611</linkUri></externalLink>.</para>
    </content>
    <sections>
      <section>
        <title>Verweisassemblys</title>
        <content>
          <para>Verweisassemblys werden standardmäßig an folgendem Speicherort installiert: <codeInline>C:\Programme\Reference Assemblies\Microsoft\WindowsPowerShell\V1.0</codeInline>.</para>
          <alert class="note">
            <para>Code, der für die Windows PowerShell 2.0-Assemblys kompiliert wird, kann nicht in Windows PowerShell 1.0-Installationen geladen werden. Jedoch kann Code, der für die Windows PowerShell 1.0-Assemblys kompiliert wird, in Windows PowerShell 2.0-Installationen geladen werden.</para>
          </alert>
        </content>
      </section>
      <section>
        <title>Beispiele</title>
        <content>
          <para>Codebeispiele werden standardmäßig an folgendem Speicherort installiert: <codeInline>C:\Programme\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\</codeInline>.</para>
          <para>Die folgenden Abschnitte enthalten eine kurze Beschreibung der Wirkungsweise jedes Beispiels.</para>
        </content>
        <sections>
          <section>
            <title>Cmdlet-Beispiele</title>
            <content>
              <definitionTable>
                <definedTerm>GetProcessSample01</definedTerm>
                <definition>
                  <para>Zeigt, wie ein einfaches Cmdlet geschrieben wird, das alle Prozesse auf dem lokalen Computer abruft.</para>
                </definition>
                <definedTerm>GetProcessSample02</definedTerm>
                <definition>
                  <para>Zeigt, wie Parameter zum Cmdlet hinzugefügt werden. Das Cmdlet nimmt einen oder mehrere Prozessnamen und gibt die entsprechenden Prozesse zurück.</para>
                </definition>
                <definedTerm>GetProcessSample03</definedTerm>
                <definition>
                  <para>Zeigt, wie Parameter hinzugefügt werden, die eine Eingabe aus der Pipeline akzeptieren.</para>
                </definition>
                <definedTerm>GetProcessSample04</definedTerm>
                <definition>
                  <para>Zeigt, wie Fehler ohne Abbruch behandelt werden.</para>
                </definition>
                <definedTerm>GetProcessSample05</definedTerm>
                <definition>
                  <para>Zeigt, wie eine Liste angegebener Prozesse angezeigt wird.</para>
                </definition>
                <definedTerm>SelectObject</definedTerm>
                <definition>
                  <para>Zeigt, wie ein Filter geschrieben wird, um nur bestimmte Objekte auszuwählen. </para>
                </definition>
                <definedTerm>SelectString</definedTerm>
                <definition>
                  <para>Zeigt, wie Dateien für angegebene Muster gesucht werden.</para>
                </definition>
                <definedTerm>StopProcessSample01</definedTerm>
                <definition>
                  <para>Zeigt, wie ein <parameterReference>PassThru</parameterReference>-Parameter implementiert wird, und wie durch Aufrufe der Methoden <codeEntityReference>Overload:System.Management.Automation.Cmdlet.ShouldProcess</codeEntityReference> und <codeEntityReference>Overload:System.Management.Automation.Cmdlet.ShouldContinue</codeEntityReference> Benutzerfeedback angefordert wird. Benutzer geben den <parameterReference>PassThru</parameterReference>-Parameter an, wenn sie das Cmdlet dazu zwingen möchten, ein Objekt zurückzugeben, </para>
                </definition>
                <definedTerm>StopProcessSample02</definedTerm>
                <definition>
                  <para>Zeigt, wie ein bestimmter Prozess beenden wird.</para>
                </definition>
                <definedTerm>StopProcessSample03</definedTerm>
                <definition>
                  <para>Zeigt, wie Aliase für Parameter deklariert und wie Platzhalter unterstützt werden.</para>
                </definition>
                <definedTerm>StopProcessSample04</definedTerm>
                <definition>
                  <para>Zeigt, wie Parametersätze und das Objekt, das vom Cmdlet als Eingabe verwendet wird, deklariert werden, und wie der zu verwendende Standardparametersatz angegeben wird.</para>
                </definition>
              </definitionTable>
            </content>
          </section>
          <section>
            <title>Beispiele für Remoting</title>
            <content>
              <definitionTable>
                <definedTerm>RemoteRunspace01</definedTerm>
                <definition>
                  <para>Zeigt, wie ein Remoterunspace erstellt wird, der zum Herstellen einer Remoteverbindung verwendet wird.</para>
                </definition>
                <definedTerm>RemoteRunspacePool01</definedTerm>
                <definition>
                  <para>Zeigt, wie ein Remoterunspacepool erstellt wird, und wie mithilfe dieses Pools mehrere Befehle gleichzeitig ausgeführt werden.</para>
                </definition>
                <definedTerm>Serialization01</definedTerm>
                <definition>
                  <para>Zeigt, wie eine vorhandene .NET-Klasse betrachtet werden kann, und wie sichergestellt wird, dass Informationen von ausgewählten öffentlichen Eigenschaften dieser Klasse über die Serialisierung/Deserialisierung hinweg beibehalten werden.</para>
                </definition>
                <definedTerm>Serialization02</definedTerm>
                <definition>
                  <para>Zeigt, wie eine vorhandene .NET-Klasse betrachtet werden kann, und wie sichergestellt wird, dass die Informationen der Instanz dieser Klasse über die Serialisierung/Deserialisierung hinweg beibehalten werden, wenn die Informationen nicht in öffentlichen Eigenschaften der Klasse verfügbar sind</para>
                </definition>
                <definedTerm>Serialization03</definedTerm>
                <definition>
                  <para>Zeigt, wie eine vorhandene .NET-Klasse betrachtet werden kann, und wie sichergestellt wird, dass Instanzen dieser Klasse und abgeleiteter Klassen in aktive .NET-Objekte deserialisiert (aktiviert) werden.</para>
                </definition>
              </definitionTable>
            </content>
          </section>
          <section>
            <title>Ereignisbeispiele</title>
            <content>
              <definitionTable>
                <definedTerm>Event01</definedTerm>
                <definition>
                  <para>Zeigt, wie durch Ableiten von ObjectEventRegistrationBase ein Cmdlet für die Ereignisregistrierung erstellt wird.</para>
                </definition>
                <definedTerm>Event02</definedTerm>
                <definition>
                  <para>Zeigt, wie Benachrichtigungen über <token>mshshort</token>-Ereignisse empfangen werden, die auf Remotecomputern generiert werden. Es verwendet das von der Klasse <codeEntityReference>T:System.Management.Automation.Runspaces.Runspace</codeEntityReference> offen gelegte PSEventReceived-Ereignis.</para>
                </definition>
              </definitionTable>
            </content>
          </section>
          <section>
            <title>Hostinganwendungsbeispiele</title>
            <content>
              <definitionTable>
                <definedTerm>Runspace01</definedTerm>
                <definition>
                  <para>Zeigt, wie die Klasse <codeEntityReference>T:System.Management.Automation.PowerShell</codeEntityReference> verwendet wird, um das Cmdlet <externalLink><linkText>Get-Process</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=113324</linkUri></externalLink> synchron auszuführen. Das Cmdlet <externalLink><linkText>Get-Process</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=113324</linkUri></externalLink> gibt <codeEntityReference>T:System.Diagnostics.Process</codeEntityReference>-Objekte für jeden auf dem lokalen Computer ausgeführten Prozess zurück.</para>
                </definition>
                <definedTerm>Runspace02</definedTerm>
                <definition>
                  <para>Zeigt, wie die Klasse <codeEntityReference>T:System.Management.Automation.PowerShell</codeEntityReference> verwendet wird, um die Cmdlets <externalLink><linkText>Get-Process</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=113324</linkUri></externalLink> und <externalLink><linkText>Sort-Object</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkID=113403</linkUri></externalLink> synchron auszuführen. Das Cmdlet <externalLink><linkText>Get-Process</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=113324</linkUri></externalLink> gibt <codeEntityReference>T:System.Diagnostics.Process</codeEntityReference>-Objekte für jeden auf dem lokalen Computer ausgeführten Prozess zurück. Das Sort-Objekt sortiert die Objekte basierend auf ihrer <codeEntityReference>P:System.Diagnostics.Process.Id</codeEntityReference>-Eigenschaft. Die Ergebnisse dieser Befehle werden mithilfe eines <codeEntityReference>T:System.Windows.Forms.DataGridView</codeEntityReference>-Steuerelements angezeigt.</para>
                </definition>
                <definedTerm>Runspace03</definedTerm>
                <definition>
                  <para>Zeigt, wie die Klasse <codeEntityReference>T:System.Management.Automation.PowerShell</codeEntityReference> verwendet wird, um ein Skript synchron auszuführen, und wie Fehler ohne Abbruch behandelt werden. Das Skript empfängt eine Liste von Prozessnamen und ruft diese Prozesse anschließend ab. Die Ergebnisse des Skripts, einschließlich aller Fehler ohne Abbruch, die beim Ausführen des Skripts generiert wurden, werden in einem Konsolenfenster angezeigt.</para>
                </definition>
                <definedTerm>Runspace04</definedTerm>
                <definition>
                  <para>Zeigt, wie die Klasse <codeEntityReference>T:System.Management.Automation.PowerShell</codeEntityReference> verwendet wird, um Befehle auszuführen, und wie Fehler mit Abbruch erfasst werden, die beim Ausführen der Befehle ausgelöst werden. Zwei Befehle werden ausgeführt. An den letzten Befehl wird ein ungültiges Parameterargument übergeben. Daher werden keine Objekte zurückgegeben und ein Fehler mit Abbruch wird ausgelöst.</para>
                </definition>
                <definedTerm>Runspace05</definedTerm>
                <definition>
                  <para>Zeigt, wie einem <codeEntityReference>T:System.Management.Automation.Runspaces.InitialSessionState</codeEntityReference>-Objekt ein Snap-In hinzugefügt wird, damit das Cmdlet des Snap-Ins verfügbar ist, wenn der Runspace geöffnet wird. Das Snap-In stellt ein „Get-Proc“-Cmdlet (definiert durch das <legacyLink xlink:href="7b48bf80-cbf0-4cb1-8d5b-3b8d06196598">Beispiel GetProcessSample01</legacyLink>) bereit, das mithilfe eines <codeEntityReference>T:System.Management.Automation.PowerShell</codeEntityReference>-Objekts synchron ausgeführt wird.</para>
                </definition>
                <definedTerm>Runspace06</definedTerm>
                <definition>
                  <para>Zeigt, wie ein Modul einem <codeEntityReference>T:System.Management.Automation.Runspaces.InitialSessionState</codeEntityReference>-Objekt hinzugefügt wird, damit das Modul geladen wird, wenn der Runspace geöffnet wird. Das Modul stellt ein „Get-Proc“-Cmdlet (definiert durch das <legacyLink xlink:href="481f557d-3344-4d33-b2da-4736a0165181">Beispiel GetProcessSample02</legacyLink>) bereit, das mithilfe eines <codeEntityReference>T:System.Management.Automation.PowerShell</codeEntityReference>-Objekts synchron ausgeführt wird.</para>
                </definition>
                <definedTerm>Runspace07</definedTerm>
                <definition>
                  <para>Zeigt, wie ein Runspace erstellt wird, und wie dieser Runspace anschließend dazu verwendet wird, zwei Cmdlets mithilfe eines <codeEntityReference>T:System.Management.Automation.PowerShell</codeEntityReference>-Objekts synchron auszuführen.</para>
                </definition>
                <definedTerm>Runspace08</definedTerm>
                <definition>
                  <para>Zeigt, wie Befehle und Argumente zur Pipeline eines <codeEntityReference>T:System.Management.Automation.PowerShell</codeEntityReference>-Objekts hinzugefügt werden, und wie die Befehle synchron ausgeführt werden.</para>
                </definition>
                <definedTerm>Runspace09</definedTerm>
                <definition>
                  <para>Zeigt, wie ein Skript zur Pipeline eines <codeEntityReference>T:System.Management.Automation.PowerShell</codeEntityReference>-Objekts hinzugefügt wird, und wie das Skript asynchron ausgeführt wird. Ereignisse werden zur Handhabung der Skriptausgabe verwendet.</para>
                </definition>
                <definedTerm>Runspace10</definedTerm>
                <definition>
                  <para>Zeigt, wie ein standardmäßiger anfänglicher Sitzungsstatus erstellt wird, wie ein Cmdlet zu <codeEntityReference>T:System.Management.Automation.Runspaces.InitialSessionState</codeEntityReference> hinzugefügt wird, wie ein Runspace erstellt wird, der den anfänglichen Sitzungsstatus verwendet, und wie der Befehl mithilfe eines <codeEntityReference>T:System.Management.Automation.PowerShell</codeEntityReference>-Objekts ausgeführt wird.</para>
                </definition>
                <definedTerm>Runspace11</definedTerm>
                <definition>
                  <para>Zeigt, wie die Klasse <codeEntityReference>T:System.Management.Automation.ProxyCommand</codeEntityReference> dazu verwendet wird, einen Proxybefehl zu erstellen, der ein vorhandenes Cmdlet abruft, den Satz verfügbarer Parameter jedoch einschränkt. Der Proxybefehl wird anschließend zu einem anfänglichen Sitzungsstatus hinzugefügt, der dazu verwendet wird, einen eingeschränkten Runspace zu erstellen. Dies bedeutet, dass der Benutzer nur über den Proxybefehl auf die Funktionalität des Cmdlets zugreifen kann.</para>
                </definition>
                <definedTerm>PowerShell01</definedTerm>
                <definition>
                  <para>Zeigt, wie ein eingeschränkter Runspace mithilfe eines <codeEntityReference>T:System.Management.Automation.Runspaces.InitialSessionState</codeEntityReference>-Objekts erstellt wird.</para>
                </definition>
                <definedTerm>PowerShell02</definedTerm>
                <definition>
                  <para>Zeigt, wie ein Runspacepool zum Ausführen mehrerer Befehle gleichzeitig verwendet wird.</para>
                </definition>
              </definitionTable>
            </content>
          </section>
          <section>
            <title>Hostbeispiele</title>
            <content>
              <definitionTable>
                <definedTerm>Host01</definedTerm>
                <definition>
                  <para>Zeigt, wie eine Hostanwendung implementiert wird, die einen benutzerdefinierten Host verwendet. In diesem Beispiel wird ein Runspace erstellt, der den benutzerdefinierten Host verwendet. Anschließend wird die <codeEntityReference>T:System.Management.Automation.PowerShell</codeEntityReference>-API zum Ausführen eines Skripts verwendet, das „exit“ abruft. Die Hostanwendung betrachtet anschließend die Ausgabe des Skripts und druckt die Ergebnisse aus.</para>
                </definition>
                <definedTerm>Host02</definedTerm>
                <definition>
                  <para>Zeigt, wie eine Hostanwendung geschrieben wird, die die <token>mshshort</token>-Laufzeit zusammen mit einer benutzerdefinierten Hostimplementierung verwendet. Die Hostanwendung legt die Hostkultur auf Deutsch fest, führt das Cmdlet <externalLink><linkText>Get-Process</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=113324</linkUri></externalLink> aus und zeigt die Ergebnisse so an, wie Sie sie mithilfe von „pwrsh.exe“ sehen würden. Anschließend druckt sie die aktuellen Daten und die Zeit auf Deutsch aus.</para>
                </definition>
                <definedTerm>Host03</definedTerm>
                <definition>
                  <para>Zeigt, wie eine interaktive, konsolenbasierte Hostanwendung erstellt wird, die Befehle von der Befehlszeile aus liest, die Befehle ausführt und die Ergebnisse anschließend in der Konsole anzeigt.</para>
                </definition>
                <definedTerm>Host04</definedTerm>
                <definition>
                  <para>Zeigt, wie eine interaktive, konsolenbasierte Hostanwendung erstellt wird, die Befehle von der Befehlszeile aus liest, die Befehle ausführt und die Ergebnisse anschließend in der Konsole anzeigt. Diese Hostanwendung unterstützt auch das Anzeigen von Eingabeaufforderungen, die es den Benutzern ermöglichen, mehrere Auswahlmöglichkeiten anzugeben.</para>
                </definition>
                <definedTerm>Host05</definedTerm>
                <definition>
                  <para>Zeigt, wie eine interaktive, konsolenbasierte Hostanwendung erstellt wird, die Befehle von der Befehlszeile aus liest, die Befehle ausführt und die Ergebnisse anschließend in der Konsole anzeigt. Diese Hostanwendung unterstützt auch Aufrufe an Remotecomputern mithilfe der Cmdlets <externalLink><linkText>Enter-PsSession</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=135210</linkUri></externalLink> und <externalLink><linkText>Exit-PsSession</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=135212</linkUri></externalLink>.</para>
                </definition>
                <definedTerm>Host06</definedTerm>
                <definition>
                  <para>Zeigt, wie eine interaktive, konsolenbasierte Hostanwendung erstellt wird, die Befehle von der Befehlszeile aus liest, die Befehle ausführt und die Ergebnisse anschließend in der Konsole anzeigt. Darüber hinaus verwendet dieses Beispiel die Tokenizer-APIs, um die Farbe des vom Benutzer eingegebenen Texts anzugeben.</para>
                </definition>
              </definitionTable>
            </content>
          </section>
          <section>
            <title>Anbieterbeispiele</title>
            <content>
              <definitionTable>
                <definedTerm>AccessDBProviderSample01</definedTerm>
                <definition>
                  <para>Zeigt, wie eine Anbieterklasse deklariert wird, die direkt von der Klasse <codeEntityReference>T:System.Management.Automation.Provider.CmdletProvider</codeEntityReference> abgeleitet wird. Es wird hier nur der Vollständigkeit halber aufgelistet.</para>
                </definition>
                <definedTerm>AccessDBProviderSample02</definedTerm>
                <definition>
                  <para>Zeigt, wie die Methoden <codeEntityReference>M:System.Management.Automation.Provider.DriveCmdletProvider.NewDrive(System.Management.Automation.PSDriveInfo)</codeEntityReference> und <codeEntityReference>M:System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive(System.Management.Automation.PSDriveInfo)</codeEntityReference> überschrieben werden, um Aufrufe der Cmdlets „New-PSDrive“ und „Remove-PSDrive“ zu unterstützen. Die Anbieterklasse in diesem Beispiel ist abgeleitet von der Klasse <codeEntityReference>T:System.Management.Automation.Provider.DriveCmdletProvider</codeEntityReference>.</para>
                </definition>
                <definedTerm>AccessDBProviderSample03</definedTerm>
                <definition>
                  <para>Zeigt, wie die Methoden <codeEntityReference>M:System.Management.Automation.Provider.ItemCmdletProvider.GetItem(System.String)</codeEntityReference> und <codeEntityReference>M:System.Management.Automation.Provider.ItemCmdletProvider.SetItem(System.String,System.Object)</codeEntityReference> überschrieben werden, um Aufrufe der Cmdlets „Get-Item“ und „Set-Item“ zu unterstützen. Die Anbieterklasse in diesem Beispiel ist abgeleitet von der Klasse <codeEntityReference>T:System.Management.Automation.Provider.ItemCmdletProvider</codeEntityReference>.</para>
                </definition>
                <definedTerm>AccessDBProviderSample04</definedTerm>
                <definition>
                  <para>Zeigt, wie Containermethoden überschrieben werden, um Aufrufe der Cmdlets „Copy-Item“, „Get-ChildItem“, „New-Item“ und „Remove-Item“ zu unterstützen. Diese Methoden sollten implementiert werden, wenn der Datenspeicher Elemente enthält, die Container sind. Ein Container ist eine Gruppe von untergeordneten Elementen unter einem gemeinsamen übergeordneten Element. Die Anbieterklasse in diesem Beispiel ist abgeleitet von der Klasse <codeEntityReference>T:System.Management.Automation.Provider.ItemCmdletProvider</codeEntityReference>.</para>
                </definition>
                <definedTerm>AccessDBProviderSample05</definedTerm>
                <definition>
                  <para>Zeigt, wie Containermethoden überschrieben werden, um Aufrufe der Cmdlets „Move-Item“ und „Join-Path“ zu unterstützen. Diese Methoden sollten implementiert werden, wenn der Benutzer Elemente innerhalb eines Containers verschieben muss, und wenn der Datenspeicher geschachtelte Container enthält. Die Anbieterklasse in diesem Beispiel ist abgeleitet von der Klasse <codeEntityReference>T:System.Management.Automation.Provider.NavigationCmdletProvider</codeEntityReference>.</para>
                </definition>
                <definedTerm>AccessDBProviderSample06</definedTerm>
                <definition>
                  <para>Zeigt, wie Inhaltsmethoden überschrieben werden, um Aufrufe der Cmdlets „Clear-Content“, „Get-Content“ und „Set-Content“ zu unterstützen. Diese Methoden sollten implementiert werden, wenn der Benutzer den Inhalt der Elemente im Datenspeicher verwaltet muss. Die Anbieterklasse in diesem Beispiel ist abgeleitet von der Klasse <codeEntityReference>T:System.Management.Automation.Provider.NavigationCmdletProvider</codeEntityReference> und implementiert die Schnittstelle <codeEntityReference>T:System.Management.Automation.Provider.IContentCmdletProvider</codeEntityReference>.</para>
                </definition>
              </definitionTable>
            </content>
          </section>
        </sections>
      </section>
    </sections>
  </section>
  <relatedTopics />
</developerConceptualDocument>



<!--HONumber=May16_HO4-->


