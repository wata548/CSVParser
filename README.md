CSVParser
==================================================
This library for Unity.  
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

_!Warnning!  
target class must have empty constructor_


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


CSVParser
==================================================
유니티용 파서입니다.  
CSV를 파싱하고 CSV데이터로 스크립트를 만들고 심지어 스크립터블 오브젝트 또한 지원합니다.

Package
==================================================

[Download](https://drive.google.com/file/d/1WAdqEXo2yCsxft-soXeJg5v-Z4o9AnlM/view?usp=sharing)

--------------------------------------------------

CSV 형식 규칙:  
==================================================
    1행: 필드 / 프로퍼티 이름 줄
    2행: 필드 / 프로퍼티 타입 줄  
    (타입 이름으로 int, float, string은 지원하지 않습니다. Int32, Single, String을 사용하세요 ) 
    3행 이후: 데이터

예시:

|SerialNumber|Name|Age|
|:-:|:------:|:--:|
|Int32|String|Int32|
|1|1Human1|10|
|2|Human2|20|
|3|Human3|30|

Parsing
==================================================

1. CSV 문자열을 2차원 배열로 변환하는 법 (string &rarr; 2d list)  

```cs
var rawCSVData = File.ReadAllText(path);
CSV.Parse(rawCSVData);
```
--------------------------------------------------
2. CSV행 리스트 / CSV 2차원 리스트를 특정 클래스 리스트로 변환 (string / 2d list &rarr; class list(1d))  

_!주의!  
대상 클래스는 무조건 빈 생성자를 소유해야 합니다._


```cs
var rawCSVData = File.ReadAllText(path);
CSV.DeserializeToList<T>(rawCSVData) as List<T>;
```

(object타입으로 리턴하기 때문에 List<T>으로 형변환 시켜주어야합니다.)
(필드나 프로퍼티의 setter를 찾기 때문에, 
열의 대상이 readonly거나 프로퍼티의 setter가 없다면 문제를 일으킵니다.)

--------------------------------------------------
3.  CSV행 리스트 / CSV 2차원 리스트를 dictionary로 변환
(string / 2d list &rarr; my class dictionary)

```cs
var rawCSVData = File.ReadAllText(path);
CSV.DeserializeToDictionary<T>(rawCSVData, "SerialNumber", out var keyType);
```

(이것도 object형을 반환하기 때문에 Dictionary<keyType, T>타입으로 캐스팅 해주어야합니다.)

--------------------------------------------------
Generating
==================================================
1. CSVFile(Assets폴더 내 경로)  
csv 형태로 클래스 생성

    1) 스크립터블 오브젝트를 만듭니다.  
        create/Loader/Generator/Path
    2) 경로와 만들어질 타입명을 적습니다.  
    3) 'Generate'버튼을 누릅니다.  

    $\Rightarrow$ Scripts/AutoCSVOutputScripts/(TypeName).cs file이 생산됩니다.
   
--------------------------------------------------
 2. CSVFile(TextAsset 타입)
 generate class file by csv format
 
     1) 스크립터블 오브젝트를 만듭니다.
         create/Loader/Generator/File
     2) 대상파일을 드래그 후 만들어질 타입명을 작성합니다.
     3) 'Generate'버튼 누릅니다.
 
     $\Rightarrow$ 'Scripts/AutoCSVOutputScripts/(TypeName).cs' file이 생산됩니다.
    
--------------------------------------------------
3. GoogleSpreadSheet
 generate class file by csv format
 
     1) 스크립터블 오브젝트를 만듭니다.  
         create/Loader/Generator/SpreadSheet  
     2) API키를 작성합니다.(Google cloud console에서 공급받을 수 있습니다.),  
        그리고 spreadSheet경로 ("https://docs.google.com/spreadsheets/d/XXX/edit?gid=YYY#gid=ZZZ"의 XXX 입니다.)  
        그리고 spreadSheet의 페이지 명을 작성합니다.  
     3) 'Generate'버튼 누릅니다. 
 
     $\Rightarrow$ 'Scripts/AutoCSVOutputScripts/(TypeName).cs' file이 생산됩니다.
   
--------------------------------------------------
     
Scriptable Object 생산 및 동기화  
==================================================


