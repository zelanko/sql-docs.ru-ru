---
title: Запрос с полнотекстовым поиском | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: search, sql-database
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- queries [full-text search], about full-text queries
- queries [full-text search], predicates
- full-text queries [SQL Server], about full-text queries
- full-text search [SQL Server], querying SQL Server
- full-text queries [SQL Server]
- queries [full-text search], functions
ms.assetid: 7624ba76-594b-4be5-ac10-c3ac4a3529bd
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 4b597fffe92f7cfc8a0000ccdf2d34005c8f7164
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/15/2018
ms.locfileid: "51660583"
---
# <a name="query-with-full-text-search"></a>Запрос с полнотекстовым поиском
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
Пишите полнотекстовые запросы с помощью предикатов **CONTAINS** и **FREETEXT** и функций **CONTAINSTABLE** и **FREETEXTTABLE**, возвращающих наборы строк, с инструкцией **SELECT**. В этой статье приведены примеры предикатов и функций, из которых вы сможете выбрать самые подходящие.

-   Для сопоставления слов и фраз используйте функции **CONTAINS** и **CONTAINSTABLE**.
-   Для поиска совпадений по смыслу, а не буквального совпадения, используйте функции **FREETEXT** и **FREETEXTTABLE**.

## <a name="examples_simple"></a> Примеры предикатов и функций

