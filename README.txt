======
PySide
======

.. contents:: **Table of Contents** 

Introduction
============

PySide is the Python Qt bindings project, providing access the complete Qt 4.8 framework
as well as to generator tools for rapidly generating bindings for any C++ libraries.

The PySide project is developed in the open, with all facilities you'd expect
from any modern OSS project such as all code in a git repository [1], an open
Bugzilla [2] for reporting bugs, and an open design process [3]. We welcome
any contribution without requiring a transfer of copyright.

Compatibility
=============

PySide requires Python 2.6 or later and Qt 4.6 or better.

Installing PySide from source on a Windows System
=================================================

Installing prerequisities
-------------------------

#. Install `Python 2.7
   <http://python.org/download/releases/2.7.3/>`_.

#. Install `Qt 4.8 libraries for Windows (VS 2008)
   <http://releases.qt-project.org/qt4/source/qt-win-opensource-4.8.2-vs2008.exe>`_.

#. Install `Cmake 2.8
   <http://www.cmake.org/cmake/resources/software.html>`_.

#. Install `MS Visual Studio Express 2008
   <http://www.microsoft.com/express/Downloads/>`_.

#. Install `Git 1.7
   <http://git-scm.com/download/win>`_.

#. (Optional) Install `OpenSSL
   <http://slproweb.com/products/Win32OpenSSL.html>`_.

#. Install latest `distribute` distribution into the Python you
   installed in the first step: download `distribute_setup.py
   <http://python-distribute.org/distribute_setup.py>`_ and run it using
   the ``python`` interpreter of your Python 2.7 installation using a
   command prompt:

   ::

      c:\> c:\Python27\python distribute_setup.py

#. Use that Python's `bin/easy_install` to install `virtualenv`:

   ::

      c:\> c:\Python27\Scripts\easy_install virtualenv

#. Use that Python's virtualenv to make a workspace:

   ::

      c:\> c:\Python27\Scripts\virtualenv env

#. Open Visual Studio 2008 Command Prompt:

   ::

      c:\> c:\ProgramData\Microsoft\Windows\Start Menu\Programs\Microsoft Visual Studio 2008\Visual Studio Tools\Visual Studio 2008 Command Prompt.lnk

#. Switch to the ``env`` directory:

   ::

      c:\> cd env

Installing PySide
-----------------

Use ``pip`` to get `PySide` installed:

::

   c:\env> Scripts\pip install PySide --install-option="--qmake=c:\\Qt\\4.8.2\\bin\\qmake.exe"

Optionally you can specify the path to OpenSSL libs:

::

   c:\env> Scripts\pip install PySide --install-option="--openssl=c:\\OpenSSL32bit\\bin" --install-option="--qmake=c:\\Qt\\4.8.2\\bin\\qmake.exe"

Building PySide installer
-------------------------

#. Clone ``PySide`` from git repository:

   ::

      c:\> git clone https://github.com/PySide/pyside-setup.git pyside-setup

#. Switch to the ``pyside-setup`` directory:

   ::

      c:\> cd pyside-setup

#. Build ``PySide`` windows installer:

   ::

      c:\> c:\Python27\python setup.py bdist_wininst --qmake=c:\Qt\4.8.2\bin\qmake.exe --openssl=c:\OpenSSL32bit\bin

Installing PySide from source on a UNIX System (Ubuntu 12.04 LTS)
=================================================================

Installing prerequisities
-------------------------

#. Install Python 2.7 header files and a static library:
    
   ::

      $ sudo apt-get install python2.7-dev
   
#. Install Qt 4.8 libraries:
    
   ::

      $ sudo apt-get install qt-sdk
   
#. Install cmake:
    
   ::

      $ sudo apt-get install cmake

#. Install git:
    
   ::

      $ sudo apt-get install git
   
#. Install latest `distribute` distribution into the Python you
   installed in the first step: download `distribute_setup.py
   <http://python-distribute.org/distribute_setup.py>`_ and run it using
   the ``python`` interpreter of your Python 2.7 installation using a
   command prompt:

   ::

      $ sudo python distribute_setup.py

