---
title: "FREETEXT (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 08/11/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- FREETEXT
- FREETEXT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- full-text search [SQL Server], meaning matches
- meaning matches [full-text search]
- FREETEXT predicate (Transact-SQL)
- words in predicate [full-text search]
- column searches [full-text search]
ms.assetid: 2f199d3c-440e-4bcf-bdb5-82bb3994005d
caps.latest.revision: 44
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 48c7ce4788a0c5da0b22e80ab1dc366091c25f97
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="freetext-transact-sql"></a>FREETEXT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Предикат, используемый в [!INCLUDE[tsql](../../includes/tsql-md.md)] [предложение WHERE](../../t-sql/queries/where-transact-sql.md) из [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкции SELECT для выполнения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] полнотекстового поиска в полнотекстовых индексированных столбцах, содержащим типы символьных данных. Этот предикат выполняет поиск значений, которые соответствуют условию поиска по смыслу, а не написанию. Когда используется предикат FREETEXT, ядро полнотекстовых запросов автоматически выполняет следующие действия над *freetext_string*, присваивает вес каждому терму, а затем ищет совпадения:  
  
-   Разбивает строку на отдельные слова согласно границам слов (пословное разбиение).  
  
-   Формирует словоформы (а также производит выделение основы слова).  
  
-   Определяет список расширений или замен для термов на основании совпадений в тезаурусе.  
  
> [!NOTE]  
>  Дополнительные сведения о формах и полнотекстовом поиске, поддерживаемых [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], в разделе [запрос с Full-Text Search](../../relational-databases/search/query-with-full-text-search.md).  
  
**Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658)).
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
FREETEXT ( { column_name | (column_list) | * }   
          , 'freetext_string' [ , LANGUAGE language_term ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *column_name*  
 Имя одного или нескольких столбцов с полнотекстовой индексацией в таблице, указанной в предложении FROM. Столбцы могут иметь тип **char**, **varchar**, **nchar**, **nvarchar**, **текст**, **ntext**, **изображения**, **xml**, **varbinary**, или **varbinary(max)**.  
  
 *column_list*  
 Указывает, что можно задать несколько столбцов, разделенных запятыми. *column_list* должен быть заключен в круглые скобки. Если не *language_term* указано, язык всех столбцов *column_list* должны быть одинаковыми.  
  
 \*  
 Указывает, что все столбцы, которые были зарегистрированы для полнотекстового поиска следует использовать для поиска заданного *freetext_string*. Если более чем одна таблица из предложения FROM \* должно уточняться именем таблицы. Если не *language_term* указан, язык всех столбцов таблицы должны быть одинаковыми.  
  
 *freetext_string*  
 Текст для поиска в *column_name*. Допустимо вводить любой текст, включая слова, фразы или предложения. Соответствия формируются, если любой ключ или его формы найдены в полнотекстовом индексе.  
  
 В отличие от CONTAINS и CONTAINSTABLE поиска условием, где слово AND является ключевым, при использовании в *freetext_string* слова «и» считается пропускаемым словом или [стоп-слово](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)и будут потеряны.  
  
 Использование функций WEIGHT, FORMSOF, символов шаблонов, NEAR, а также других синтаксических элементов запрещено. *freetext_string* wordbroken и пропускается через тезаурус.  
  
 *freetext_string* — **nvarchar**. Если в качестве входных данных используется другой тип символьных данных, производится неявное преобразование. В следующем примере переменная `@SearchWord`, тип которой определен как `varchar(30)`, вызывает неявное преобразование в предикате `FREETEXT`.  
  
```  
  
USE AdventureWorks2012;  
GO  
DECLARE @SearchWord varchar(30)  
SET @SearchWord ='performance'  
SELECT Description   
FROM Production.ProductDescription   
WHERE FREETEXT(Description, @SearchWord);  
  
```  
  
 Так как «пробное сохранение параметров» не работает с преобразованием, используйте **nvarchar** для повышения производительности. В этом примере объявлять `@SearchWord` как `nvarchar(30)`.  
  
```  
  
USE AdventureWorks2012;  
GO  
DECLARE @SearchWord nvarchar(30)  
SET @SearchWord = N'performance'  
SELECT Description   
FROM Production.ProductDescription   
WHERE FREETEXT(Description, @SearchWord);  
  
```  
  
 Указанием запроса OPTIMIZE FOR можно также воспользоваться в случаях, когда формируется неоптимальный план.  
  
 Язык *language_term*  
 Язык, ресурсы которого будут использованы для разбиения по словам, выделения корня, проверки по тезаурусу и удаления стоп-слов в составе запроса. Этот аргумент не является обязательным и может быть строкой, целым числом или шестнадцатеричным значением, соответствующим идентификатору локали (LCID). Если *language_term* указан, то соответствующий язык будет применяться ко всем элементам условия поиска. Если значение не указано, то используется язык полнотекстового поиска, заданный для столбца.  
  
 Если в одном столбце хранятся документы на различных языках в виде больших двоичных объектов, то идентификатор локали заданного документа определяет, какой язык должен использоваться для индексирования его содержимого. При запросе такой столбец, указав *язык**language_term* может повысить вероятность хорошего соответствия.  
  
 Если указан как строка, *language_term* соответствует **псевдоним** значение столбца в он [sys.syslanguages &#40; Transact-SQL &#41; ](../../relational-databases/system-compatibility-views/sys-syslanguages-transact-sql.md) Просмотр в режиме совместимости.  Строка должна быть заключена в одинарные кавычки, например "*language_term*". Если указано как целое число, *language_term* фактический код, определяющий язык. Если указан как шестнадцатеричное значение *language_term* 0 x следуют шестнадцатеричное значение кода языка. Шестнадцатеричное значение не может иметь более восьми знаков, включая начальные нули.  
  
 Если значение указано в формате двухбайтовой кодировки (DBCS), [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] преобразует его в Юникод.  
  
 Если указанный язык не недопустим или ресурсы не установлены, соответствующие этому языку [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращает сообщение об ошибке. Для использования нейтральных языковых ресурсов укажите 0x0 как *language_term*.  
  
## <a name="general-remarks"></a>Общие замечания  
 Полнотекстовые предикаты и функции работают в одной таблице, что следует из наличия предиката FROM. Для поиска в нескольких таблицах используйте в предложении FROM соединенную таблицу, чтобы выполнять поиск в результирующем наборе, который получен в результате соединения нескольких таблиц.  
  
Полнотекстовые запросы с использованием FREETEXT являются менее точными, нежели полнотекстовые запросы с использованием CONTAINS. Средство [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] полнотекстового поиска идентифицирует важные слова и фразы. Нет специального назначения предоставить всем зарезервированные ключевые слова или подстановочные знаки, которые обычно имеют при использовании в \<contains_search_condition > параметр предиката CONTAINS.
  
 Полнотекстовые предикаты не допускаются в [предложение OUTPUT](../../t-sql/queries/output-clause-transact-sql.md) при уровне совместимости базы данных равным 100.  
  
> [!NOTE]  
>  Функция FREETEXTTABLE полезна для поиска совпадений того же типа, что и предикат FREETEXT. Можно ссылаться как на обычное имя таблицы в эту функцию [из предложения](../../t-sql/queries/from-transact-sql.md) инструкции SELECT. Дополнительные сведения см. в разделе [FREETEXTTABLE &#40; Transact-SQL &#41; ](../../relational-databases/system-functions/freetexttable-transact-sql.md).  
  
## <a name="querying-remote-servers"></a>Запрос к удаленному серверу  
 Можно использовать четырехкомпонентное имя в [CONTAINS](../../t-sql/queries/contains-transact-sql.md) или FREETEXT для запроса полнотекстовых индексированных столбцах целевых таблиц на связанном сервере. Чтобы подготовить удаленный сервер к приему полнотекстовых запросов, сначала необходимо создать полнотекстовые индексы для целевых таблиц и столбцов на удаленном сервере, а затем добавить удаленный сервер в качестве связанного сервера.  
  
## <a name="comparison-of-like-to-full-text-search"></a>Сравнение предиката LIKE с полнотекстовым поиском  
 В отличие от полнотекстового поиска предикат [LIKE](../../t-sql/language-elements/like-transact-sql.md)[!INCLUDE[tsql](../../includes/tsql-md.md)] работает только с комбинациями символов. Кроме того, предикат LIKE нельзя использовать в запросах к форматированным двоичным данным. Более того, запрос с предикатом LIKE к большому количеству неструктурированных текстовых данных выполняется гораздо медленнее, чем эквивалентный полнотекстовый запрос к тем же данным. Выполнение запроса LIKE к нескольким миллионам строк текстовых данных может занять несколько минут, в то время как полнотекстовый запрос к тем же данным занимает всего несколько секунд или даже меньше, в зависимости от количества возвращаемых строк.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-freetext-to-search-for-words-containing-specified-character-values"></a>A. Использование инструкции FREETEXT для поиска слов, содержащих определенные значения символов  
 Следующий пример просматривает все документы, содержащие слова, которые связаны со словами «vital», «safety», «components».  
  
```  
USE AdventureWorks2012;  
GO  
SELECT Title  
FROM Production.Document  
WHERE FREETEXT (Document, 'vital safety components' );  
GO  
```  
  
### <a name="b-using-freetext-with-variables"></a>Б. Использование FREETEXT с переменными  
 Нижеприведенные примеры используют переменную вместо конкретного термина для поиска.  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @SearchWord nvarchar(30);  
SET @SearchWord = N'high-performance';  
SELECT Description   
FROM Production.ProductDescription   
WHERE FREETEXT(Description, @SearchWord);  
GO  
```  
  
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
 [Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)   
 [FREETEXTTABLE (Transact-SQL)](../../relational-databases/system-functions/freetexttable-transact-sql.md)   
 [ГДЕ &#40; Transact-SQL &#41;](../../t-sql/queries/where-transact-sql.md)  
  
  

