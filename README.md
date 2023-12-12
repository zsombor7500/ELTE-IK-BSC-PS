# ELTE-IK-Bsc, 1. félév Számrend PowerShell cheatsheet

| In a nutshell: |
| :-----: |
>  Lényegesebb dolgok kigyűjtve néhány példa szkriptel, melyek előjöhetnek ZH-n  

> Megjegyzés:
>> Nem fed le sok minden részletet, de azokra ennél a ZH-nál nagy eséllyel nem lesz szükség.


| Újfent megjegyezném: |
| :-----: |
> Biztos bele lehet kötni, meg szőrszálhasogatni, jelenleg ignoráljuk azokat (v. hagyj hátra suggestiont ha nagyon zavar valami)

| One-liner PS szkript pandorás feltöltéshez |
| :-----: |
```powershell
$n=read-host "Neptunkodod";$f="ps_cheatsheet.md";if($n.Length -eq 6 -and ($n|select-string -pattern "^[a-zA-Z0-9]{6}$")){$n=$n.ToLower();(new-object System.Net.WebClient).DownloadFile("https://github.com/zsombor7500/ELTE-IK-BSC-PS/blob/main/$f","$env:temp\$f");$c=$n.ToCharArray();invoke-expression "scp $env:temp\$f $n@pandora.inf.elte.hu:/afs/inf.elte.hu/user/$($c[0])/$($c[0]+$c[1])/$n/Asztal/$f";write-host "A cheatsheet sikeresen fel lett tltve a pandora-ra!"}else{write-host "Hibas neptunkod"}
```