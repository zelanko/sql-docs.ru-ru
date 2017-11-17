---
title: "НАПРИМЕР (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ESCAPE
- LIKE
- ESCAPE_TSQL
- LIKE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ESCAPE keyword
- '% (wildcard - character(s) to match)'
- ASCII pattern matching
- pattern searching [SQL Server]
- wildcard characters [SQL Server]
- literals [SQL Server], using wildcards
- character strings [SQL Server], LIKE
- exact matches [SQL Server]
- Boolean functions
- LIKE comparisons
- matching patterns [SQL Server]
- NOT LIKE keyword
ms.assetid: 581fb289-29f9-412b-869c-18d33a9e93d5
caps.latest.revision: 50
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: aecf422ca2289b2a417147eb402921bb8530d969
ms.openlocfilehash: 07a8bb8b08120f08cd54e42dcd332459544c206d
ms.contentlocale: ru-ru
ms.lasthandoff: 10/24/2017

---
# <a name="like-transact-sql"></a>LIKE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Определяет, совпадает ли указанная символьная строка с заданным шаблоном. Шаблон может включать обычные символы и символы-шаблоны. Во время сравнения с шаблоном необходимо, чтобы его обычные символы в точности совпадали с символами, указанными в строке. Символы-шаблоны могут совпадать с произвольными элементами символьной строки. Использование символов-шаблонов в отличие от использования операторов сравнения строки (= и !=) делает оператор LIKE более гибким. Если тип данных одного из аргументов не является символьной строкой, компонент [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], если это возможно, преобразует его в тип данных символьной строки.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
match_expression [ NOT ] LIKE pattern [ ESCAPE escape_character ]  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
match_expression [ NOT ] LIKE pattern  
```  
  
## <a name="arguments"></a>Аргументы  
 *match_expression*  
 Любое допустимое [выражение](../../t-sql/language-elements/expressions-transact-sql.md) символьного типа данных.  
  
 *шаблон*  
 Конкретная строка символов для поиска в *match_expression*и могут включать следующие допустимые символы-шаблоны. *шаблон* не может превышать 8 000 байт.  
  
|Символ-шаблон|Description|Пример|  
|------------------------|-----------------|-------------|  
|%|Любая строка, содержащая ноль или более символов.|Инструкция WHERE Название LIKE '%компьютер%' выполняет поиск и выдает все названия книг, содержащие слово «компьютер».|  
|_ (подчеркивание)|Любой одиночный символ.|Инструкция WHERE фамилия_автора LIKE '_етров' выполняет поиск и выдает все имена, состоящие из шести букв и заканчивающиеся сочетанием «етров» (Петров, Ветров и т.п.).|  
|[ ]|Любой одиночный символ, содержащийся в диапазоне ([a-f]) или наборе ([abcdef]).|Инструкция WHERE Фамилия_автора LIKE '[Л-С]омов' выполняет поиск и выдает все фамилии авторов, заканчивающиеся на «омов» и начинающиеся на любую букву в промежутке от «Л» до «С», например Ломов, Ромов, Сомов и т.п. При выполнении операции поиска в диапазоне символы, включенные в диапазон, могут изменяться в зависимости от правил сортировки параметров сортировки.|  
|[^]|Любой одиночный символ, не содержащийся в  диапазоне ([^a-f]) или наборе ([^abcdef]).|Инструкция WHERE Фамилия_автора LIKE 'ив[^а]%' выполняет поиск и выдает все фамилии, начинающиеся на «ив», в которых третья буква отличается от «а».|  
  
 *escape_character*  
 Символ, помещаемый перед символом-шаблоном, чтобы символ-шаблон рассматривался как обычный символ, а не как шаблон. *escape_character* символьное выражение, нет значения по умолчанию и возвращающим результат в виде одного символа.  
  
## <a name="result-types"></a>Типы результата  
 **Логическое значение**  
  
## <a name="result-value"></a>Значение результата  
 КАК и возвращает TRUE, если *match_expression* соответствует указанному *шаблон*.  
  
## <a name="remarks"></a>Замечания  
 При использовании оператора LIKE для сравнения строк во внимание принимаются все символы строки-шаблона. Это касается начальных и конечных пробелов (« »). Если операция сравнения в запросе должна вернуть все строки, содержащие строки LIKE 'абв ' (с символом пробела на конце), то строка, содержащая «абв» (без пробела), не будет возвращена. Однако завершающие пробелы в выражении, с которым сравнивается шаблон, не учитываются. Если операция сравнения в запросе должна вернуть все строки, содержащие строки LIKE 'абв' (без знака пробела на конце), то будут возвращены все строки, содержащие «абв», как с завершающими пробелами, так и без них.  
  
 Сравнение строк, используя шаблон, который содержит **char** и **varchar** данных не может передать из-за хранение данных использования оператора LIKE. Необходимо знать методы хранения каждого типа данных, чтобы избежать некорректного использования оператора LIKE. В следующем примере передается локальный **char** переменной в хранимую процедуру и использует сопоставление шаблонов для поиска всех сотрудников, чьи фамилии начинаются с указанного набора символов.  
  
```tsql
-- Uses AdventureWorks  
  