Ниже приводятся примеры базы данных AdventureWorks. Окончательный выпуск AdventureWorks см. в разделе [Базы данных и сценарии AdventureWorks для SQL Server 2016 CTP3](https://www.microsoft.com/download/details.aspx?id=49502). Чтобы запустить примеры запросов, нужно также настроить полнотекстовый поиск. Дополнительные сведения см. в разделе [Начало работы с полнотекстовым поиском](get-started-with-full-text-search.md). 

### <a name="example---contains"></a>Пример CONTAINS  
В следующем примере выполняется поиск всех продуктов с ценой `$80.99`, которые содержат слово `"Mountain"`:
  
```sql
USE AdventureWorks2012  
GO  
  
SELECT Name, ListPrice  
FROM Production.Product  
WHERE ListPrice = 80.99  
   AND CONTAINS(Name, 'Mountain')  
GO  
```  
  
### <a name="example---freetext"></a>Пример FREETEXT 
 В следующем примере выполняется поиск всех документов, содержащих слова, связанные с `vital safety components`:
  
```sql
USE AdventureWorks2012  
GO  
  
SELECT Title  
FROM Production.Document  
WHERE FREETEXT (Document, 'vital safety components')  
GO  
```

### <a name="example---containstable"></a>Пример CONTAINSTABLE  
 В приведенном ниже примере возвращается идентификатор описания и описание всех товаров, для которых столбец **Description** содержит слово "aluminum" рядом со словом "light" или "lightweight". Возвращаются только строки с рангом 2 и выше.  
  
```sql
USE AdventureWorks2012  
GO  
  
SELECT FT_TBL.ProductDescriptionID,  
   FT_TBL.Description,   
   KEY_TBL.RANK  
FROM Production.ProductDescription AS FT_TBL INNER JOIN  
   CONTAINSTABLE (Production.ProductDescription,  
      Description,   
      '(light NEAR aluminum) OR  
      (lightweight NEAR aluminum)'  
   ) AS KEY_TBL  
   ON FT_TBL.ProductDescriptionID = KEY_TBL.[KEY]  
WHERE KEY_TBL.RANK > 2  
ORDER BY KEY_TBL.RANK DESC;  
GO  
```  
  
### <a name="example---freetexttable"></a>Пример FREETEXTTABLE  
 В следующем примере запрос FREETEXTTABLE расширяется таким образом, чтобы он возвратил первыми строки с самыми высокими ранжирующими значениями и добавил ранг каждой строки к списку выбора. Чтобы написать аналогичный запрос, необходимо знать, что столбец **ProductDescriptionID** является уникальным ключевым столбцом для таблицы **ProductDescription**.  
  
```sql 
USE AdventureWorks2012  
GO  
  
SELECT KEY_TBL.RANK, FT_TBL.Description  
FROM Production.ProductDescription AS FT_TBL   
     INNER JOIN  
     FREETEXTTABLE(Production.ProductDescription, Description,  
                    'perfect all-around bike') AS KEY_TBL  
     ON FT_TBL.ProductDescriptionID = KEY_TBL.[KEY]  
ORDER BY KEY_TBL.RANK DESC  
GO  
```  
  
Ниже приведено расширение того же запроса, которое возвращает только строки с рангом 10 или выше.  
  
```sql  
USE AdventureWorks2012  
GO  
  
SELECT KEY_TBL.RANK, FT_TBL.Description  
FROM Production.ProductDescription AS FT_TBL   
     INNER JOIN  
     FREETEXTTABLE(Production.ProductDescription, Description,  
                    'perfect all-around bike') AS KEY_TBL  
     ON FT_TBL.ProductDescriptionID = KEY_TBL.[KEY]  
WHERE KEY_TBL.RANK >= 10  
ORDER BY KEY_TBL.RANK DESC  
GO  
```  

## <a name="match-words-or-match-meaning"></a>Сопоставление слов или смысла

`CONTAINS`/`CONTAINSTABLE` и `FREETEXT`/`FREETEXTTABLE` полезны для различных типов сопоставления. Следующая информация поможет выбрать самый подходящий предикат или функцию для запроса:

### <a name="containscontainstable"></a>CONTAINS/CONTAINSTABLE

-   Поиск точных и неточных соответствий отдельных слов и фраз.
-   Вы сможете также делать следующее:
    -   указывать уровень сходства похожих слов;
    -   возвращать взвешенные совпадения;
    -   объединять условия поиска с логическими операторами. Дополнительные сведения см. в разделе [Использование логических операторов (AND, OR и NOT)](#Using_Boolean_Operators) далее в этой статье.

### <a name="freetextfreetexttable"></a>FREETEXT/FREETEXTTABLE

-   Поиск совпадений по смыслу, а не по буквальному совпадению задаваемых слов, фраз или предложений (*текст в свободной форме*).
-   Соответствие регистрируется, если в полнотекстовом индексе указанного столбца найден любой из терминов в любой форме.

## <a name="compare-predicates-and-functions"></a>Сравнение предикатов и функций

Синтаксис и параметры предикатов `CONTAINS`/`FREETEXT`, а также функций, возвращающих наборы строк, `CONTAINSTABLE`/`FREETEXTTABLE` отличаются. Следующая информация поможет выбрать самый подходящий предикат или функцию для запроса:

### <a name="predicates-contains-and-freetext"></a>Предикаты CONTAINS и FREETEXT

**Использование**. Полнотекстовые **предикаты** CONTAINS и FREETEXT используются в предложении WHERE или HAVING инструкции SELECT.

**Результаты**. Предикаты CONTAINS и FREETEXT возвращают значение TRUE или FALSE, которое указывает, соответствует ли данная строка полнотекстовому запросу. Совпадающие строки возвращаются в результирующем наборе.

**Дополнительные параметры**. Предикаты можно объединить с любым из других предикатов [!INCLUDE[tsql](../../includes/tsql-md.md)], например LIKE и BETWEEN.

Вы можете указать, следует ли искать один столбец, список столбцов или все столбцы в таблице.

Вы также можете указать язык, ресурсы на котором используются данным полнотекстовым запросом для разбиения на слова и выделения корней, поиска в тезаурусе и удаления пропускаемых слов.

Четырехкомпонентное имя может использоваться в предикате CONTAINS или FREETEXT для запроса по столбцам полнотекстового индекса целевых таблиц на связанном сервере. Чтобы подготовить удаленный сервер к приему полнотекстовых запросов, сначала необходимо создать полнотекстовые индексы для целевых таблиц и столбцов на удаленном сервере, а затем добавить удаленный сервер в качестве связанного сервера.

**Дополнительные сведения**. Дополнительные сведения о синтаксисе и аргументах этих предикатов см. в статьях о [CONTAINS](../../t-sql/queries/contains-transact-sql.md) и [FREETEXT](../../t-sql/queries/freetext-transact-sql.md).

### <a name="rowset-valued-functions-containstable-and-freetexttable"></a>Функции со значениями набора строк CONTAINSTABLE и FREETEXTTABLE

**Использование**. Полнотекстовые **функции** CONTAINSTABLE и FREETEXTTABLE можно использовать в предложении FROM инструкции SELECT, как обычное имя таблицы.

Вам нужно указать базовую таблицу для поиска при использовании любой из этих функций. Как и для предикатов, в таблице, где выполняется поиск, можно задавать один столбец, список столбцов или все столбцы, а также при необходимости язык, ресурсы которого будут использоваться данным полнотекстовым запросом.

Обычно результат функций CONTAINSTABLE или FREETEXTTABLE необходимо соединять с базовой таблицей. Для присоединения таблиц необходимо знать уникальное имя ключевого столбца. Этот столбец, имеющийся в каждой таблице с поддержкой полнотекстового поиска, используется для принудительного применения уникальных строк в таблице (*уникальный**ключевой столбец*). Дополнительные сведения о ключевом столбце см. в статье [Создание полнотекстовых индексов и управление ими](../../relational-databases/search/create-and-manage-full-text-indexes.md).

**Результаты**. Эти функции возвращают пустую таблицу, либо таблицу с одной или несколькими строками, соответствующими полнотекстовому запросу. Возвращаемая таблица содержит только строки базовой таблицы, которые соответствуют критерию выбора, задаваемому в условии полнотекстового поиска функции.

Запросы, использующие одну из этих функций, также возвращают ранжирующие по релевантности значения (RANK) и полнотекстовый ключ (KEY) для каждой строки:

-   **Столбец KEY**. Столбец KEY возвращает уникальные значения возвращаемых строк. С помощью столбца KEY можно задавать критерии выбора.
-   **Столбец RANK**. Столбец RANK содержит *ранжирующее значение* для каждой строки, указывающее степень соответствия этой строки критериям выбора. Чем выше ранжирующее значение текста или документа в строке, тем больше она релевантна данному полнотекстовому запросу. Разные строки могут ранжироваться одинаково. Можно ограничить число возвращаемых совпадений. Для этого нужно задать необязательный параметр *top_n_by_rank* . Дополнительные сведения см. в разделе [Ограничение количества результатов поиска с использованием функции RANK](../../relational-databases/search/limit-search-results-with-rank.md).

**Дополнительные сведения**. Дополнительные сведения о синтаксисе и аргументах этих функций см. в статьях о [CONTAINSTABLE](../../relational-databases/system-functions/containstable-transact-sql.md) и [FREETEXTTABLE](../../relational-databases/system-functions/freetexttable-transact-sql.md).

## <a name="examples_specific"></a> Определенные типы поиска

###  <a name="Simple_Term"></a>Поиск конкретного слова или фразы (простое выражение)  
 Для поиска конкретного слова или фразы в таблице можно использовать запросы [CONTAINS](../../t-sql/queries/contains-transact-sql.md), [CONTAINSTABLE](../../relational-databases/system-functions/containstable-transact-sql.md), [FREETEXT](../../t-sql/queries/freetext-transact-sql.md) или [FREETEXTTABLE](../../relational-databases/system-functions/freetexttable-transact-sql.md). Например, для поиска в таблице **ProductReview** базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] всех комментариев о продукции, содержащих фразу "learning curve", можно использовать предикат CONTAINS следующим образом:  
  
```sql
USE AdventureWorks2012  
GO  
  
SELECT Comments  
FROM Production.ProductReview  
WHERE CONTAINS(Comments, '"learning curve"')  
GO  
```  
  
Условие поиска (в этом случае "learning curve") может быть сложным и включать одно выражение или несколько.

#### <a name="more-info-about-simple-term-searches"></a>Дополнительные сведения о простых условиях поиска

В полнотекстовом поиске *слово* (или *токен*) представляет собой строку, границы которой определяются соответствующими словами согласно лингвистическим правилам указанного языка. Допустимая *фраза* состоит из нескольких слов со знаками препинания между ними или без них.

Например, «круассан» — это слово, а «кофе с молоком» — фраза. Такие слова и фразы называются простыми выражениями.

Функции[CONTAINS](../../t-sql/queries/contains-transact-sql.md) и [CONTAINSTABLE](../../relational-databases/system-functions/containstable-transact-sql.md) выполняют поиск точного соответствия для фразы. Функции[FREETEXT](../../t-sql/queries/freetext-transact-sql.md) и [FREETEXTTABLE](../../relational-databases/system-functions/freetexttable-transact-sql.md) разбивают фразу на отдельные слова.

###  <a name="Prefix_Term"></a>Поиск слова по префиксу (префиксное выражение)  
 Для поиска слов и фраз с указанным префиксом можно использовать функции [CONTAINS](../../t-sql/queries/contains-transact-sql.md) или [CONTAINSTABLE](../../relational-databases/system-functions/containstable-transact-sql.md) . Будут возвращены все записи в столбце, содержащие текст, который начинается с заданного префикса. Например, чтобы найти все строки, содержащие префикс `top`-, как в `top``ple`, `top``ping`и `top`. Запрос выглядит следующим образом:  
  
```sql  
USE AdventureWorks2012  
GO  
  
SELECT Description, ProductDescriptionID  
FROM Production.ProductDescription  
WHERE CONTAINS (Description, '"top*"' )  
GO  
```  
  
 При выполнении этого запроса будут возвращены все фрагменты текста, соответствующие тексту, указанному перед звездочкой (*). Если текст и звездочка не ограничены двойными кавычками (например, `CONTAINS (DESCRIPTION, 'top*')`), звездочка не считается символом-шаблоном.  
  
 Если префиксный терм является фразой, каждый токен, составляющий фразу, считается отдельным префиксным термом. При выполнении такого запроса будут возвращены все строки со словами, начинающимися на префиксные термы. Например, если запрос включает префиксное выражение "белый хлеб\*", будут возвращены строки с текстом "белый хлебец", "белый хлебный" и "белый хлеб", но не "белый поджаренный хлеб".

#### <a name="more-info-about-prefix-searches"></a>Дополнительные сведения о поиске префиксов

Для создания производного слова или словоформ *префиксное выражение* обращается к строке, прикрепленной к началу слова.

-   Для единственного префиксного выражения частью результирующего набора будет любое слово, начинающееся с указанного выражения. Например, для префиксного выражения "авто *" совпадениями будут "автоматический", "автомобиль" и т. д.

-   Внутри фразы каждое слово считается префиксным выражением. Например, выражение "авто тран\*" соответствует фразам "автоматическая трансмиссия" и "автомобильный транспорт", но не "автомобильный личный транспорт".

Поиск префиксов поддерживается [CONTAINS](../../t-sql/queries/contains-transact-sql.md) и [CONTAINSTABLE](../../relational-databases/system-functions/containstable-transact-sql.md).
  
###  <a name="Inflectional_Generation_Term"></a>Поиск словоформ конкретного слова (производное выражение)  
С помощью функций [CONTAINS](../../t-sql/queries/contains-transact-sql.md), [CONTAINSTABLE](../../relational-databases/system-functions/containstable-transact-sql.md), [FREETEXT](../../t-sql/queries/freetext-transact-sql.md)или [FREETEXTTABLE](../../relational-databases/system-functions/freetexttable-transact-sql.md) можно найти все грамматические формы глаголов и существительных (поиск словоформ) или синонимы указанного слова (поиск по тезаурусу).  
  
В следующем примере выполняется поиск любых форм слова "foot" ("foot", "feet" и т. д.) в столбце `Comments` таблицы `ProductReview` в базе данных `AdventureWorks`. 
  
```sql  
USE AdventureWorks2012  
GO  
  
SELECT Comments, ReviewerName  
FROM Production.ProductReview  
WHERE CONTAINS (Comments, 'FORMSOF(INFLECTIONAL, "foot")')  
GO  
```  
  
В полнотекстовом поиске используются *парадигматические модули*, которые позволяют найти глагол в различных временах и лицах или существительное в формах единственного или множественного числа. Дополнительные сведения о парадигматических модулях см. в разделе [Настройка и управление средством разбиения на слова и парадигматические модули для поиска](../../relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md).  

#### <a name="more-info-about-generation-term-searches"></a>Дополнительные сведения о создании условий поиска

*Словоформы* — это глаголы в различных временах и лицах или существительные в формах единственного или множественного числа.

Примером такого поиска может служить поиск словоформ слова "водить". Если разные строки таблицы содержат слова "водить", "водит", "водят", "водил" и "водите", все они войдут в результирующий набор, потому что каждое из этих слов можно образовать флективным способом от слова "водить".

Запросы[FREETEXT](../../t-sql/queries/freetext-transact-sql.md) и [FREETEXTTABLE](../../relational-databases/system-functions/freetexttable-transact-sql.md) по умолчанию ищут словоформы всех указанных слов. Запросы [CONTAINS](../../t-sql/queries/contains-transact-sql.md) и [CONTAINSTABLE](../../relational-databases/system-functions/containstable-transact-sql.md) поддерживают необязательный аргумент `INFLECTIONAL`.

### <a name="search-for-synonyms-of-a-specific-word"></a>Поиск синонимов конкретного слова

В *тезаурусе* определяются пользовательские синонимы терминов. Дополнительные сведения о файлах тезауруса см. в статье [Настройка файлов тезауруса для полнотекстового поиска и управление ими](../../relational-databases/search/configure-and-manage-thesaurus-files-for-full-text-search.md).

Например, если в тезаурусе есть запись "{машина, автомобиль, грузовик, фургон}", можно искать синонимическую форму слова "машина". В результирующий набор войдут все строки таблицы, содержащие слова "автомобиль", "грузовик", "фургон" или "машина", потому что каждое из этих слов входит в состав расширяющего набора синонимов, содержащего и слово "машина".

По умолчанию тезаурус используется в запросах[FREETEXT](../../t-sql/queries/freetext-transact-sql.md) и [FREETEXTTABLE](../../relational-databases/system-functions/freetexttable-transact-sql.md) . Запросы [CONTAINS](../../t-sql/queries/contains-transact-sql.md) и [CONTAINSTABLE](../../relational-databases/system-functions/containstable-transact-sql.md) поддерживают необязательный аргумент `THESAURUS`.

### <a name="search-for-a-word-near-another-word"></a>Поиск слова ОКОЛО другого слова

*Выражение с учетом расположения* означает слова или фразы, которые находятся рядом друг с другом. Также можно указать максимальное количество слов, которые не включаются в поиск и разделяют первое и последнее из искомых слов. Кроме того, можно искать два слова или две фразы в любом порядке или в порядке, в котором они указаны.

Примером может служить поиск строк, в которых слово "лед" находится рядом со словом "хоккей" или фраза "хоккей на льду" — рядом с фразой "катание на коньках". 

[CONTAINS](../../t-sql/queries/contains-transact-sql.md) и [CONTAINSTABLE](../../relational-databases/system-functions/containstable-transact-sql.md)

Дополнительные сведения о поиске похожих слов см. в разделе [Поиск слов близких к другим с использованием оператора NEAR](search-for-words-close-to-another-word-with-near.md).

###  <a name="Weighted_Term"></a>Поиск слов или фраз с использованием взвешенных величин (взвешенное выражение)  
Для поиска слов и фраз можно использовать функцию [CONTAINSTABLE](../../relational-databases/system-functions/containstable-transact-sql.md) с взвешенными значениями. Вес, измеряемый числом от 0,0 до 1,0, обозначает степень важности каждого слова и фразы в наборе слов или фраз. Значение веса 0,0 является самым низким, значение 1,0 — самым высоким.  
  
В следующем примере показан запрос, выполняющий поиск (с использованием взвешенных значений) всех адресов заказчиков, в которых текст, начинающийся со строки "Залив", продолжается строкой "Улица" или "Вид". В результатах более высокий ранг назначается тем строкам, в которых встречается больше заданных слов.  
  
```sql  
USE AdventureWorks2012  
GO  
  
SELECT AddressLine1, KEY_TBL.RANK   
FROM Person.Address AS Address INNER JOIN  
CONTAINSTABLE(Person.Address, AddressLine1, 'ISABOUT ("Bay*",   
         Street WEIGHT(0.9),   
         View WEIGHT(0.1)  
         ) ' ) AS KEY_TBL  
ON Address.AddressID = KEY_TBL.[KEY]  
ORDER BY KEY_TBL.RANK DESC  
GO  
```  
  
 Взвешенное выражение можно использовать в сочетании с любым простым выражением, префиксным выражением, производным выражением или выражением с учетом расположения.

#### <a name="more-info-about-weighted-term-searches"></a>Дополнительные сведения о взвешенных условиях поиска

Во взвешенных условиях поиска *взвешенное значение* показывает уровень важности каждого слова и фразы в наборе слов и фраз. Значение веса 0,0 является самым низким, значение 1,0 — самым высоким.

Например, в запросе для поиска нескольких выражений можно задать вес для каждого искомого слова, обозначающий его значимость по сравнению с другими словами в условии поиска. Результат выполнения такого типа запроса будет в начале содержать наиболее релевантные строки, исходя из соответствующего веса, присвоенного искомым словам. В результирующих наборах содержатся документы или строки с любыми из указанных выражений (или содержимым, которое находится между ними), однако некоторые из результатов будут считаться важнее остальных ввиду разницы во взвешенных значениях, связанных с различными выражениями, по которым выполнялся поиск.

Поиск взвешенных условий поиска поддерживается [CONTAINSTABLE](../../relational-databases/system-functions/containstable-transact-sql.md).

##  <a name="Using_Boolean_Operators"></a> Использование операторов AND, OR и NOT (логические операторы)
 
Функция CONTAINSTABLE и предикат CONTAINS используют одинаковые условия поиска. Они поддерживают объединение нескольких искомых терминов (с помощью логических операторов AND, OR и NOT) для выполнения логических операций. Например, оператор AND можно использовать для поиска строк, содержащих и "латте", и "пирожное с кремом". Например, с помощью оператора AND NOT можно находить строки, которые содержат слово "бублик", но не содержат "мак".  
  
Предикаты FREETEXT и FREETEXTTABLE, напротив, обрабатывают логические термины как слова, которые следует искать.  
  
 Сведения о сочетании предиката CONTAINS с другими предикатами, которые используют логические операторы AND, OR и NOT, см. в разделе [Условие поиска (Transact-SQL)](../../t-sql/queries/search-condition-transact-sql.md).  
  
### <a name="example"></a>Пример  
 Следующий пример использует предикат CONTAINS для поиска описаний, в которых идентификатор описания не равен 5, содержащих слова Aluminum и spindle. Условие поиска использует логический оператор AND. В следующем примере используется таблица ProductDescription базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].
  
