# firefox_skins
Skins listed as branches

To automate switching add the following lines to `$PROFILE` (.ps1) file

```pwsh
Function ffskin {
	cd $env:FOME
	$list = git branch
	Write-host "Available Choices ..." -foregroundcolor "cyan"
	echo $list
	Write-host ".. more .." -foregroundcolor "cyan"
	Write-host "Enter Firekox skin preference ..." -foregroundcolor "cyan"
	$name = Read-Host -Prompt "> " 
	If($name -eq "more") {
		git branch -r
		$name = Read-Host -Prompt "> " 
	}
	git checkout $name
	
	If(Test-Path -path "../user.js" -PathType Leaf){
		rm ../user.js
		cp ./user.js ../user.js
	}
	cd
}

```
