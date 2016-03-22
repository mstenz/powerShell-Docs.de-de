# Schützen der MOF-Datei

>Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0

DSC weist die Zielknoten an, welche Konfiguration sie aufweisen sollen, indem eine MOF-Datei mit den gewünschten Informationen an alle Knoten gesendet wird, auf denen der lokale Konfigurations-Manager (LCM) die gewünschte Konfiguration implementiert. Da diese Datei die Details der Konfiguration enthält, muss sie geschützt werden. Zu diesem Zweck können Sie den lokalen Konfigurations-Managers die Anmeldeinformationen eines Benutzers überprüfen lassen. In diesem Thema wird beschrieben, wie diese Anmeldeinformationen sicher an den Zielknoten übertragen werden, indem sie mithilfe von Zertifikaten verschlüsselt werden.

## Voraussetzungen

Stellen Sie sicher, dass Folgendes zutrifft, um die Anmeldeinformationen sicher zu verschlüsseln, die zum Schutz einer DSC-Konfiguration dienen:

* **Möglichkeiten zum Ausstellen und Verteilen von Zertifikaten**. In diesem Thema und seinen Beispielen wird davon ausgegangen, dass Sie eine Active Directory-Zertifizierungsstelle verwenden. Weitere Informationen zu Active Directory-Zertifikatdiensten finden Sie unter [Übersicht über Active Directory-Zertifikatdienste](https://technet.microsoft.com/library/hh831740.aspx) und [Active Directory-Zertifikatdienste in Windows Server 2008](https://technet.microsoft.com/windowsserver/dd448615.aspx).
* **Administratorzugriff auf den Zielknoten oder Knoten**.
* **Jeder Zielknoten hat ein verschlüsselungsfähiges Zertifikat, das in seinem persönlichen Speicher gespeichert ist**. In Windows PowerShell ist der Pfad zum Speicher „Cert: \LocalMachine\My“. In den Beispielen in diesem Thema verwenden Sie die Vorlage „Arbeitsstationsauthentifizierung“, die Sie (zusammen mit anderen Zertifikatvorlagen) unter [Standardzertifikatvorlagen](https://technet.microsoft.com/library/cc740061(v=WS.10).aspx) finden.
* Wenn Sie diese Konfiguration auf einem anderen Computer als dem Zielknoten ausführen, **exportieren Sie den öffentlichen Schlüssel des Zertifikats**, und importieren Sie ihn anschließend auf den Computer, auf dem Sie die Konfiguration ausführen. Stellen Sie sicher, dass Sie nur den **öffentlichen** Schlüssel exportieren. Halten Sie den privaten Schlüssel geschützt.

## Allgemeiner Prozess

1. Richten Sie die Zertifikate, Schlüssel und Fingerabdrücke ein, und stellen Sie sicher, dass jeder Zielknoten über Kopien des Zertifikats verfügt, und dass sich der öffentliche Schlüssel und Fingerabdruck auf dem Konfigurationscomputer befinden.
1. Erstellen Sie einen „Configuration“-Datenblock, der den Pfad und Fingerabdruck des öffentlichen Schlüssels enthält.
1. Erstellen Sie ein Konfigurationsskript, das die gewünschte Konfiguration für den Zielknoten definiert. Richten Sie die Entschlüsselung auf den Zielknoten ein, indem Sie den lokalen Konfigurations-Manager anweisen, die Konfigurationsdaten mithilfe des Zertifikats und Fingerabdrucks zu entschlüsseln.
1. Führen Sie die Konfiguration aus, woraufhin die Einstellungen des lokalen Konfigurations-Managers festgelegt werden und die DSC-Konfiguration gestartet wird.

## Konfigurationsdaten

Der „Configuration“-Datenblock definiert die betroffenen Zielknoten, ob die Anmeldeinformationen verschlüsselt werden oder nicht, die Verschlüsselungsmethode und andere Informationen. Weitere Informationen zum „Configuration“-Datenblock finden Sie unter [Trennen von Konfigurations- und Umgebungsdaten](configData.md).

Dieses Beispiel zeigt einen „Configuration“-Datenblock, einen betroffenen Zielknoten namens „targetNode“, den Pfad zur Zertifikatdatei mit dem öffentlichen Schlüssel (namens „targetNode.cer“) und den Fingerabdruck des öffentlichen Schlüssels.

```powershell
$ConfigData= @{ 
    AllNodes = @(     
            @{  
                # The name of the node we are describing 
                NodeName = "targetNode" 

                # The path to the .cer file containing the 
                # public key of the Encryption Certificate 
                # used to encrypt credentials for this node 
                CertificateFile = "C:\publicKeys\targetNode.cer" 

         
                # The thumbprint of the Encryption Certificate 
                # used to decrypt the credentials on target node 
                Thumbprint = "AC23EA3A9E291A75757A556D0B71CBBF8C4F6FD8" 
            }; 
        );    
    }
```

## Konfigurationsskript

Verwenden Sie im Skript selbst den `PsCredential`-Parameter, um sicherzustellen, dass die Anmeldeinformationen so kurz wie möglich gespeichert werden. Wenn Sie das bereitgestellte Beispiel ausführen, werden Sie von DSC zum Eingeben von Anmeldeinformationen und anschließendem Verschlüsseln der MOF-Datei mithilfe der Zertifikatdatei aufgefordert, die dem Zielknoten im „Configuration“-Datenblock zugeordnet ist. Bei diesem Codebeispiel wird eine Datei aus einer geschützten Freigabe zu einem Benutzer kopiert.

```
configuration CredentialEncryptionExample 
{ 
    param( 
        [Parameter(Mandatory=$true)] 
        [ValidateNotNullorEmpty()] 
        [PsCredential] $credential 
        ) 
    

    Node $AllNodes.NodeName 
    { 
        File exampleFile 
        { 
            SourcePath = "\\Server\share\path\file.ext" 
            DestinationPath = "C:\destinationPath" 
            Credential = $credential 
        } 
    } 
}
```

## Einrichten der Entschlüsselung

Damit `Start-DscConfiguration` funktionieren kann, müssen Sie den lokalen Konfigurations-Manager auf allen Zielknoten informieren, welches Zertifikat zum Entschlüsseln der Anmeldeinformationen verwendet werden soll. Die „CertificateID“-Ressource wird zum Überprüfen des Fingerabdrucks des Zertifikats verwendet. Diese Beispielfunktion findet das entsprechende lokale Zertifikat (Sie müssen ggf. eine Anpassung vornehmen, damit genau das gewünschte Zertifikat gefunden wird):

```powershell
# Get the certificate that works for encryption 
function Get-LocalEncryptionCertificateThumbprint 
{ 
    (dir Cert:\LocalMachine\my) | %{
        # Verify the certificate is for Encryption and valid 
        if ($_.PrivateKey.KeyExchangeAlgorithm -and $_.Verify()) 
        { 
            return $_.Thumbprint 
        } 
    } 
}
```

Mit dem über seinen Fingerabdruck bestimmten Zertifikat kann das Konfigurationsskript für das Verwenden des folgenden Werts aktualisiert werden:

```powershell
configuration CredentialEncryptionExample 
{ 
    param( 
        [Parameter(Mandatory=$true)] 
        [ValidateNotNullorEmpty()] 
        [PsCredential] $credential 
        ) 
    

    Node $AllNodes.NodeName 
    { 
        File exampleFile 
        { 
            SourcePath = "\\Server\share\path\file.ext" 
            DestinationPath = "C:\destinationPath" 
            Credential = $credential 
        } 
        
        LocalConfigurationManager 
        { 
             CertificateId = $node.Thumbprint 
        } 
    } 
}
```

## Ausführen der Konfiguration

An dieser Stellen können Sie die Konfiguration ausführen, woraufhin zwei Dateien ausgegeben werden:

* Eine Datei des Typs „*.meta.mof“, die vom lokalen Konfigurations-Manager zum Entschlüsseln der Anmeldeinformationen mithilfe des Zertifikats verwendet wird, das sich im lokalen Computerspeicher befindet und von dessen Fingerabdruck bestimmt wird. „Set DscLocalConfigurationManager“ wendet die Datei „*.meta.mof“ an.
* Eine MOF-Datei, die die Konfiguration tatsächlich anwendet. „Start-DscConfiguration“ wendet die Konfiguration an.

Mit diesen Befehlen werden diese Schritte ausgeführt:

```powershell
Write-Host "Generate DSC Configuration..."
CredentialEncryptionExample -ConfigurationData $ConfigData -OutputPath .\CredentialEncryptionExample

Write-Host "Setting up LCM to decrypt credentials..."
Set-DscLocalConfigurationManager .\CredentialEncryptionExample -Verbose 
 
Write-Host "Starting Configuration..."
Start-DscConfiguration .\CredentialEncryptionExample -wait -Verbose
```

Es folgt ein vollständiges Beispiel, das alle diese Schritte enthält, sowie ein Hilfs-Cmdlet zum Exportieren und Kopieren der öffentlichen Schlüssel:

```powershell
# A simple example of using credentials
configuration CredentialEncryptionExample
{
    param(
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [PsCredential] $credential
        )
    

    Node $AllNodes.NodeName
    {
        File exampleFile
        {
            SourcePath = "\\server\share\file.txt"
            DestinationPath = "C:\Users\user"
            Credential = $credential
        }
        
        LocalConfigurationManager
        {
            CertificateId = $node.Thumbprint
        }
    }
}

# A Helper to invoke the configuration, with the correct public key 
# To encrypt the configuration credentials
function Start-CredentialEncryptionExample
{
    [CmdletBinding()]
    param ($computerName)


    [string] $thumbprint = Get-EncryptionCertificate -computerName $computerName -Verbose
    Write-Verbose "using cert: $thumbprint"

    $certificatePath = join-path -Path "$env:SystemDrive\$script:publicKeyFolder" -childPath "$computername.EncryptionCertificate.cer"         

    $ConfigData=    @{
        AllNodes = @(     
                        @{  
                            # The name of the node we are describing
                            NodeName = "$computerName"

                            # The path to the .cer file containing the
                            # public key of the Encryption Certificate
                            CertificateFile = "$certificatePath"

                            # The thumbprint of the Encryption Certificate
                            # used to decrypt the credentials
                            Thumbprint = $thumbprint
                        };
                    );    
    }

    Write-Verbose "Generate DSC Configuration..."
    CredentialEncryptionExample -ConfigurationData $ConfigData -OutputPath .\CredentialEncryptionExample `
        -credential (Get-Credential -UserName "$env:USERDOMAIN\$env:USERNAME" -Message "Enter credentials for configuration") 

    Write-Verbose "Setting up LCM to decrypt credentials..."
    Set-DscLocalConfigurationManager .\CredentialEncryptionExample -Verbose 

    Write-Verbose "Starting Configuration..."
    Start-DscConfiguration .\CredentialEncryptionExample -wait -Verbose

}


#region HelperFunctions

# The folder name for the exported public keys
$script:publicKeyFolder = "publicKeys"

# Get the certificate that works for encryptions
function Get-EncryptionCertificate
{
    [CmdletBinding()]
    param ($computerName)
    $returnValue= Invoke-Command -ComputerName $computerName -ScriptBlock {
            $certificates = dir Cert:\LocalMachine\my

            $certificates | %{
                    # Verify the certificate is for Encryption and valid
                    if ($_.PrivateKey.KeyExchangeAlgorithm -and $_.Verify())
                    {
                        # Create the folder to hold the exported public key
                        $folder= Join-Path -Path $env:SystemDrive\ -ChildPath $using:publicKeyFolder
                        if (! (Test-Path $folder))
                        {
                            md $folder | Out-Null
                        }

                        # Export the public key to a well known location
                        $certPath = Export-Certificate -Cert $_ -FilePath (Join-Path -path $folder -childPath "EncryptionCertificate.cer") 

                        # Return the thumbprint, and exported certificate path
                        return @($_.Thumbprint,$certPath);
                    }
                  }
        }
    Write-Verbose "Identified and exported cert..."
    # Copy the exported certificate locally
    $destinationPath = join-path -Path "$env:SystemDrive\$script:publicKeyFolder" -childPath "$computername.EncryptionCertificate.cer"
    Copy-Item -Path (join-path -path \\$computername -childPath $returnValue[1].FullName.Replace(":","$"))  $destinationPath | Out-Null

    # Return the thumbprint
    return $returnValue[0]
}
```<!--HONumber=Feb16_HO4-->