```sql  
USE AdventureWorks2012  
GO  
  
SELECT Description  
FROM Production.ProductDescription  
WHERE ProductDescriptionID <> 5 AND  
   CONTAINS(Description, 'aluminum AND spindle')  
GO  
```  
  
##  <a name="Additional_Considerations"></a> Регистр, стоп-слова, язык и тезаурус

 При написании полнотекстовых запросов можно также указать следующие параметры.
  
-   **Учет регистра букв**. В запросах полнотекстового поиска не учитывается регистр букв. Однако в японском языке есть несколько фонетических орфографий, в которых концепция орфографической нормализации аналогична нечувствительности к регистру (например, японская азбука = нечувствительность). Этот тип орфографической нормализации не поддерживается.  

-   **Стоп-слова**. При определении полнотекстового запроса следует иметь в виду, что средство полнотекстового поиска не учитывает стоп-слова (также известные как пропускаемые слова), указанные в критерии поиска. Стоп-слова — это часто встречающиеся слова, которые не повышают эффективность поиска конкретного текста. Примерами могут служить слова «и», «или», «о» и «в». Стоп-слова перечислены в списке стоп-слов. Каждый полнотекстовый индекс связан с конкретным списком стоп-слов, который определяет, какие стоп-слова не указываются в запросе или в индексе во время индексирования. Дополнительные сведения см. в статье [Настройка стоп -слов и списков стоп-слов для полнотекстового поиска и управление ими](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md).  