CREATE PROCEDURE FindEmployee @EmpLName char(20)  
AS  
SELECT @EmpLName = RTRIM(@EmpLName) + '%';  
SELECT p.FirstName, p.LastName, a.City  
FROM Person.Person p JOIN Person.Address a ON p.BusinessEntityID = a.AddressID  
WHERE p.LastName LIKE @EmpLName;  
GO  
EXEC FindEmployee @EmpLName = 'Barb';  
GO  
```  
  
 В `FindEmployee` процедуры, строки не возвращаются, поскольку **char** переменной (`@EmpLName`) содержит конечные пробелы, каждый раз, когда имя содержит не более 20 символов. Поскольку `LastName` столбец **varchar**, существуют не конечные пробелы. Данная процедура завершается неудачей, так как завершающие пробелы учитываются.  
  
 Однако следующий пример завершается успешно, поскольку конечные пробелы не добавляются в **varchar** переменной.  
  
```tsql
-- Uses AdventureWorks  
  
CREATE PROCEDURE FindEmployee @EmpLName varchar(20)  
AS  
SELECT @EmpLName = RTRIM(@EmpLName) + '%';  
SELECT p.FirstName, p.LastName, a.City  
FROM Person.Person p JOIN Person.Address a ON p.BusinessEntityID = a.AddressID  
WHERE p.LastName LIKE @EmpLName;  
GO  
EXEC FindEmployee @EmpLName = 'Barb';  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 FirstName      LastName            City
 ----------     -------------------- --------------- 
 Angela         Barbariol            Snohomish
 David          Barber               Snohomish
 (2 row(s) affected)  
 ``` 
 
## <a name="pattern-matching-by-using-like"></a>Совпадение с шаблоном с использованием оператора LIKE  
 Оператор LIKE поддерживает шаблоны в ASCII и Юникоде. Если все аргументы (*match_expression*, *шаблон*, и *escape_character*, если он существует) — символьный тип ASCII, шаблон ASCII. В случае, когда какой-либо из аргументов имеет тип данных Юникод, выполняется преобразование всех аргументов в Юникод и применяется шаблон Юникод. При использовании данных в Юникоде (**nchar** или **nvarchar** типов данных) с помощью оператора LIKE учитываются завершающие пробелы; Однако для данных не в Юникоде, завершающие пробелы не учитываются. Работа оператора LIKE с данными в Юникоде совместима со стандартом ISO. Принцип работы оператора LIKE с данными ASCII совместим с более ранними версиями [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Приведенные ниже примеры поясняют различия между результатами сравнения данных с шаблонами оператора LIKE, представленными в Юникоде и ASCII.  
  
```tsql  
-- ASCII pattern matching with char column  
CREATE TABLE t (col1 char(30));  
INSERT INTO t VALUES ('Robert King');  
SELECT *   
FROM t   
WHERE col1 LIKE '% King';   -- returns 1 row  
  
-- Unicode pattern matching with nchar column  
CREATE TABLE t (col1 nchar(30));  
INSERT INTO t VALUES ('Robert King');  
SELECT *   
FROM t   
WHERE col1 LIKE '% King';   -- no rows returned  
  
-- Unicode pattern matching with nchar column and RTRIM  
CREATE TABLE t (col1 nchar (30));  
INSERT INTO t VALUES ('Robert King');  
SELECT *   
FROM t   
WHERE RTRIM(col1) LIKE '% King';   -- returns 1 row  
```  
  
> [!NOTE]  
>  Операции сравнения с помощью оператора LIKE зависят от параметров сортировки. Дополнительные сведения см. в разделе [COLLATE (Transact-SQL)](~/t-sql/statements/collations.md).  
  
## <a name="using-the--wildcard-character"></a>Использование символа-шаблона «%»  
 Если в операторе LIKE указать символ '5%', то компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] будет искать число «5», за которым следует любая строка с числом символов от нуля и больше.  
  
 Например, при выполнении следующего примера отображаются все динамические административные представления базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)], так как все они начинаются символами `dm`.  
  
```tsql  
-- Uses AdventureWorks  
  
