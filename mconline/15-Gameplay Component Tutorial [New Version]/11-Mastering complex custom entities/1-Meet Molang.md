--- 
front: https://nie.res.netease.com/r/pic/20211104/69055361-2e7a-452f-8b1a-f23e1262a03a.jpg 
hard: Advanced 
time: 20 minutes 
--- 

# Get to know Molang 

**Molang** is an expression-based scripting language that aims to use a simple scripting language to implement complex behaviors in lower-level systems without breaking away from data-driven. Of course, we can still use Molang in scripts, which helps us easily get the values of some internal members or flags, and can also achieve more complex linkage with data-driven. Molang is often used in entity resource control or world generator-related operations, and supports the calculation of single simple expressions and multi-line complex expressions. 

## Basic concepts 

Molang often appears as a field value in data-driven JSON files, which is often a string. The expression in the string is a Molang expression. For example: 

```json 
"some_field": "math.sin(query.anim_time * 1.23)" 
``` 

In which `math.sin(query.anim_time * 1.23)` is a Molang expression. According to the latest international standard, a Molang **expression** (**Expression**) refers to the sum of all Molang statements enclosed in quotation marks. If there are multiple statements in an expression, each statement is called a **Sub-expression** (**Sub-expression**). For example: 

```cpp 
temp.moo = math.sin(query.anim_time * 1.23); 
temp.baa = math.cos(query.life_time + 2.0); 
return temp.moo * temp.moo + temp.baa; 
``` 

There are three statements, two assignment statements and one return statement. Each of these three statements is called a Molang subexpression. In the latest standard, we do not use the word "script" to refer to Molang. 

From the above example, we can see that there are two forms of Molang expressions. One is an expression that contains only one statement, and there is no `;` at the end as an "end marker". This expression is called a **Simple Expression**. The other is an expression that contains multiple subexpressions (that is, multiple statements). Each subexpression must have a `;` at the end as an "end marker". This expression is called a **Complex Expression**. Both expressions can be written as Molang parameters in the value of the JSON field. When a complex expression is a string value, all statements can be written on the same line, or they can be wrapped and indented, similar to: 

```json 
{ 
"some_field": " 
temp.moo = math.sin(query.anim_time * 1.23); 
temp.baa = math.cos(query.life_time + 2.0); 
return temp.moo * temp.moo + temp.baa; 
", 
"some_other_field": "something" 
// ... 
} 
``` 

Minecraft can parse this kind of wrapped Molang fields, and only Molang fields can be parsed in this way. If a field only accepts ordinary strings, the engine cannot parse it in a wrapped and indented manner like the example above. 

Every Molang expression must return a value. Simple expressions will return the value calculated by the statement itself. If the statement is a Boolean check, the result value of the Boolean check is returned, `true` is equivalent to `1.0`, and `false` is equivalent to `0.0`. If the statement does not produce a value, `0.0` will be returned. 

If it is a complex expression, you need to use a `return` sub-expression to return the value. If there is no such return statement, no matter how "intense" the intermediate calculation is, only a `0.0` will be returned in the end. 

## Operators and Keywords 


There are many operators and keywords in Molang, all of which are listed below. It is worth noting that except for the content inside strings, letters in Molang are case-insensitive, that is, there is no difference between uppercase and lowercase letters. 

