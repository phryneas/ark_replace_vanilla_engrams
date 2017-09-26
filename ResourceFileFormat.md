# Ark Engram File Format:
* Offset 0xA3: begin of string section.  
in this section, there is always a 32-bit-number describing the length of a zero-terminated string that directly follows.  

the first string in that section is the ingame spawn name

execute this snippet in `powershell` to get a quick list of all installed mod resources:

```
(Get-ChildItem -Path $((Get-ItemProperty "HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall\Steam App 346110" -Name InstallLocation).InstallLocation + "\ShooterGame\Content\Mods") -Recurse -Filter PrimalItemResource*.uasset) |
    ForEach{
    $file = [System.IO.File]::Open($_.FullName, "Open");
    $reader = New-Object System.IO.BinaryReader -ArgumentList $file;
    $file.Seek(0xA3, "Begin") | Out-Null;
    $length = $reader.ReadUInt32();
    $bytes = $reader.ReadChars($length - 1);
    $string = New-Object System.String(@(,$bytes));
	Write-Output ($string);
	$file.Close()
} | sort | Get-Unique

```