CSVParser
==================================================
This Unity Library.
Parse CSV, And Make script by CSV data, even surpport scriptable object 

Package
==================================================

[Download](https://drive.google.com/file/d/1WAdqEXo2yCsxft-soXeJg5v-Z4o9AnlM/view?usp=sharing)

--------------------------------------------------

CSV Format rule:  
==================================================
    first row: field or property name line  
    second row: field or property type line  
    (Type name int / float / string is wrong, use Int32 / Single / String) 
    over third lines: data line

Example:

|SerialNumber|Name|Age|
|:-:|:------:|:--:|
|Int32|String|Int32|
|1|1Human1|10|
|2|Human2|20|
|3|Human3|30|

Parsing
==================================================

1. Parse raw csv string to 2 dimension list (string &rarr; 2d list)  

```cs
var rawCSVData = File.ReadAllText(path);
CSV.Parse(rawCSVData);
```
--------------------------------------------------
2. Parse raw csv string or csv list(2d) to your class list (string / 2d list &rarr; class list(1d))  

```cs
var rawCSVData = File.ReadAllText(path);
CSV.DeserializeToList<T>(rawCSVData);
```

(it return object, so you should cast to List<T>)
(it find field and setter property, 
if some column's type name point readonly or don't have setter properties it may cause bug)

--------------------------------------------------
3. Parse raw csv string or csv list(2d) to dictionary
(string / 2d list &rarr; my class dictionary)

```cs
var rawCSVData = File.ReadAllText(path);
CSV.DeserializeToDictionary<T>(rawCSVData, "SerialNumber", out var keyType);
```

(it also return object, so you should cast to Dictionary<keyType, T>)

--------------------------------------------------
Generating
==================================================
1. CSVFile(In Assets file) - Path type
generate class file by csv format

    1) in unity create ScriptableObject
        create/Loader/Generator/Path
    2) typing path and result's type name
    3) push 'Generate'Button

    $\Rightarrow$ Scripts/AutoCSVOutputScripts/(TypeName).cs file generated
   
--------------------------------------------------
 2. CSVFile(In Assets file) - Asset type
 generate class file by csv format
 
     1) in unity create ScriptableObject
         create/Loader/Generator/File
     2) drag your file and type result's type name
     3) push 'Generate'Button
 
     $\Rightarrow$ 'Scripts/AutoCSVOutputScripts/(TypeName).cs' file generated
    
--------------------------------------------------
3. GoogleSpreadSheet
 generate class file by csv format
 
     1) in unity create ScriptableObject
         create/Loader/Generator/SpreadSheet
     2) type API key(able to get in Google cloud console),
        And spreadSheetPath ("https://docs.google.com/spreadsheets/d/XXX/edit?gid=YYY#gid=ZZZ"'s XXX)
        And PageName
     3) push 'Generate'Button
 
     $\Rightarrow$ 'Scripts/AutoCSVOutputScripts/(TypeName).cs' file generated
   
--------------------------------------------------
     
Generating and Sync Scriptable Object
==================================================

1. CSVFile(In Assets file) - Path type
generate class file by csv format

    1) in unity create ScriptableObject
        create/Loader/Generator/Path
    2) typing path and result's type name
    3) push 'Generate'Button

    $\Rightarrow$ Scripts/AutoCSVOutputScripts/(TypeName).cs file generated
    
--------------------------------------------------
 2. CSVFile(In Assets file) - Asset type
 generate class file by csv format
 
     1) in unity create ScriptableObject
         create/Loader/Generator/File
     2) drag your file and type result's type name
     3) push 'Generate'Button
 
     $\Rightarrow$ 'Scripts/AutoCSVOutputScripts/(TypeName).cs' file generated   

--------------------------------------------------
3. GoogleSpreadSheet
 generate class file by csv format
 
     1) in unity create ScriptableObject
         create/Loader/Generator/SpreadSheet
     2) type API key(able to get in Google cloud console),
        And spreadSheetPath ("https://docs.google.com/spreadsheets/d/XXX/edit?gid=YYY#gid=ZZZ"'s XXX)
        And PageName
     3) push 'Generate'Button
 
     $\Rightarrow$ 'Scripts/AutoCSVOutputScripts/(TypeName).cs' file generated   
     
