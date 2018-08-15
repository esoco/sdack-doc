
# esoco-common
This library contains core functionality that is of use for almost any kind of application. It also uses only a limited number of Java APIs to be compatible with the JRE emulation of the [GWT library](http://gwtproject.org). The esoco-common library is divided into the following packages and functionalities.

## Package de.esoco.lib.model
This package contains several interfaces and implementations for the abstraction and representation of data models. Most notable here is the interface **DataModel** and it's sub-interfaces. While DataModel is just a simple description of indexed data it's derivations provide additional abstractions like sorting or remoting (i.e. client-server communication). Another important interface is **DataSet** which describes tabular sets of data that can be used as input for the rendering of visualizations. The package also contains some DataSet implementations.

## Package de.esoco.lib.property
The property package contains a large number of interfaces that allow to declare certain properties of classes. For example, the **TextAttribute** declares the method for objects with text. Other classes like **PropertyName** and **HasProperties** define generic properties and provide implementations to manage these properties in subclasses.