---
title: "FREETEXTTABLE (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- FREETEXTTABLE_TSQL
- FREETEXTTABLE
dev_langs: TSQL
helpviewer_keywords:
- search conditions [SQL Server], meaning matches
- meaning matches [full-text search]
- FREETEXTTABLE function (Transact-SQL)
- ranked results [full-text search]
- column searches [full-text search]
ms.assetid: 4523ae15-4260-40a7-a53c-8df15e1fee79
caps.latest.revision: "51"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 32d2f6ab0ec5faf5603504824ec6917f0297ef72
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="freetexttable-transact-sql"></a>FREETEXTTABLE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Функция, используемая в [предложение FROM](../../t-sql/queries/from-transact-sql.md) из [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкции SELECT для выполнения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] полнотекстового поиска в полнотекстовых индексированных столбцах, содержащим типы символьных данных. Эта функция возвращает таблицу из нуля, одной или нескольких строк и столбцов содержат значения, совпадающие по смыслу, а не только дословно, с текстом, указанным в *freetext_string*. Ссылки на функцию FREETEXTTABLE указываются так, как если бы это было имя обычной таблицы.  
  
 Функция FREETEXTTABLE полезна для тех же видов совпадений, что [FREETEXT &#40; Transact-SQL &#41; ](../../t-sql/queries/freetext-transact-sql.md),  
  
 Запросы, использующие функцию FREETEXTTABLE, возвращают ранжирующие по релевантности значения (RANK) и полнотекстовый ключ (KEY) для каждой строки.  
  
> [!NOTE]  
>  Дополнительные сведения о формах и полнотекстовом поиске, поддерживаемых [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], в разделе [запрос с Full-Text Search](../../relational-databases/search/query-with-full-text-search.md).  
  
(http://azure.microsoft.com/documentation/articles/sql-database-preview-whats-new/?WT.mc_id=TSQL_GetItTag)). |  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
FREETEXTTABLE (table , { column_name | (column_list) | * }   
          , 'freetext_string'   
     [ , LANGUAGE language_term ]   
     [ , top_n_by_rank ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *table*  
 Имя таблицы, помеченной как допускающая полнотекстовые запросы. *Таблица* или *представление*может быть одно-, двух- или имя объекта базы данных трех частей. При выполнении запроса к представлению задействуется только базовая таблица с полнотекстовым индексированием.  
  
 *Таблица* нельзя указывать имя сервера и не может использоваться в запросах к связанным серверам.  
  
 *column_name*  
 Имя одного или нескольких столбцов с полнотекстовой индексацией в таблице, указанной в предложении FROM. Столбцы могут иметь тип **char**, **varchar**, **nchar**, **nvarchar**, **текст**, **ntext**, **изображения**, **xml**, **varbinary**, или **varbinary(max)**.  
  
 *column_list*  
 Указывает, что можно задать несколько столбцов, разделенных запятыми. *column_list* должен быть заключен в круглые скобки. Если не *language_term* указано, язык всех столбцов *column_list* должны быть одинаковыми.  
  
 \*  
 Указывает, что все столбцы, которые были зарегистрированы для полнотекстового поиска следует использовать для поиска заданного *freetext_string*. Если не *language_term* указан, язык всех полнотекстовых индексированных столбцов в таблице должны быть одинаковыми.  
  
 *freetext_string*  
 Текст для поиска в *column_name*. Допустимо вводить любой текст, включая слова, фразы или предложения. Соответствия формируются, если любой ключ или его формы найдены в полнотекстовом индексе.  
  
 В отличие от поиска CONTAINS условием, где слово AND является ключевым, при использовании в *freetext_string* слова «и» считается пропускаемым словом или [стоп-слово](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)и будут потеряны.  
  
 Использование функций WEIGHT, FORMSOF, символов шаблонов, NEAR, а также других синтаксических элементов запрещено. *freetext_string* wordbroken и пропускается через тезаурус.  
  
 Язык *language_term*  
 Язык, ресурсы которого будут использованы для разбиения по словам, выделения корня, проверки по тезаурусу и удаления стоп-слов в составе запроса. Этот аргумент не является обязательным и может быть строкой, целым числом или шестнадцатеричным значением, соответствующим идентификатору локали (LCID). Если *language_term* указан, то соответствующий язык будет применяться ко всем элементам условия поиска. Если значение не указано, то используется язык полнотекстового поиска, заданный для столбца.  
  
 Если в одном столбце хранятся документы на различных языках в виде больших двоичных объектов, то идентификатор локали заданного документа определяет, какой язык должен использоваться для индексирования его содержимого. При запросе такой столбец, указав *язык**language_term* может повысить вероятность хорошего соответствия.  
  
 Если указан как строка, *language_term* соответствует **псевдоним** значение столбца в [sys.syslanguages &#40; Transact-SQL &#41; ](../../relational-databases/system-compatibility-views/sys-syslanguages-transact-sql.md) Просмотр в режиме совместимости.  Строка должна быть заключена в одинарные кавычки, например "*language_term*". Если указано как целое число, *language_term* фактический код, определяющий язык. Если указан как шестнадцатеричное значение *language_term* 0 x следуют шестнадцатеричное значение кода языка. Шестнадцатеричное значение не может иметь более восьми знаков, включая начальные нули.  
  
 Если значение указано в формате двухбайтовой кодировки (DBCS), [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] преобразует его в Юникод.  
  
 Если указанный язык является недопустимым или связанные с ним ресурсы не установлены, то [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращает сообщение об ошибке. Для использования нейтральных языковых ресурсов укажите 0x0 как *language_term*.  
  
 *top_n_by_rank*  
 Указывает, что только  *n* возвращаются первых ранжированных совпадений, в порядке убывания. Применяется только тогда, когда целочисленные значения,  *n* , указан. Если параметр *top_n_by_rank* скомбинирован с другими параметрами, то запрос может вернуть меньше строк, чем фактически соответствует всем предикатам. *top_n_by_rank* позволяет повысить производительность запросов, выбирать только наиболее важные попадания.  
  
## <a name="remarks"></a>Замечания  
 Полнотекстовые предикаты и функции работают в одной таблице, что следует из наличия предиката FROM. Для поиска в нескольких таблицах используйте в предложении FROM соединенную таблицу, чтобы выполнять поиск в результирующем наборе, который получен в результате соединения нескольких таблиц.  
  
 Функция FREETEXTTABLE использует те же условия поиска, что и предикат FREETEXT.  
  
 Подобно функции CONTAINSTABLE, возвращаемая таблица содержит столбцы с именами **ключ** и **ранг**, которые ссылаются запросы для получения соответствующих строк и использования значения ранжирования строк.  
  
## <a name="permissions"></a>Permissions  
 Функция FREETEXTTABLE может быть задействована только пользователями с соответствующими правами доступа SELECT на указанную таблицу или ее ссылаемые столбцы.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-simple-example"></a>A. Простой пример  
 Следующий пример создает и заполняет простую таблицу из двух столбцов, список 3 округа и цветов в флагов. ИТ-создает и заполняет полнотекстового каталога и индекса в таблице. Затем **FREETEXTTABLE** демонстрируется синтаксис.  
  
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
SELECT * FROM FREETEXTTABLE (Flags, FlagColors, 'Blue');  
SELECT * FROM FREETEXTTABLE (Flags, FlagColors, 'Yellow');  
```  
  
### <a name="b-using-freetext-in-an-inner-join"></a>Б. Использование функции FREETEXT в INNER JOIN  
 В следующем примере возвращаются имя и описание всех категорий, связанных с `sweet`, `candy`, `bread`, `dry` или `meat`.  
  
```  
USE AdventureWorks2012;  
GO  
  
SELECT FT_TBL.Description  
    ,KEY_TBL.RANK  
FROM Production.ProductDescription AS FT_TBL   
    INNER JOIN FREETEXTTABLE(Production.ProductDescription,  
    Description,   
    'high level of performance') AS KEY_TBL  
ON FT_TBL.ProductDescriptionID = KEY_TBL.[KEY]  
ORDER BY RANK DESC;  
GO  
```  
  
### <a name="c-specifying-language-and-highest-ranked-matches"></a>В. Указание языка и соответствий с наивысшими ранжирующими значениями  
 В следующем примере идентичны и показано, как использовать `LANGUAGE` *language_term* и *top_n_by_rank* параметров.  
  
```  
USE AdventureWorks2012;  
GO  
  
SELECT FT_TBL.Description  
    ,KEY_TBL.RANK  
FROM Production.ProductDescription AS FT_TBL   
    INNER JOIN FREETEXTTABLE(Production.ProductDescription,  
    Description,   
    'high level of performance',  
    LANGUAGE N'English', 2) AS KEY_TBL  
ON FT_TBL.ProductDescriptionID = KEY_TBL.[KEY]  
ORDER BY RANK DESC;  
GO  
```  
  
> [!NOTE]  
>  Язык *language_term* являются*r* не требуется для использования *top_n_by_rank* параметр*.*  
  
## <a name="see-also"></a>См. также:  
 [Приступая к работе с компонентом Full-Text Search](../../relational-databases/search/get-started-with-full-text-search.md)   
 [Создание и управление ими полнотекстовых каталогов](../../relational-databases/search/create-and-manage-full-text-catalogs.md)   
 [CREATE FULLTEXT CATALOG #40; Transact-SQL &#41;](../../t-sql/statements/create-fulltext-catalog-transact-sql.md)   
 [CREATE FULLTEXT INDEX (Transact-SQL)](../../t-sql/statements/create-fulltext-index-transact-sql.md)   
 [Создание и управление полнотекстовыми индексами](../../relational-databases/search/create-and-manage-full-text-indexes.md)   
 [Запрос с Full-Text Search](../../relational-databases/search/query-with-full-text-search.md)   
 [Создание запросов полнотекстового поиска (визуальные инструменты для баз данных)](http://msdn.microsoft.com/library/537fa556-390e-4c88-9b8e-679848d94abc)   
 [CONTAINS (Transact-SQL)](../../t-sql/queries/contains-transact-sql.md)   
 [CONTAINSTABLE (Transact-SQL)](../../relational-databases/system-functions/containstable-transact-sql.md)   
 [FREETEXT (Transact-SQL)](../../t-sql/queries/freetext-transact-sql.md)   
 [Функции наборов строк &#40; Transact-SQL &#41;](../../t-sql/functions/rowset-functions-transact-sql.md)   
 [SELECT (Transact-SQL)](../../t-sql/queries/select-transact-sql.md)   
 [ГДЕ &#40; Transact-SQL &#41;](../../t-sql/queries/where-transact-sql.md)   
 [Параметр конфигурации сервера «precompute rank»](../../database-engine/configure-windows/precompute-rank-server-configuration-option.md)  
  
  
