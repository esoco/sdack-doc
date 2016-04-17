# User Interfaces

In SDACK user interfaces are created by creating interactive process steps. If a process encounters such an interactive step during execution it will stop and communicate with the application user to display data and collect input. If the user finishes the interaction the process will continue to run, either until the next interaction or to it's end. On a stop the framework queries all process parameters that have been declared as interactive by the causing step. Then it generates the corresponding user interface components and displays them to the user. Any input will be collected into the corresponding parameters and the process step will be notified if the process continues to run.

## InteractionFragment

The base for all process interactions is the class `InteractionFragment`. It is not a subclass of `ProcessStep` but they share a common base class (`ProcessFragment`). Although it is possible to have interactive process steps it is desirable to have re-usable user interface structures. Interaction fragments provide exactly that, allowing to combine multiple fragments in an interactive step. The root of an interaction always is a process step but that is handled transparently by the framework.

Most subclasses of `InteractionFragment` just need to implement the method `init()`. There they declare which process parameters shall be displayed to the user and which of these can receive input from the user. As process parameters are instances of `RelationType` (from the ObjectRelations framework) an interaction is defined by a list of parameter relation types. If fragments contain other fragments they just add the parameter lists of the sub-fragments into parameters that have a collection of relation types as their datatype. That means a complex interaction is defined by nested collections of process parameter relation types.

To modify the default presentation of interactive parameters a fragment can set corresponding properties as meta-data on the parameters. Most of these properties are defined in the class `UserInterfaceProperties`.

## Fragment Layout

The layout of a fragment defines how it's parameters are arranged in the generated UI. Because interactions are basically defined as lists of parameters the property to set the fragment layout is called `ListDisplayMode`. It is defined in the class `DataElementList`, a subclass of `DataElement`. Data elements are the data transport objects for the communication between server and client (i.e. process and UI). To set the layout of a fragment use the fluent parameter interface:

    fragmentParam().layout(ListDisplayMode.GRID);

Fragment layouts can be divided into several categories: simple, segmented, grouped, and structured. Simple layouts just displays one or more parameters without further constraints. Segmented layouts place parameters in specific areas of the available space. Grouped layouts display multiple parameter separately so that only one parameter (which may be a sub-fragment) is visible at a time. And structured layouts expect certain layout properties to be set on parameters to place them accordingly.

### Simple Layouts

* `FILL`: This mode simply fills the display area available to a fragment with a single parameter. Placing multiple parameters in this layout is not supported and may result in rendering problems or exception. (HTML: `div` with width and height set to 100%)
* `FLOW`: Parameters are arranged in a natural flow as defined by the UI context. For web applications that means that components will be placed by the web browsers layout engine. This can often be controlled by providing CSS styling.  (HTML: `div`)
* `MENU`: Adds all parameters to a structure that represents a menu or other navigation element. (HTML: `nav`)

### Segmented Layouts

* `DOCK`: Up to three parameters (or sub-fragments) can be arranged as left, right, and center elements. The left and/or right parameters must have an explicit size set so that the center element will fill the remaining space. To arrange the parameters vertically instead of horizontally the flag `VERTICAL` can be set on the fragment parameter.
* `SPLIT`: Similar to `DOCK` but the pre-set sizes of the border areas can be modified interactively by the user afterwards.

### Grouped Layouts

* `TABS`: All fragment parameter will be placed in distinct horizontal tabs of which only one can be visible at a time. The user can select the visible tab interactively but the fragment that also query and set the index of the currently active tab through the property `CURRENT_SELECTION`.
* `STACK`: Similar to `TABS` but the parameters are arranged in a vertical stack instead.
* `DECK`: This mode doesn't provide a interface for the user. Therefore the currently visible parameter can only be set by the fragment through `CURRENT_SELECTION`.
