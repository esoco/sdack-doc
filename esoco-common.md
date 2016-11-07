
# esoco-common
This library contains core functionality that is of use for almost any kind of application. It also uses only a limited number of Java APIs to be compatible with the JRE emulation of the [GWT library](http://gwtproject.org). The esoco-common library is divided into the following packages and functionalities.

## de.esoco.lib.model
This package contains several interfaces and implementations for the abstraction and representation of data models. Most notable here is the interface **DataModel** and it's sub-interfaces. While DataModel is just a simple description of indexed data (quite similar to a collection) it's derivations provide additional abstractions like sorting or remoting (i.e. client-server communication).

