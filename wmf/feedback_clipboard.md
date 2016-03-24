# „Clipboard“-Cmdlets
Die Cmdlets **Get-Clipboard** und **Set-Clipboard** vereinfachen das Übertragen von Inhalten in eine und aus einer Windows PowerShell-Sitzung. Im folgenden Beispiel wird der Datei-Explorer zum Kopieren von drei Dateien verwendet:

Sie können nun einfach auf den Inhalt der Zwischenablage als Liste von Dateien zugreifen:

PS C:\\&gt; Get-Clipboard -Format FileDropList

Directory: C:\\Users\\slee\\Downloads\\Example

Mode LastWriteTime Length Name

---- ------------- ------ ----

-a---- 4/14/2015 1:19 PM 0 File2.txt

-a---- 4/14/2015 1:19 PM 0 File3.txt

-a---- 4/14/2015 1:19 PM 0 File1.txt

Die „Clipboard“-Cmdlets unterstützen Bilder, Audiodateien, Dateilisten und Text.
<!--HONumber=Mar16_HO2-->
