---
title: "JSON_MODIFY (Transact-SQL) | Документы Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 06/02/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-json
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 96bc8255-a037-4907-aec4-1a9c30814651
caps.latest.revision: 16
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 70f2c1456da6469c39389fada6a74ccf46383582
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="jsonmodify-transact-sql"></a>JSON_MODIFY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Обновляет значение свойства в строке JSON и возвращает обновленную строку JSON.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
JSON_MODIFY ( expression , path , newValue )  
```  
  
## <a name="arguments"></a>Аргументы  
 *expression*  
 Выражение. Обычно имя переменной или столбца, содержащего текст JSON.  
  
 **JSON_MODIFY** возвращает ошибку, если *выражение* не содержит допустимых данных JSON.  
  
 *путь*  
 Выражения пути JSON, указывающий свойство, для обновления.

 *путь* имеет следующий синтаксис:  
  
 `[append] [ lax | strict ] $.<json path>`  
  
-   *Добавление*  
    Необязательный модификатор, который указывает, что новое значение следует добавить в массив, который ссылается  *\<пути json >*.  
  
-   *нестрогая*  
    Указывает, что свойство ссылается  *\<пути json >* должна существовать. Если свойство не существует, JSON_MODIFY пытается вставить новое значение по указанному пути. Вставки может завершиться ошибкой, если свойство не может быть вставлен на пути. Если не указать *нестрогой* или *strict*, *нестрогой* является режимом по умолчанию.  
  
-   *Strict*  
    Указывает, что свойство ссылается  *\<пути json >* должно быть в выражении JSON. Если свойство не существует, JSON_MODIFY возвращает ошибку.  
  
-   *\<путь JSON >*  
    Указывает путь для свойства для обновления. Дополнительные сведения см. в разделе [выражения пути JSON &#40; SQL Server &#41; ](../../relational-databases/json/json-path-expressions-sql-server.md).  
  
В [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] и [!INCLUDE[ssSDSfull_md](../../includes/sssdsfull-md.md)], можно ввести в качестве значения переменной *путь*.

**JSON_MODIFY** возвращает ошибку, если формат *путь* является недопустимой.  
  
 *новое значение*  
 Новое значение свойства, указанного в *путь*.  
  
 В режиме нестрогой JSON_MODIFY Удаляет указанный ключ, если новое значение имеет значение NULL.  
  
JSON_MODIFY экранирует все специальные символы в новое значение, если тип значения — NVARCHAR или VARCHAR. Текстовое значение не экранированы, если это должным образом в формате JSON, FOR JSON, JSON_QUERY или JSON_MODIFY.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает измененное значение *выражение* как правильно отформатированный текст JSON.  
  
## <a name="remarks"></a>Замечания  
 Функции JSON_MODIFY позволяет обновить значение существующего свойства, вставьте новую пару ключ: значение или удалить ключ на основе сочетания режимов и предоставленных значений.  
  
 В следующей таблице сравниваются поведение **JSON_MODIFY** в нестрогой режиме и в строгом режиме. Дополнительные сведения о спецификации режим дополнительный путь (значениями lax или strict) см. в разделе [выражения пути JSON &#40; SQL Server &#41; ](../../relational-databases/json/json-path-expressions-sql-server.md).  
  
|Существующее значение|Путь существует|Нестрогая режим|Строгий режим|  
|--------------------|-----------------|--------------|-----------------|  
|Не NULL|Да|Обновите существующее значение.|Обновите существующее значение.|  
|Не NULL|Нет|Попробуйте создать новую пару ключ: значение по указанному пути.<br /><br /> Это может произойти сбой. Например, если указать путь `$.user.setting.theme`, JSON_MODIFY не вставляет ключ `theme` Если `$.user` или `$.user.settings` объекты не существуют, или если параметры является массивом или скалярное значение.|Ошибка — INVALID_PROPERTY|  
|NULL|Да|Удаление существующего свойства.|Задайте существующее значение значением NULL.|  
|NULL|Нет|Никаких действий. В результате возвращается первый аргумент.|Ошибка — INVALID_PROPERTY|  
  
 В режиме нестрогой JSON_MODIFY пытается создать новую пару ключ: значение, но в некоторых случаях может возникнуть сбой.  
  
## <a name="examples"></a>Примеры  
  
### <a name="example---basic-operations"></a>Пример. основные операции  
 В следующем примере показано основных операций, которые можно выполнять с помощью текста JSON.  
  
 **Запрос**  
  
```sql  

DECLARE @info NVARCHAR(100)='{"name":"John","skills":["C#","SQL"]}'

PRINT @info

-- Update name  

SET @info=JSON_MODIFY(@info,'$.name','Mike')

PRINT @info

-- Insert surname  

SET @info=JSON_MODIFY(@info,'$.surname','Smith')

PRINT @info

-- Delete name  

SET @info=JSON_MODIFY(@info,'$.name',NULL)

PRINT @info

-- Add skill  

SET @info=JSON_MODIFY(@info,'append $.skills','Azure')