-   **Язык** с помощью параметра **LANGUAGE**. Многие выражения запроса в значительной степени зависят от поведения средства разбиения по словам. Чтобы гарантировать использование правильного средства разбиения по словам (и парадигматического модуля) и файла тезауруса, рекомендуется указывать параметр LANGUAGE. Дополнительные сведения см. в разделе [Выбор языка при создании полнотекстового индекса](../../relational-databases/search/choose-a-language-when-creating-a-full-text-index.md).  
  
-   **Тезаурус**. По умолчанию тезаурус используется в запросах FREETEXT и FREETEXTTABLE. Предикат CONTAINS и функция CONTAINSTABLE поддерживают необязательный аргумент THESAURUS. Дополнительные сведения см. в статье [Настройка файлов тезауруса для полнотекстового поиска и управление ими](configure-and-manage-thesaurus-files-for-full-text-search.md).
  
##  <a name="tokens"></a>Проверка результатов разметки

После применения сочетания заданного средства разбивки текста на слова, тезауруса и списка стоп-слов в запросе итоговый результат разметки полнотекстового поиска можно просмотреть с помощью динамического административного представления **sys.dm_fts_parser**. Дополнительные сведения см. в разделе [sys.dm_fts_parser (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-fts-parser-transact-sql.md).  
  
## <a name="see-also"></a>См. также:  
 [CONTAINS (Transact-SQL)](../../t-sql/queries/contains-transact-sql.md)   
 [CONTAINSTABLE (Transact-SQL)](../../relational-databases/system-functions/containstable-transact-sql.md)   
 [FREETEXT (Transact-SQL)](../../t-sql/queries/freetext-transact-sql.md)   
 [FREETEXTTABLE (Transact-SQL)](../../relational-databases/system-functions/freetexttable-transact-sql.md)   
 [Создание запросов полнотекстового поиска (визуальные инструменты для баз данных)](https://msdn.microsoft.com/library/537fa556-390e-4c88-9b8e-679848d94abc)   
 [Улучшение производительности полнотекстовых запросов](../../relational-databases/search/improve-the-performance-of-full-text-queries.md)
 