SELECT Name  
FROM sys.system_views  
WHERE Name LIKE 'dm%';  
GO  
```  
  
 Чтобы отобразить все объекты, не являющиеся динамическими административными представлениями, используется синтаксис `NOT LIKE 'dm%'`. Например, если всего имеется 32 объекта и оператор LIKE выдает 13 наименований, совпадающих с шаблоном, то оператор NOT LIKE возвращает 19 объектов, не соответствующих указанному в операторе LIKE шаблону.  
  
 По такому шаблону, как `LIKE '[^d][^m]%'`, не всегда будут возвращаться одни и те же имена. Вместо 19 имен можно найти только 14, так как имена, которые начинаются с буквы `d` или у которых второй буквой является `m`, будут исключены из результата, как и имена динамических административных представлений. Причиной этому является поэтапный поиск отрицательных символов-шаблонов: за один шаг обрабатывается один символ-шаблон. Процесс поиска совпадений прекращается при возникновении сбоя на любой стадии выполнения.  
  
## <a name="using-wildcard-characters-as-literals"></a>Использование символов-шаблонов в качестве литералов  
 Символы-шаблоны могут быть использованы в качестве литералов. Чтобы использовать символ-шаблон в качестве литерала, его необходимо заключать в скобки. В следующей таблице представлены несколько примеров применения ключевого слова LIKE вместе с символами-шаблонами [ ].  
  
|Символ|Значение|  
|------------|-------------|  
|LIKE '5[%]'|5%|  
|LIKE '[_]n'|_N|  
|LIKE '[a-cdf]'|a, b, c, d или f|  
|LIKE '[-acdf]'|-, a, b, c, d или f|  
|LIKE '[ [ ]'|[|  
|LIKE ']'|]|  
|LIKE 'abc[_]d%'|abc_d и abc_de|  
|LIKE 'abc[def]'|abcd, abce и abcf|  
  
## <a name="pattern-matching-with-the-escape-clause"></a>Совпадение с шаблоном с помощью предложения ESCAPE  
 Можно искать символьные строки, в состав которых входит один или более специальных символов-шаблонов. Например, таблица discounts базы данных customers может содержать значения скидок, включающих знак процента (%). Чтобы выполнить поиск знака процента в качестве символа-шаблона, необходимо ввести ключевое слово ESCAPE и escape-символ. Например, образец базы данных содержит столбец с именем comment, в котором хранится значение «30%». Чтобы найти строки, содержащие последовательность символов «30%» в столбце comment, необходимо указать предложение WHERE, например `WHERE comment LIKE '%30!%%' ESCAPE '!'`. Если предложение ESCAPE и escape-символ не указаны, компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] вернет все строки, содержащие последовательность символов «30».  
  
 Если в шаблоне LIKE после escape-символа нет никакого символа, то шаблон является недопустимым и оператор LIKE возвращает значение FALSE. Если символ после escape-символа не является символом-шаблоном, то escape-символ игнорируется, а этот символ рассматривается как обычный символ в шаблоне. Это относится к таким символам-шаблонам, как подчеркивание (_), процент (%) и левая квадратная скобка ([), в том случае, если они заключены в квадратные скобки. Также в квадратных скобках ([ ]) и при использовании escape-символов можно использовать такие символы, как знак вставки (^), дефис (-) и правая квадратная скобка (]).  
  
 0x0000 (**char(0)**) имеет неопределенный символ в параметрах сортировки Windows и не может включать в LIKE.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-like-with-the--wildcard-character"></a>A. Применение оператора LIKE с символом-шаблоном %  
 В следующем примере в таблице `415` выполняется поиск всех телефонных номеров с кодом города `PersonPhone`.  
  
```tsql  
-- Uses AdventureWorks  
  
SELECT p.FirstName, p.LastName, ph.PhoneNumber  
FROM Person.PersonPhone AS ph  
INNER JOIN Person.Person AS p  
ON ph.BusinessEntityID = p.BusinessEntityID  
WHERE ph.PhoneNumber LIKE '415%'  
ORDER by p.LastName;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
 
 ```
 FirstName             LastName             Phone
 -----------------     -------------------  ------------
 Ruben                 Alonso               415-555-124  
 Shelby                Cook                 415-555-0121  
 Karen                 Hu                   415-555-0114  
 John                  Long                 415-555-0147  
 David                 Long                 415-555-0123  
 Gilbert               Ma                   415-555-0138  
 Meredith              Moreno               415-555-0131  
 Alexandra             Nelson               415-555-0174  
 Taylor                Patterson            415-555-0170  
 Gabrielle              Russell             415-555-0197  
 Dalton                 Simmons             415-555-0115  
 (11 row(s) affected)  
 ``` 
 
### <a name="b-using-not-like-with-the--wildcard-character"></a>Б. Применение оператора NOT LIKE с символом-шаблоном %  
 В следующем примере в таблице `PersonPhone` выполняется поиск всех телефонных номеров с региональным кодом, отличным от `415`.  
  