#. Use that Python's `bin/easy_install` to install `virtualenv`:

   ::

      $ sudo easy_install virtualenv

#. Use that Python's virtualenv to make a workspace:

   ::

      $ virtualenv env

Installing PySide
-----------------

Use ``pip`` to get `PySide` installed from PyPI:

::

   $ env/bin/pip install PySide

Alternatively you can install development version of `PySide` from github repository:

::

   $ env/bin/pip install git+https://github.com/PySide/pyside-setup.git

You can also specify version of `PySide` when installing from github repository:

::

   $ env/bin/pip install git+https://github.com/PySide/pyside-setup.git@1.1.1

Building PySide distribution egg
--------------------------------

#. Clone ``PySide`` from git repository:

   ::

      $ git clone https://github.com/PySide/pyside-setup.git pyside-setup

#. Switch to the ``pyside-setup`` directory:

   ::

      $ cd pyside-setup

#. Build ``PySide`` distribution egg:

   ::

      $ env/bin/python setup.py bdist_egg

#. Optionally you can build standalone version of distribution egg with embedded Qt libs:

   ::

      $ env/bin/python setup.py bdist_egg --standalone

Feedback and getting involved
=============================

- Mailing list: http://lists.qt-project.org/mailman/listinfo/pyside
- Issue tracker: https://bugreports.qt-project.org/browse/PYSIDE
- Code Repository: http://qt.gitorious.org/pyside

Changes
=======

1.1.2 (2012-08-28)
------------------

Bug fixes
~~~~~~~~~

- During signal emission don't get return type after callback
- Invalidate QStandardModel::invisibleRootItem in clear() method
- QAbstractItemModel has wrong ownership policy for selectionModel()
- Improved QVector to python conversion
- Disable docstring generation if tools aren't found.
- Fixed some issues compiling PySide using VC++
- Install the shiboken module to site-packages
- Fix compilation when there is no libxslt installed on the system.
- Set a default hash function for all ObjectTypes.
- Fix segfault calling shiboken.dump

1.1.1 (2012-04-19)
------------------

Major changes
~~~~~~~~~~~~~

- Unified toolchain! No more GeneratorRunner and ApiExtractor, now you just need Shiboken to compile PySide.

Bug fixes
~~~~~~~~~

- 1105 Spyder fails with HEAD
- 1126 Segfault when exception is raised in signalInstanceDisconnect
- 1135 SIGSEGV when loading custom widget using QUiLoader when overriding createWidget()
- 1041 QAbstractItemModel has wrong ownership policy for selectionModel()
- 1086 generatorrunner segfault processing #include
- 1110 Concurrency error causes GC heap corruption
- 1113 Instantiating QObject in user-defined QML element's constructor crashes if instantiated from QML
- 1129 Segmentation fault on close by QStandardItem/QStandardItemModel
- 1104 QSettings has problems with long integers
- 1108 tests/QtGui/pyside_reload_test.py fails when bytecode writing is disabled
- 1138 Subclassing of QUiLoader leads to "Internal C++ object already deleted" exception (again)
- 1124 QPainter.drawPixmapFragments should take a list as first argument
- 1065 Invalid example in QFileDialog documentation
- 1092 shiboken names itself a 'generator'
- 1094 shiboken doesn't complain about invalid options
- 1044 Incorrect call to parent constructor in example
- 1139 Crash at exit due to thread state (tstate) being NULL
- PYSIDE-41 QModelIndex unhashable

1.1.0 (2012-01-02)
------------------

Major changes
~~~~~~~~~~~~~

- New type converter scheme

Bug fixes
~~~~~~~~~

