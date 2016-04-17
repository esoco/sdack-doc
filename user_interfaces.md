# User Interfaces

In SDACK user interfaces are created by creating interactive process steps. If a process encounters such an interactive step during execution it will stop and communicate with the application user to display data and collect input. If the user finishes the interaction the process will continue to run, either until the next interaction or to it's end. On a stop the framework queries all process parameters that have been declared as interactive by the causing step. Then it generates the corresponding user interface components and displays them to the user. Any input will be collected into the corresponding parameters and the process step will be notified if the process continues to run.

## InteractionFragment

The base for all process interactions is the class `InteractionFragment`. It is not a subclass of `ProcessStep` but they share a common base class (`ProcessFragment`). Although it is possible to have interactive process steps it is desirable to have re-usable user interface structures. Interaction fragments provide exactly that, allowing to combine multiple fragments in an interactive step. The root of an interaction always is a process step but that is handled transparently by the framework.

Most subclasses of `InteractionFragment` just need to implement the method `init()`. There they declare which process parameters shall be displayed to the user and which of these can receive input from the user. As process parameters are instances of `RelationType` (from the ObjectRelations framework) an interaction is defined by a list of parameter relation types. If fragments contain other fragments they just add the parameter lists of the sub-fragments into parameters that have a collection of relation types as their datatype. That means a complex interaction is defined by nested collections of process parameter relation types.

To modify the default presentation of interactive parameters a fragment can set corresponding properties as meta-data on the parameters.

## Fragment Layout

An interaction is defined by the process parameters it displays. That means that an interaction basically is nothing else as a list of process parameters. If an interaction fragment contains other fragments it simply places the sub-fragment's parameter in an own parameter that is defined as a list of parameter relation types.