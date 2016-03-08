# Selber kompilieren #

Voraussetzungen:

  * C++-Compiler (unter Windows idealerweise der Compiler aus [Visual Studio 2012](http://go.microsoft.com/?linkid=9816757), GCC aus dem [MinGW](http://www.mingw.org/)-Paket sollte aber ebenfalls funktionieren, unter Linux die GNU Compiler Collection und unter Mac OS X der mit den Developer Tools installierte clang)
  * Auf allen Plattformen empfiehlt sich der Qt Creator als Entwicklungsumgebung.
  * [OpenCV](http://opencv.org/)-Bibliothek
  * [Qt SDK](http://qt-project.org/downloads)

## Windows ##

Windows-User, die Visual Studio 2012 verwenden, müssen [Qt 5.0.1 aus den Quellen](http://download.qt-project.org/official_releases/qt/5.0/5.0.1/single/qt-everywhere-opensource-src-5.0.1.zip) übersetzen, um die Unterstützung für Desktop-OpenGL zu erhalten, die standardmäßig nicht im vorkompilierten Qt SDK enthalten ist. Zum Übersetzen müssen Perl und Python installiert sein. Wir haben [ActivePerl 5.16.3](http://www.activestate.com/activeperl/downloads) und [ActivePython 2.7.2.5](http://www.activestate.com/activepython/downloads) verwendet. Das Übersetzen der aktuellen Version 5.0.2 schlug in unseren Experimenten stets fehl.

Entpacken Sie das Quelltext-Archiv beispielsweise nach D:\Developer\qt-everywhere-opensource-src-5.0.1 und führen dann in der Visual-Studio-Eingabeaufforderung folgende Kommandos aus:

```
> set PATH=%PATH%;C:\Python27
> D:
> cd \Developer\qt-everywhere-opensource-src-5.0.1
> configure.bat -prefix D:\Developer\Qt502-VS2012 -opengl desktop \
    -qt-zlib -qt-libpng -qt-libjpeg -no-icu -no-iconv -no-angle \
    -no-sse2 -no-sse3 -no-ssse3 -no-sse4.1 -no-sse4.2 -no-avx \
    -no-avx2 -platform win32-msvc2012
```

`C:\Python27` ist durch den tatsächlichen Pfad zur Python-Installation zu ersetzen.

Nun installieren Sie [OpenCV](http://surfnet.dl.sourceforge.net/project/opencvlibrary/opencv-win/2.4.5/OpenCV-2.4.5.exe).

Sie können die Projektdatei GLSL-Live-Coder.pro jetzt mit dem Qt Creator öffnen. Sodann erscheint ein Konfigurationsdialog: Wenn Sie das Archiv zum Beispiel nach D:\Developer\opencv entpackt haben, dann müssen Sie unter "Projects/Build/Build Environment" die Umgebungsvariable `INCLUDE` um "D:\Developer\opencv\build\include\opencv;D:\Developer\opencv\build\include\opencv2" ergänzen, sowie `PATH` in der Ausführungsumgebung um "D:\Developer\opencv\build\x86\_vcxx_\bin", wobei _vcxx_ für den verwendeten Compiler steht (_vc9_: Visual Studio 2008, _vc10_: Visual Studio 2010, _vc11_: Visual Studio 2012).

Mit Strg+B übersetzen Sie das Projekt. Mit F5 starten Sie es im Debug-Modus.

## Mac OS X ##

OpenCV via MacPorts installieren: http://opencv.willowgarage.com/wiki/UsingOpenCVUnderOSX

Im Qt Creator ist anschließend unter "Projects/Build/Build Environment" die Variable `INCLUDE` um "/opt/local/include" zu ergänzen.


## Linux ##

to do ...