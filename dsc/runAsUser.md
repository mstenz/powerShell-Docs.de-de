# Ausführen von DSC mit Benutzeranmeldeinformationen 

> Gilt für: Windows PowerShell 5.0

Sie können eine DSC-Konfiguration unter einen angegebenen Satz von Anmeldeinformationen ausführen, indem Sie die Eigenschaft PsDscRunAsCredential in der Konfiguration verwenden. Standardmäßig wird DSC als Systemkonto ausgeführt.
as the system account. Es gibt Situationen, in denen DSC unter einem Benutzerkonto ausgeführt werden muss, z. B. beim Installieren von MSI-Paketen in einem bestimmten Benutzerkontext, beim Festlegen der Registrierungsschlüssel eines Benutzers, beim Zugriff auf ein bestimmtes lokales Verzeichnis eines Benutzers oder beim Zugriff auf eine Netzwerkfreigabe.
accessing a user's specific local directory, or accessing a network share.

Jede DSC-Ressource verfügt über eine PsDscRunAsCredential-Eigenschaft, die auf beliebige Anmeldeinformationen festgelegt werden kann (ein PSCredential-Objekt).
Die Anmeldeinformationen können als Wert der Eigenschaft in der Konfiguration hartcodiert werden, oder Sie können den Wert auf Get-Credential festlegen, wodurch der Benutzer beim Kompilieren der Konfiguration zur Eingabe der Anmeldeinformationen aufgefordert wird (Informationen zum Kompilieren von Konfigurationen finden Sie unter Konfigurationen.
which will prompt the user for a credential when the configuration is compiled (for information about compiling configurations, see <bpt id="p1">[</bpt>Configurations<ept id="p1">](configurations.md)</ept>.

>Hinweis: Die Eigenschaft PsDscRunAsCredential ist in PowerShell 4.0 nicht verfügbar.

Im folgenden Beispiel wird Get-Credential verwendet, um den Benutzer zur Eingabe von Anmeldeinformationen aufzufordern. Die Ressource Registry wird verwendet, um den Registrierungsschlüssel zu ändern, der die Hintergrundfarbe für das Windows-Eingabeaufforderungsfenster angibt.
for the Windows command prompt window.

```powershell
Configuration ChangeCmdBackGroundColor    

{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node $AllNodes.NodeName

    {
        Registry CmdPath

        {

            Key = 'HKEY_CURRENT_USER\SOFTWARE\Microsoft\Command Processor'

            ValueName = "DefaultColor"

            ValueData = '1F'

            ValueType = "DWORD"

            Ensure = "Present"

            Force = $true

            Hex = $true

            PsDscRunAsCredential = Get-Credential
        }
    }                   
}

$configData = @{

    AllNodes = @(

    @{

        NodeName="localhost";
        PSDscAllowDomainUser = $true
        CertificateFile = "C:\publicKeys\targetNode.cer"
        Thumbprint = "7ee7f09d-4be0-41aa-a47f-96b9e3bdec25"

    })

}

ChangeCmdBackGroundColor -ConfigurationData $configData
```
>Hinweis: In diesem Beispiel wird vorausgesetzt, dass Sie über ein gültiges Zertifikat unter `C:\publicKeys\targetNode.cer` verfügen und dass der Fingerabdruck dieses Zertifikats der angezeigte Wert ist.
>Informationen zum Verschlüsseln von Anmeldeinformationen in DSC MOF-Konfigurationsdateien finden Sie unter Absichern der MOF-Datei. 



<!--HONumber=Mar16_HO2-->