```tsql  
-- Uses AdventureWorks  
  
SELECT p.FirstName, p.LastName, ph.PhoneNumber  
FROM Person.PersonPhone AS ph  
INNER JOIN Person.Person AS p  
ON ph.BusinessEntityID = p.BusinessEntityID  
WHERE ph.PhoneNumber NOT LIKE '415%' AND p.FirstName = 'Gail'  
ORDER BY p.LastName;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
 
 ```
FirstName              LastName            Phone
---------------------- -------------------- -------------------
Gail                  Alexander            1 (11) 500 555-0120  
Gail                  Butler               1 (11) 500 555-0191  
Gail                  Erickson             834-555-0132  
Gail                  Erickson             849-555-0139  
Gail                  Griffin              450-555-0171  
Gail                  Moore                155-555-0169  
Gail                  Russell              334-555-0170  
Gail                  Westover             305-555-0100  
(8 row(s) affected)  
```  

### <a name="c-using-the-escape-clause"></a>В. Применение предложения ESCAPE  
 В следующем примере предложение `ESCAPE` и escape-символ используются для поиска символьной строки `10-15%` в столбце `c1` таблицы `mytbl2`.  
  
```tsql
USE tempdb;  
GO  
IF EXISTS(SELECT TABLE_NAME FROM INFORMATION_SCHEMA.TABLES  
      WHERE TABLE_NAME = 'mytbl2')  
   DROP TABLE mytbl2;  
GO  
USE tempdb;  
GO  
CREATE TABLE mytbl2  
(  
 c1 sysname  
);  
GO  
INSERT mytbl2 VALUES ('Discount is 10-15% off'), ('Discount is .10-.15 off');  
GO  
SELECT c1   
FROM mytbl2  
WHERE c1 LIKE '%10-15!% off%' ESCAPE '!';  
GO  
```  
  
### <a name="d-using-the---wildcard-characters"></a>Г. Использование символов-шаблонов [ ]  
 В следующем примере вычисляется сотрудников на `Person` таблицу с имя `Cheryl` или `Sheryl`.  
  
```tsql  
-- Uses AdventureWorks  
  
SELECT BusinessEntityID, FirstName, LastName   
FROM Person.Person   
WHERE FirstName LIKE '[CS]heryl';  
GO  
```  
  
 В следующем примере выполняется поиск строк в таблице `Person` для сотрудников с фамилией `Zheng` или `Zhang`.  
  
```tsql  
-- Uses AdventureWorks  
  
SELECT LastName, FirstName  
FROM Person.Person  
WHERE LastName LIKE 'Zh[ae]ng'  
ORDER BY LastName ASC, FirstName ASC;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="e-using-like-with-the--wildcard-character"></a>Д. Применение оператора LIKE с символом-шаблоном %  
 В следующем примере вычисляется всех сотрудников в `DimEmployee` таблицы с помощью телефонных номеров, запускаемые с `612`.  
  
```tsql  
-- Uses AdventureWorks  
  
SELECT FirstName, LastName, Phone  
FROM DimEmployee  
WHERE phone LIKE '612%'  
ORDER by LastName;  
```  
  
### <a name="f-using-not-like-with-the--wildcard-character"></a>Е. Применение оператора NOT LIKE с символом-шаблоном %  
 Следующий пример выполняется поиск всех телефонных номеров в `DimEmployee` таблицу, не ставьте `612`.  .  
  
```tsql  
-- Uses AdventureWorks  
  
SELECT FirstName, LastName, Phone  
FROM DimEmployee  
WHERE phone NOT LIKE '612%'  
ORDER by LastName;  
```  
  
### <a name="g-using-like-with-the--wildcard-character"></a>Ж. Применение оператора LIKE с символом-шаблоном _  
 Следующий пример выполняет поиск всех телефонных номеров с кодом города, начиная с `6` и заканчиваются `2` в `DimEmployee` таблицы. Обратите внимание, что символом-шаблоном % также в конце шаблона поиска, так как код города — первая часть номера телефона и существуют дополнительные символы после значения столбца.  
  
```tsql  
-- Uses AdventureWorks  
  
SELECT FirstName, LastName, Phone  
FROM DimEmployee  
WHERE phone LIKE '6_2%'  
ORDER by LastName;   
```  
  
## <a name="see-also"></a>См. также:  
 [Выражения &#40; Transact-SQL &#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [Встроенные функции (Transact-SQL)](~/t-sql/functions/functions.md)   
 [SELECT (Transact-SQL)](../../t-sql/queries/select-transact-sql.md)   
 [ГДЕ &#40; Transact-SQL &#41;](../../t-sql/queries/where-transact-sql.md)  
 

