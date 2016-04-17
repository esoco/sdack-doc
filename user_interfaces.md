# User Interfaces

In SDACK user interfaces are created by creating interactive process steps. If a process encounters such an interactive step during execution it will stop and communicate with the application user to display data and collect input. If the user finishes the interaction the process will continue to run, either until the next interaction or to it's end. On a stop the framework queries all process parameters that have been declared as interactive by the causing step. Then it generates the corresponding user interface components and displays them to the user. Any input will be collected into the corresponding parameters and the process step will be notified if the process continues to run.

## InteractionFragment

The base for all process interactions is the class `InteractionFragment`. It is not a subclass of `ProcessStep` but they share a common base class (`ProcessFragment`). This is because for user interfaces it is desirable to have re-usable blocks that can be arranged side-by-side if necessary. Therefore interaction fragments can be combined 