| Operator, keyword or literal | Description | 
| --------------------------------- | ------------------------------------------------------------ | 
| `1.23` | A numeric constant value. | 
| `! && || < <= >= > == !=` | Logical operators, namely negation, and, or, less than, less than or equal to, greater than or equal to, greater than, equal to, and not equal to operators. | 
| `* / + -` | Basic mathematical operators, namely multiplication, division, addition, and subtraction operators. | 
| `(` `)` | Parentheses used to control the evaluation of terms in an expression, and also used to pass parameters to query functions with parameters. | 
| `[` `]` | Square brackets used to access arrays. | 
| `{` `}` | Curly braces used to control the execution scope. | 
| `??` | Null coalescing operator, used to handle missing variables and stale live object references. | 
| `<test> ? <if true>` | Binary conditional operator. | 
| `<test> ? <if true> : <if false>` | Ternary conditional operator. | 
| `->` | Arrow operator, used to access data from a different entity. | 
| `geometry.geometry_name` | A short name reference to a geometry named in the entity definition file. | 
| `material.material_name` | A short name reference to a material named in the entity definition file. | 
| `texture.texture_name` | A short name reference to a texture named in the entity definition file. | 
| `math.function_name` | For accessing various math functions. | 
| `query.function_name` | For accessing properties of an entity. | 
| `variable.variable_name` | Read and write the memory of a live object. | 
| `temp.variable_name` | Read and write temporary storage. | 
| `context.variable_name` | Access read-only storage provided by the game in some scenarios. | 
| `this` | The current value of the value that the expression (given the specified context) eventually writes. | 
| `return` | Designed for complex expressions, this will evaluate the statement immediately following the keyword and stop the execution of the entire expression, returning the calculated value. | 
| `loop` | Used to execute one or more commands repeatedly. | 
| `for_each` | Used to iterate over an array of entities. | 
| `break` | Used to exit the scope of a `loop` or `for_each` prematurely. | 
| `continue` | Used to skip the rest of the set of statements iterated by a `loop` or `for_each` and move to the next iteration. | 

For detailed usage of the above operators or keywords, please refer to the [Molang documentation hosted on bedrock.dev](https://bedrock.dev/zh/b/Molang). 

## Query Function 

Among the keywords listed above, there is a special variable type called **Query Function**, whose syntax is `query.function_name`, where `function_name` is a query function name. As the name implies, a query function is a function used to query the value of an attribute. Various values including **Global Parameter**, **Entity Member**, and **Entity Flag** can be queried by the query function. 

Query functions are divided into **parameterless query functions** and **parameterized query functions**. A parameterless query function is a query function without a parameter list. For this type of query function, you can get the return of the corresponding attribute by simply writing its function name. For example, `query.anim_time` in the example at the beginning of this section is a parameterless query function used to query a global parameter `anim_time`. 

A parameterized query function refers to a query function that first passes in some parameters as a basis to query a specific value. Such a query function needs to be followed by a pair of parentheses (`(` `)`), and then the parameter list is written in the parentheses. For example, in the following example, the `query.get_nearby_entities` function accepts a numeric value as its first parameter and a string as its second parameter. 

```cpp 
v.x = 0; 
for_each(v.pig, query.get_nearby_entities(4, 'minecraft:pig'), { 
v.x = v.x + v.pig->query.get_relative_block_state(0, 1, 0, 'flammable'); 
}); 
``` 

The specific query function list can still be found in the [Molang document hosted on bedrock.dev](https://bedrock.dev/zh/b/Molang). Select the version that matches the current Chinese version of Minecraft in the version list to view the query function list for the corresponding version. 

## Custom variables 


Molang has various **Variable**. Variables can be used to store a value for subsequent access. There are three types of variables in Molang, namely entity variables, temporary variables and context variables. 

**Entity Variable** is a variable stored on an entity. The entity here refers to the general entity, which refers to the entity in the ECS framework, including blocks, items, particles, world generators, etc. The life cycle of the entity variable is consistent with the entity. When the entity is destroyed in memory (for example, the entity disappears in the world), its entity variable will also be destroyed and become inaccessible. We define this variable using the `variable.variable_name` syntax. 

**Temp Variable** is a variable stored in a temporary register. This variable is valid in the scope in which they are defined and will be destroyed after the scope operation ends. However, due to some defects, the current temporary variable life cycle is still global, so be extra careful when naming temporary variables. This variable is defined using the `temp.variable_name` syntax. 

**Context Variable** is a read-only variable that can only be defined by the hard-coded game engine. This variable exists depending on the context of the game running state. For example, in the anvil context, there is `context.other` representing the second input slot of the anvil. If it is out of the anvil environment, the variable will not exist. This variable is defined using the `context.variable_name` syntax. 

Developers can flexibly customize entity variables and temporary variables, rewrite or access the values of various variables on the appropriate real machine, so that development can be done with twice the result with half the effort.