- 1010 Shiboken Cygwin patch
- 1034 Error compiling PySide with Python 3.2.2 32bit on Windows
- 1040 pyside-uic overwriting attributes before they are being used
- 1053 pyside-lupdate used with .pro files can't handle Windows paths that contain spaces
- 1060 Subclassing of QUiLoader leads to "Internal C++ object already deleted" exception
- 1063 Bug writing to files using "QTextStream + QFile + QTextEdit" on Linux
- 1069 QtCore.QDataStream silently fails on writing Python string
- 1077 Application exit crash when call QSyntaxHighlighter.document()
- 1082 OSX binary links are broken
- 1083 winId returns a PyCObject making it impossible to compare two winIds
- 1084 Crash (segfault) when writing unicode string on socket
- 1091 PixmapFragment and drawPixmapFragments are not bound
- 1095 No examples for shiboken tutorial
- 1097 QtGui.QShortcut.setKey requires QKeySequence
- 1101 Report invalid function signatures in typesystem
- 902 Expose Shiboken functionality through a Python module
- 969 viewOptions of QAbstractItemView error

1.0.9 (2011-11-29)
------------------

Bug fixes
~~~~~~~~~

- 1058 Strange code in PySide/QtUiTools/glue/plugins.h
- 1057 valgrind detected "Conditional jump or move depends on uninitialised value"
- 1052 PySideConfig.cmake contains an infinite loop due to missing default for SHIBOKEN_PYTHON_SUFFIX
- 1048 QGridLayout.itemAtPosition() crashes when it should return None
- 1037 shiboken fails to build against python 3.2 (both normal and -dbg) on i386 (and others)
- 1036 Qt.KeyboardModifiers always evaluates to zero
- 1033 QDialog.DialogCode instances and return value from \QDialog.exec_ hash to different values
- 1031 QState.parentState() or QState.machine() causes python crash at exit
- 1029 qmlRegisterType Fails to Increase the Ref Count
- 1028 QWidget winId missing
- 1016 Calling of Q_INVOKABLE method returning not QVariant is impossible...
- 1013 connect to QSqlTableModel.primeInsert() causes crash
- 1012 FTBFS with hardening flags enabled
- 1011 PySide Cygwin patch
- 1010 Shiboken Cygwin patch
- 1009 GeneratorRunner Cygwin patch
- 1008 ApiExtractor Cygwin patch
- 891 ApiExtractor doesn't support doxygen as backend to doc generation.

1.0.8 (2011-10-21)
------------------

Major changes
~~~~~~~~~~~~~

- Experimental Python3.2 support
- Qt4.8 beta support

Bug fixes
~~~~~~~~~

- 1022 RuntimeError: maximum recursion depth exceeded while getting the str of an object
- 1019 Overriding QWidget.show or QWidget.hide do not work
- 944 Segfault on QIcon(None).pixmap()

1.0.7 (2011-09-21)
------------------

Bug fixes
~~~~~~~~~

- 996 Missing dependencies for QtWebKit in buildscripts for Fedora
- 986 Documentation links
- 985 Provide versioned pyside-docs zip file to help packagers
- 981 QSettings docs should empathize the behavior changes of value() on different platforms
- 902 Expose Shiboken functionality through a Python module
- 997 QDeclarativePropertyMap doesn't work.
- 994 QIODevice.readData must use qmemcpy instead of qstrncpy
- 989 Pickling QColor fails
- 987 Disconnecting a signal that has not been connected
- 973 shouldInterruptJavaScript slot override is never called
- 966 QX11Info.display() missing
- 959 can't pass QVariant to the QtWebkit bridge
- 1006 Segfault in QLabel init
- 1002 Segmentation fault on PySide/Spyder exit
- 998 Segfault with Spyder after switching to another app
- 995 QDeclarativeView.itemAt returns faulty reference. (leading to SEGFAULT)
- 990 Segfault when trying to disconnect a signal that is not connected
- 975 Possible memory leak
- 991 The __repr__ of various types is broken
- 988 The type supplied with currentChanged signal in QTabWidget has changed in 1.0.6

1.0.6 (2011-08-22)
------------------

Major changes
~~~~~~~~~~~~~

- New documentation layout;
- Fixed some regressions from the last release (1.0.5);
- Optimizations during anonymous connection;

Bug fixes
~~~~~~~~~

