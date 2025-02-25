Install `py2app`.

```zsh
pip install py2app
```

Create `setup.py`.
`py2app` does not handle dependency very well.
The `cffi` python package needs to be added manually.

```zsh
py2applet \
  --packages=cffi \
  --iconfile=./icon/logo.ico \
  --make-setup ./MicroTaxaApp.py
```

Build the app.

```zsh
python setup.py py2app
```

This x86_64 version of `libffi.8.dylib` was acquired from Anaconda.
It needs to be copied to the app bundle.

```zsh
cp ./lib/libffi.8.dylib ./dist/MicroTaxaApp.app/Contents/Frameworks/
```

Run the app from the command line. It can also be run by double clicking the app.

```zsh
dist/MicroTaxaApp.app/Contents/MacOS/MicroTaxaApp
```

Move, compress the app, and clean up.

```zsh
export VERSION="v0.0.0"

mv dist/MicroTaxaApp.app ./
zip -r MicroTaxaApp-mac-$VERSION.zip MicroTaxaApp.app

rm -r dist
rm -r build
rm setup.py
```
