## pd-comma
[comma ] object for [Pure Data](https://github.com/pure-data/pure-data) - a free real-time computer music system. 

### Overview

A utility object that adds or removes commas from a message.

### Description

[comma ] has just one input and one output. The input accepts any message but processes messages differently depending on the number of atoms in addition to the selector.

Reminder: messages that begin with a number are automatically given the selector 'list' unless there is only one number in the message, in which case that number is given the selector 'float'. In all other cases, the selector is set to the first element in the message box.

Reminder: if the elements of a message are separated by commas, they are treated as separate messages and are output one at a time, rapid-fire.

If an incoming message contains just one atom, then that atom is stored in an internal memory array without clearing previously stored atoms, thus accumulating atoms in internal memory. Each time the internal memory is modified, the array of atoms is output along with the selector 'set' so that the atoms can be stored in a message box. If the atoms originated from a single message box with multiple atoms separated by commas, than the output message box will end up containing all of the atoms but without the commas, effectively removing the commas.

If the incoming message contains more than one atom, a 'list' selector is checked for. If missing, the message is ignored. Otherwise, the atoms are stored in internal memory separated by comma atoms, after clearing any previously stored atoms. The stored array is then ouput with a 'set' selector so that it can be stored in a message box. The new message consists of comma-separated atoms.

A 'bang' sent to the input will clear the internal memory array and output a 'set' selector without any atoms, which has the effect of clearing the message box connected to the output.

### Installation

The comma.c file can be compiled into a Pure Data external using [pure-data/pd-lib-builder](https://github.com/pure-data/pd-lib-builder). Simply place the linked file (e.g. comma.pd_linux) along with the help patch comma-help.pd into the same directory as your patch, or somewhere on the Pd search path (e.g., externals/comma folder).