- 972 anchorlayout.py of graphicsview example raised a unwriteable memory exception when exits
- 953 Segfault when QObject is garbage collected after QTimer.singeShot
- 951 ComponentComplete not called on QDeclarativeItem subclass
- 965 Segfault in QtUiTools.QUiLoader.load
- 958 Segmentation fault with resource files
- 944 Segfault on QIcon(None).pixmap()
- 941 Signals with QtCore.Qt types as arguments has invalid signatures
- 964 QAbstractItemView.moveCursor() method is missing
- 963 What's This not displaying QTableWidget column header information as in Qt Designer
- 961 QColor.__repr__/__str__ should be more pythonic
- 960 QColor.__reduce__ is incorrect for HSL colors
- 950 implement Q_INVOKABLE
- 940 setAttributeArray/setUniformValueArray do not take arrays
- 931 isinstance() fails with Signal instances
- 928 100's of QGraphicItems with signal connections causes slowdown
- 930 Documentation mixes signals and functions.
- 923 Make QScriptValue (or QScriptValueIterator) implement the Python iterator protocol
- 922 QScriptValue's repr() should give some information about its data
- 900 QtCore.Property as decorator
- 895 jQuery version is outdated, distribution code de-duplication breaks documentation search
- 731 Can't specify more than a single 'since' argument
- 983 copy.deepcopy raises SystemError with QColor
- 947 NETWORK_ERR during interaction QtWebKit window with server
- 873 Deprecated methods could emit DeprecationWarning
- 831 PySide docs would have a "Inherited by" list for each class

1.0.5 (2011-07-22)
------------------

Major changes
~~~~~~~~~~~~~

- Widgets present on "ui" files are exported in the root widget, check PySide ML thread for more information[1];
- pyside-uic generate menubars without parent on MacOS plataform;
- Signal connection optimizations;

Bug fixes
~~~~~~~~~

- 892 Segfault when destructing QWidget and QApplication has event filter installed
- 407 Crash while multiple inheriting with QObject and native python class
- 939 Shiboken::importModule must verify if PyImport_ImportModule succeeds
- 937 missing pid method in QProcess
- 927 Segfault on QThread code.
- 925 Segfault when passing a QScriptValue as QObject or when using .toVariant() on a QScriptValue
- 905 QtGui.QHBoxLayout.setMargin function call is created by pyside-uic, but this is not available in the pyside bindings
- 904 Repeatedly opening a QDialog with Qt.WA_DeleteOnClose set crashes PySide
- 899 Segfault with 'QVariantList' Property.
- 893 Shiboken leak reference in the parent control
- 878 Shiboken may generate incompatible modules if a new class is added.
- 938 QTemporaryFile JPEG problem
- 934 A __getitem__ of QByteArray behaves strange
- 929 pkg-config files do not know about Python version tags
- 926 qmlRegisterType does not work with QObject
- 924 Allow QScriptValue to be accessed via []
- 921 Signals not automatically disconnected on object destruction
- 920 Cannot use same slot for two signals
- 919 Default arguments on QStyle methods not working
- 915 QDeclarativeView.scene().addItem(x) make the x object invalid
- 913 Widgets inside QTabWidget are not exported as members of the containing widget
- 910 installEventFilter() increments reference count on target object
- 907 pyside-uic adds MainWindow.setMenuBar(self.menubar) to the generated code under OS X
- 903 eventFilter in ItemDelegate
- 897 QObject.property() and QObject.setProperty() methods fails for user-defined properties
- 896 QObject.staticMetaObject() is missing
- 916 Missing info about when is possible to use keyword arguments in docs [was: QListWidgetItem's constructor ignores text parameter]
- 890 Add signal connection example for valueChanged(int) on QSpinBox to the docs
- 821 Mapping interface for QPixmapCache
- 909 Deletion of QMainWindow/QApplication leads to segmentation fault

References
==========

- [1] http://qt.gitorious.org/pyside
- [2] https://bugreports.qt-project.org/browse/PYSIDE
- [3] http://www.pyside.org/docs/pseps/psep-0001.html
- [4] http://developer.qt.nokia.com/wiki/PySideDownloads
