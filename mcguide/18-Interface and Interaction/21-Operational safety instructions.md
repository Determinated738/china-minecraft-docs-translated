--- 
front: 
hard: Getting Started 
time: minutes 
--- 

# Operational Security 

## <span id="LoadPrefab">Failed to load custom control</span> 

If the custom control does not exist in the file where the custom control is located, or the file is illegal (does not conform to the json format, lacks the "namespace" node under the root node), this error will be generated. 

## <span id="DeletePrefab">Cannot delete the currently edited custom control</span> 

The currently edited custom control is not allowed to be deleted. 

## <span id="NamespaceDuplicate">UI name has been used by the system or native</span> 

Some native controls already exist in MC and occupy a certain namespace. Users should name UI files with other names 

## <span id="CircularInherit">Inheritance Circular Error</span> 

When editing a custom control, when the control inheritance relationship is complex, it is difficult to detect the circular error caused by inheritance. For example, if there are three controls A, B, and C, and the inheritance relationship is B inherits from A and C inherits from B, then when editing A, if C is instantiated in A and saved in A, it will indirectly cause the custom control C to include itself in the object inherited by it, resulting in a circular error when instantiating C. 

## <span id="CircularInclude">Inclusion Circular Error</span> 

When editing a custom control, when the control inheritance relationship and inclusion relationship are complex, it is easy to cause this inclusion circular error. For example, if there are three A, B, and C, and the inheritance relationship is that B inherits from C, and if C contains a child node inherited from A, when B does not rewrite its own child nodes, it is equivalent to B also containing a child node inherited from A. If the user is editing custom control A at this time, when B is instantiated in A, it will indirectly cause custom control A to contain nodes inherited from custom control A, thus causing a circular error. 

## <span id="AddVariable">Failed to add variable</span> 

The variable that the user is trying to update is a global variable or a variable type that the UI editor does not currently support, such as "\$variable_1": "\$variable_2" This type of variable references a variable, which will cause this error 

## <span id="UpdateVariable">Failed to update variable</span> 

For the cause of the error, see [Failed to add variable](#AddVariable). 

## <span id="LostRef">Variables cannot be resolved due to lost reference</span> 

For example, in an image type control, the basic property "alpha" references the variable "\$myAlpha", and the variable is declared in its parent component. When the image control is created as a custom control, the "\$myAlpha" variable does not exist in the custom control (assuming that the "\$myAlpha|default" variable is not declared in the control). Therefore, when the custom control is instantiated, its instance does not contain the variable at the beginning. If this instance is mounted under a parent node tree that does not contain the "\$myAlpha" variable, the instance will not be able to search for the "\$myAlpha" variable when parsing the property "alpha" and report a parsing error. 

Similarly, if a control is a universal control, the controls it inherits are parsed by variables. If the variable cannot be found, the inherited object cannot be parsed, causing it to become a broken control. 

Therefore, users will be prompted with this potential risk when deleting variables and creating custom controls. 

## <span id="CircularVariable">Circular Variable</span> 

When changing the variable value inherited by the universal control, the custom control corresponding to the variable value will be parsed and generated. Assume that universal control A inherits the variable "\$myCustomControl" and the value is "myNamespace.myCustomControl", that is, A inherits the custom control myCustomControl. If this custom control happens to contain a universal control that inherits the variable "\$myCustomControl", and this variable of the universal control is also parsed as "myNamespace.myCustomControl", then a variable loop will be caused, and the parsing of the loop variable will be continuously performed when parsing the inherited control.