PRINT @info
```  
  
 **Результаты**  
  
```json  
{
    "name": "John",
    "skills": ["C#", "SQL"]
} {
    "name": "Mike",
    "skills": ["C#", "SQL"]
} {
    "name": "Mike",
    "skills": ["C#", "SQL"],
    "surname": "Smith"
} {
    "skills": ["C#", "SQL"],
    "surname": "Smith"
} {
    "skills": ["C#", "SQL", "Azure"],
    "surname": "Smith"
}
```  
  
### <a name="example---multiple-updates"></a>Пример - несколько обновлений  
 JSON_MODIFY позволяет обновить только одно свойство. Если необходимо выполнить несколько обновлений, можно использовать несколько вызовов JSON_MODIFY.  
  
 **Запрос**  
  
```sql  
DECLARE @info NVARCHAR(100)='{"name":"John","skills":["C#","SQL"]}'

PRINT @info

-- Multiple updates  

SET @info=JSON_MODIFY(JSON_MODIFY(JSON_MODIFY(@info,'$.name','Mike'),'$.surname','Smith'),'append $.skills','Azure')

PRINT @info
```  
  
 **Результаты**  
  
```json  
{
    "name": "John",
    "skills": ["C#", "SQL"]
} {
    "name": "Mike",
    "skills": ["C#", "SQL", "Azure"],
    "surname": "Smith"
}
```  
  
### <a name="example---rename-a-key"></a>Пример. Переименование ключа  
 Приведенный ниже показано, как переименовать свойства в тексте JSON с помощью функции JSON_MODIFY. Сначала можно взять значение существующего свойства и вставить его как новую пару ключ: значение. Затем можно удалить старый ключ, задав значение свойства старого значение NULL.  
  
 **Запрос**  
  
```sql  
DECLARE @product NVARCHAR(100)='{"price":49.99}'

PRINT @product

-- Rename property  

SET @product=
 JSON_MODIFY(
  JSON_MODIFY(@product,'$.Price',CAST(JSON_VALUE(@product,'$.price') AS NUMERIC(4,2))),
  '$.price',
  NULL
 )

PRINT @product
```  
  
 **Результаты**  
  
```json  
{
    "price": 49.99
} {
    "Price": 49.99
}
```  
  
 Если не приведение к числовому типу новое значение, JSON_MODIFY воспринимает его как текст и он заключен в двойные кавычки.  
  
### <a name="example---increment-a-value"></a>Пример: приращение значений  
 Следующий пример показывает, как увеличить значение свойства в тексте JSON с помощью функции JSON_MODIFY. Сначала можно взять значение существующего свойства и вставить его как новую пару ключ: значение. Затем можно удалить старый ключ, задав значение свойства старого значение NULL.  
  
 **Запрос**  
  
```sql  
DECLARE @stats NVARCHAR(100)='{"click_count": 173}'

PRINT @stats

-- Increment value  

SET @stats=JSON_MODIFY(@stats,'$.click_count',
 CAST(JSON_VALUE(@stats,'$.click_count') AS INT)+1)

PRINT @stats
```  
  
 **Результаты**  
  
```json  
{
    "click_count": 173
} {
    "click_count": 174
}
```  
  
### <a name="example---modify-a-json-object"></a>Пример. Изменение объекта JSON  
 Рассматривает JSON_MODIFY *newValue* аргумент в виде обычного текста даже в том случае, если он содержит неправильно отформатированный текст JSON. В результате выходные данные JSON, функции, заключен в двойные кавычки, и все специальные символы экранируются, как показано в следующем примере.  
  
 **Запрос**  
  
```sql  
DECLARE @info NVARCHAR(100)='{"name":"John","skills":["C#","SQL"]}'

PRINT @info

-- Update skills array

SET @info=JSON_MODIFY(@info,'$.skills','["C#","T-SQL","Azure"]')

PRINT @info
```  
  
 **Результаты**  
  
```json  
{
    "name": "John",
    "skills": ["C#", "SQL"]
} {
    "name": "John",
    "skills": "["C#","T-SQL","Azure"]"
}
```  
  
 Чтобы избежать автоматического экранирование, предоставляют *newValue* с помощью функции JSON_QUERY. JSON_MODIFY известно, что значение, возвращаемое JSON_MODIFY должным образом в формате JSON, поэтому он не escape-значение.  
  
 **Запрос**  
  
```sql  
DECLARE @info NVARCHAR(100)='{"name":"John","skills":["C#","SQL"]}'

PRINT @info

-- Update skills array  

SET @info=JSON_MODIFY(@info,'$.skills',JSON_QUERY('["C#","T-SQL","Azure"]'))

PRINT @info
```  
  
 **Результаты**  
  
```json  
{
    "name": "John",
    "skills": ["C#", "SQL"]
} {
    "name": "John",
    "skills": ["C#", "T-SQL", "Azure"]
}
```  
  
### <a name="example---update-a-json-column"></a>Пример. обновление столбца JSON  
 В следующем примере обновляется значение свойства в таблице столбец, содержащий JSON.  
  
```sql  
UPDATE Employee
SET jsonCol=JSON_MODIFY(jsonCol,"$.info.address.town",'London')
WHERE EmployeeID=17
 
```  
  
## <a name="see-also"></a>См. также:  
 [Выражения пути JSON &#40; SQL Server &#41;](../../relational-databases/json/json-path-expressions-sql-server.md)   
 [Данные JSON &#40; SQL Server &#41;](../../relational-databases/json/json-data-sql-server.md)  
  
  

