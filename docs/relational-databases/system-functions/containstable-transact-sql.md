---
title: CONTAINSTABLE (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 07/24/2015
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- CONTAINSTABLE
- CONTAINSTABLE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- precise or fuzzy (less precise) matches [full-text search]
- fuzzy (less precise) word or phrase search [full-text search]
- word searches [full-text search]
- weighted values [full-text search]
- values [SQL Server], ranked
- LANGUAGE option
- NEAR option [full-text search]
- RANK column
- phrase searches [full-text search]
- conditions [SQL Server], CONTAINSTABLE
- relevance ranking values [full-text search]
- proximity searches [full-text search]
- CONTAINSTABLE function (Transact-SQL)
- ranked results [full-text search]
- rankings [full-text search]
- less precise (fuzzy) searches [full-text search]
ms.assetid: e580c210-cf57-419d-9544-7f650f2ab814
author: MikeRayMSFT
ms.author: mikeray
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: d1e4af8a90a4f83d8200f02910f3e445b49fca91
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "73983211"
---
# <a name="containstable-transact-sql"></a>CONTAINSTABLE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает пустую таблицу или таблицу из одной или нескольких строк. Столбцы этой таблицы содержат символьные данные, точно или нечетко (менее точно) соответствующие отдельным словам и фразам, расстоянию между словами или взвешенным совпадениям. Функция CONTAINSTABLE используется в [предложении from](../../t-sql/queries/from-transact-sql.md) инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] SELECT и упоминается как обычное имя таблицы. Выполняет полнотекстовый поиск [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] по столбцам полнотекстового индекса, содержащим символьные типы данных.  
  
 Функция CONTAINSTABLE полезна для тех же типов совпадений, что и [предикат CONTAINS](../../t-sql/queries/contains-transact-sql.md) , и использует те же условия поиска, что и Contains.  
  
 В отличие от CONTAINS, запросы с функцией CONTAINSTABLE содержат типизированные полнотекстовые запросы, возвращающие ранжирующие по релевантности значения (RANK) и полнотекстовый ключ (KEY) для каждой строки.  Сведения о формах и полнотекстовом поиске, поддерживаемых в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], см. в разделе [Запрос с полнотекстовым поиском](../../relational-databases/search/query-with-full-text-search.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
CONTAINSTABLE   
( table , { column_name | ( column_list ) | * } , ' <contains_search_condition> '   
     [ , LANGUAGE language_term]   
  [ , top_n_by_rank ]   
)   
  
<contains_search_condition> ::=   
    { <simple_term>   
    | <prefix_term>   
    | <generation_term>   
    | <generic_proximity_term>   
    | <custom_proximity_term>   
    |  <weighted_term>   
    }   
    | { ( <contains_search_condition> )   
    { { AND | & } | { AND NOT | &! } | { OR | | } }   
     <contains_search_condition> [ ...n ]   
    }  
  
<simple_term> ::=   
     { word | "phrase" }  
<prefix term> ::=   
     { "word*" | "phrase*" }   
<generation_term> ::=   
     FORMSOF ( { INFLECTIONAL | THESAURUS } , <simple_term> [ ,...n ] )   
  
<generic_proximity_term> ::=   
     { <simple_term> | <prefix_term> } { { { NEAR | ~ }   
     { <simple_term> | <prefix_term> } } [ ...n ] }  
  
<custom_proximity_term> ::=   
  NEAR (   
     {  
        { <simple_term> | <prefix_term> } [ ,...n ]  
     |  
        ( { <simple_term> | <prefix_term> } [ ,...n ] )   
      [, <maximum_distance> [, <match_order> ] ]  
     }  
       )   
  
      <maximum_distance> ::= { integer | MAX }  
      <match_order> ::= { TRUE | FALSE }   
  
<weighted_term> ::=   
     ISABOUT  
    ( { {   
  <simple_term>   
  | <prefix_term>   
  | <generation_term>   
  | <proximity_term>   
  }   
   [ WEIGHT ( weight_value ) ]   
   } [ ,...n ]   
    )  
  
```  
  
## <a name="arguments"></a>Аргументы  
 *table*  
 Имя таблицы, у которой есть полнотекстовый индекс. *Таблица* может представлять собой одно-, два, три или четыре части имени объекта базы данных. При выполнении запроса к представлению задействуется только базовая таблица с полнотекстовым индексированием.  
  
 *Таблица* не может указывать имя сервера и не может использоваться в запросах к связанным серверам.  
  
 *column_name*  
 Имя одного или нескольких столбцов с полнотекстовым индексом для поиска. Столбцы должны иметь тип **char**, **varchar**, **nchar**, **nvarchar**, **text**, **ntext**, **image**, **xml**, **varbinary** или **varbinary(max)** .  
  
 *column_list*  
 Указывает, что можно задать несколько столбцов, разделенных запятыми. *column_list* должен быть заключен в скобки. Если задан аргумент *language_term*, то у всех столбцов в *column_list* должен быть одинаковый язык.  
  
 \*  
 Указывает, что все столбцы с полнотекстовым индексом в *таблице* должны использоваться для поиска заданного условия поиска. Если не определен аргумент *language_term*, язык для всех столбцов таблицы должен быть одинаковым.  
  
 LANGUAGE *language_term*  
 — Это язык, ресурсы которого будут использоваться для удаления разбиения по словам, извлечения корней, тезауруса и пропускаемых слов (или [стоп-слово](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)) в составе запроса. Этот аргумент не является обязательным и может быть строкой, целым числом или шестнадцатеричным значением, соответствующим идентификатору локали (LCID). Если аргумент *language_term* задан, то соответствующий язык будет применяться ко всем элементам условия поиска. Если значение не указано, то используется язык полнотекстового поиска, заданный для столбца.  
  
 Если в одном столбце хранятся документы на различных языках в виде больших двоичных объектов, то идентификатор локали заданного документа определяет, какой язык должен использоваться для индексирования его содержимого. Указание аргумента *LANGUAGE**language_term* при запросе к такому столбцу может повысить вероятность хорошего соответствия.  
  
 При указании в виде строки *language_term* соответствует значению столбца **Alias** в представлении совместимости [sys. syslanguages](../../relational-databases/system-compatibility-views/sys-syslanguages-transact-sql.md) .  Строка должна быть заключена в одиночные кавычки: '*language_term*'. Если значением аргумента *language_term* является целое число, оно представляет собой действительный код языка. Если значение *language_term* задано в шестнадцатеричной форме, то после символов "0x" должна следовать шестнадцатеричная запись кода языка. Шестнадцатеричное значение не может иметь более восьми знаков, включая начальные нули.  
  
 Если значение находится в формате двухбайтовой кодировки (DBCS), [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] преобразует его в Юникод.  
  
 Если указанный язык является недопустимым или связанные с ним ресурсы не установлены, то [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращает сообщение об ошибке. Для использования нейтральных языковых ресурсов следует указать 0x0 в качестве значения аргумента *language_term*.  
  
 *top_n_by_rank*  
 Указывает, что возвращаются только *n* соответствий с наивысшим рангом в порядке убывания. Применяется только в том случае, если указано целочисленное значение *n*. Если параметр *top_n_by_rank* скомбинирован с другими параметрами, то запрос может вернуть меньше строк, чем фактически соответствует всем предикатам. *top_n_by_rank* позволяет повысить производительность запросов, вызвав только наиболее актуальные попадания.  
  
 <contains_search_condition>  
 Текст, который необходимо найти в столбце *column_name*, и условия соответствия. Дополнительные сведения об условиях поиска см. в разделе [CONTAINS &#40;&#41;Transact-SQL ](../../t-sql/queries/contains-transact-sql.md).  
  
## <a name="remarks"></a>Remarks  
 Полнотекстовые предикаты и функции работают в одной таблице, что следует из наличия предиката FROM. Для поиска в нескольких таблицах используйте в предложении FROM соединенную таблицу, чтобы выполнять поиск в результирующем наборе, который получен в результате соединения нескольких таблиц.  
  
 Возвращаемая таблица содержит столбец с именем **Key** , содержащий значения полнотекстовых ключей. Каждая таблица с полнотекстовым индексом содержит столбец, значения которого гарантированно уникальны, а значения, возвращаемые в **ключевом** столбце, являются значениями полнотекстового ключа строк, соответствующих условию выбора, указанному в условии поиска CONTAINS. Свойство **TableFulltextKeyColumn** , полученное из функции OBJECTPROPERTYEX, предоставляет идентификатор этого уникального ключевого столбца. Чтобы получить идентификатор столбца, связанного с полнотекстовым ключом полнотекстового индекса, используйте представление **sys. fulltext_indexes**. Дополнительные сведения см. в разделе [sys. fulltext_indexes &#40;&#41;Transact-SQL ](../../relational-databases/system-catalog-views/sys-fulltext-indexes-transact-sql.md).  
  
 Чтобы получить нужные строки первоначальной таблицы, следует указать соединение со строками, возвращаемыми функцией CONTAINSTABLE. Обычно используется следующая форма инструкции SELECT с предложением FROM и функцией CONTAINSTABLE:  
  
```  
SELECT select_list  
FROM table AS FT_TBL INNER JOIN  
   CONTAINSTABLE(table, column, contains_search_condition) AS KEY_TBL  
   ON FT_TBL.unique_key_column = KEY_TBL.[KEY];  
```  
  
 Таблица, созданная функцией CONTAINSTABLE, включает столбец с именем **Rank**. Столбец **Rank** — это значение (от 0 до 1000) для каждой строки, показывающее, насколько хорошо строка соответствует критериям выбора. Это значение обычно используется в инструкции SELECT следующим образом.  
  
-   В предложении ORDER BY для упорядочивания строк таблицы по рангу.  
  
-   В списке выборки для определения ранжирующего значения каждой строки.  
  
## <a name="permissions"></a>Разрешения  
 Функцию могут выполнять только пользователи, обладающие правами доступа SELECT к соответствующей таблице или столбцам, к которым обращается функция.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-simple-example"></a>A. Простой пример  
 В следующем примере создается и заполняется простая таблица из двух столбцов, перечислены 3 подсчета и цвета в их флагах. Он создает и заполняет полнотекстовый каталог и индекс для таблицы. Затем демонстрируется синтаксис **CONTAINSTABLE** . В этом примере показано, как значение ранжирования увеличивается выше, когда искомое значение встречается несколько раз. В последнем запросе Танзания, который содержит как зеленый, так и черный, имеет более высокий ранг, чем Италия, который содержит только один из запрашиваемых цветов.  
  
```  
CREATE TABLE Flags (Country nvarchar(30) NOT NULL, FlagColors varchar(200));  
CREATE UNIQUE CLUSTERED INDEX FlagKey ON Flags(Country);  
INSERT Flags VALUES ('France', 'Blue and White and Red');  
INSERT Flags VALUES ('Italy', 'Green and White and Red');  
INSERT Flags VALUES ('Tanzania', 'Green and Yellow and Black and Yellow and Blue');  
SELECT * FROM Flags;  
GO  
  
CREATE FULLTEXT CATALOG TestFTCat;  
CREATE FULLTEXT INDEX ON Flags(FlagColors) KEY INDEX FlagKey ON TestFTCat;  
GO   
  
SELECT * FROM Flags;  
SELECT * FROM CONTAINSTABLE (Flags, FlagColors, 'Green') ORDER BY RANK DESC;  
SELECT * FROM CONTAINSTABLE (Flags, FlagColors, 'Green or Black') ORDER BY RANK DESC;  
```  
  
### <a name="b-returning-rank-values"></a>Б) Получение значений ранга  
 В следующем примере выполняется поиск всех названий продуктов, содержащих слова «frame», «wheel» или «tire», при этом для каждого слова задается определенный вес. Для каждой строки набора результатов, удовлетворяющей условию поиска, отображается относительная «близость» к совпадению (ранг). Кроме того, строки с более высоким рангом возвращаются первыми.  
  
```  
USE AdventureWorks2012;  
GO  
  
SELECT FT_TBL.Name, KEY_TBL.RANK  
    FROM Production.Product AS FT_TBL   
        INNER JOIN CONTAINSTABLE(Production.Product, Name,   
        'ISABOUT (frame WEIGHT (.8),   
        wheel WEIGHT (.4), tire WEIGHT (.2) )' ) AS KEY_TBL  
            ON FT_TBL.ProductID = KEY_TBL.[KEY]  
ORDER BY KEY_TBL.RANK DESC;  
GO  
```  
  
### <a name="c-returning-rank-values-greater-than-a-specified-value"></a>В. Получение значений ранга, превышающих указанное значение  
  
||  
|-|  
|**Область применения**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] и более поздних версий.|  
  
 В следующем примере используется оператор NEAR для поиска «`bracket`» и «`reflector`», находящихся близко друг от друга в столбце таблицы `Production.Document`. Возвращаются только ранжирующие строки от 50 и выше.  
  
```  
USE AdventureWorks2012  
GO  
  
SELECT DocumentNode, Title, DocumentSummary  
FROM Production.Document AS DocTable   
INNER JOIN CONTAINSTABLE(Production.Document, Document,  
  'NEAR(bracket, reflector)' ) AS KEY_TBL  
  ON DocTable.DocumentNode = KEY_TBL.[KEY]  
WHERE KEY_TBL.RANK > 50  
ORDER BY KEY_TBL.RANK DESC;  
GO  
```  
  
> [!NOTE]  
>  Если в полнотекстовом запросе не указывается целочисленное максимальное расстояние, то документ, содержащий лишь попадания с расстояниями, большими 100 логических выражений, не будет отвечать требованиям NEAR и получит ранг 0.  
  
### <a name="d-returning-top-5-ranked-results-using-top_n_by_rank"></a>Г. Получение 5 строк с максимальным рангом с помощью функции top_n_by_rank  
 В следующем примере возвращается описание первых 5 товаров, где столбец `Description` содержит слово «aluminum» рядом со словом «light» или «lightweight».  
  
```  
USE AdventureWorks2012;  
GO  
  
SELECT FT_TBL.ProductDescriptionID,  
   FT_TBL.Description,   
   KEY_TBL.RANK  
FROM Production.ProductDescription AS FT_TBL INNER JOIN  
   CONTAINSTABLE (Production.ProductDescription,  
      Description,   
      '(light NEAR aluminum) OR  
      (lightweight NEAR aluminum)',  
      5  
   ) AS KEY_TBL  
   ON FT_TBL.ProductDescriptionID = KEY_TBL.[KEY];  
GO  
```  
  
 `GO`  
  
### <a name="e-specifying-the-language-argument"></a>Д. Указание аргумента LANGUAGE  
 Следующий пример демонстрирует использование аргумента `LANGUAGE`.  
  
```  
USE AdventureWorks2012;  
GO  
  
SELECT FT_TBL.ProductDescriptionID,  
   FT_TBL.Description,   
   KEY_TBL.RANK  
FROM Production.ProductDescription AS FT_TBL INNER JOIN  
   CONTAINSTABLE (Production.ProductDescription,  
      Description,   
      '(light NEAR aluminum) OR  
      (lightweight NEAR aluminum)',  
      LANGUAGE N'English',  
      5  
   ) AS KEY_TBL  
   ON FT_TBL.ProductDescriptionID = KEY_TBL.[KEY];  
GO  
```  
  
> [!NOTE]  
>  Аргумент LANGUAGE *language_term* не требуется для использования *top_n_by_rank.*  
  
## <a name="see-also"></a>См. также:  
 [Ограничение результатов поиска по РАНГу](../../relational-databases/search/limit-search-results-with-rank.md)   
 [Запрос с полнотекстовым поиском](../../relational-databases/search/query-with-full-text-search.md)   
 [Создание запросов полнотекстового поиска (визуальные инструменты для баз данных)](https://msdn.microsoft.com/library/537fa556-390e-4c88-9b8e-679848d94abc)   
 [СОДЕРЖИТ &#40;&#41;Transact-SQL](../../t-sql/queries/contains-transact-sql.md)   
 [Запрос с полнотекстовым поиском](../../relational-databases/search/query-with-full-text-search.md)   
 [SELECT (Transact-SQL)](../../t-sql/queries/select-transact-sql.md)   
 [FROM (Transact-SQL)](../../t-sql/queries/from-transact-sql.md)  
  
  
