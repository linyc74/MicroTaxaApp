Install PyInstaller

```PowerShell
pip install PyInstaller
```

Package as a .exe file

```PowerShell
$VERSION = "v0.0.0"
pyinstaller --clean --onefile --icon="icon/logo.ico" --add-data="icon;icon" MicroTaxaApp.py
Move-Item -Path "dist\MicroTaxaApp.exe" -Destination "MicroTaxaApp-win-$VERSION.exe"
rm -r build ; rm -r dist ; rm MicroTaxaApp.spec
```

Package as a folder

```PowerShell
$VERSION = "v0.0.0"
pyinstaller --clean --icon="icon/logo.ico" --add-data="icon;icon" MicroTaxaApp.py
Move-Item -Path "dist\MicroTaxaApp.exe" -Destination "MicroTaxaApp.exe"
Compress-Archive -Path "MicroTaxaApp" -DestinationPath "MicroTaxaApp-win-$VERSION.zip"
rm -r build ; rm -r dist ; rm -r MicroTaxaApp ; rm MicroTaxaApp.spec
```
