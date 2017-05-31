---
title: "Запрос с полнотекстовым поиском | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-search
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- queries [full-text search], about full-text queries
- queries [full-text search], predicates
- full-text queries [SQL Server], about full-text queries
- full-text search [SQL Server], querying SQL Server
- full-text queries [SQL Server]
- queries [full-text search], functions
ms.assetid: 7624ba76-594b-4be5-ac10-c3ac4a3529bd
caps.latest.revision: 80
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 5034ce123455c63718fb41b02450c14ca2f68a0b
ms.contentlocale: ru-ru
ms.lasthandoff: 04/11/2017

---
# <a name="query-with-full-text-search"></a>Запрос с полнотекстовым поиском

Пишите полнотекстовые запросы при помощи полнотекстовых предикатов **CONTAINS** и **FREETEXT** и функций, возвращающих наборы строк **CONTAINSTABLE** и **FREETEXTTABLE** с инструкцией **SELECT**. В этом разделе приведены примеры предикатов и функций, из которых вы сможете выбрать самые подходящие.

-   Используйте функции **CONTAINS** и **CONTAINSTABLE** для сопоставления слов и фраз.
-   Используйте функции **FREETEXT** и **FREETEXTTABLE** для поиска совпадений по смыслу, а не буквального совпадения.

## <a name="examples_simple"></a>Простые примеры предикатов и функций

### <a name="example---contains"></a>Пример CONTAINS  
 В следующем примере выполняется поиск всех продуктов с ценой `$80.99` , которые содержат слово `"Mountain"`.  
  
```tsql
USE AdventureWorks2012  
GO  
  
SELECT Name, ListPrice  
FROM Production.Product  
WHERE ListPrice = 80.99  
   AND CONTAINS(Name, 'Mountain')  
GO  
```  
  
### <a name="example---freetext"></a>Пример FREETEXT 
 В следующем примере выполняется поиск всех документов, содержащих слова, связанные с терминами vital, safety, components.  
  
```tsql
USE AdventureWorks2012  
GO  
  
SELECT Title  
FROM Production.Document  
WHERE FREETEXT (Document, 'vital safety components')  
GO  
```

### <a name="example---containstable"></a>Пример CONTAINSTABLE  
 В следующем примере возвращается идентификатор описания и описание всех товаров, для которых столбец **Description** содержит слово «aluminum» рядом со словом «light» или «lightweight». Возвращаются только строки с рангом 2 и выше.  
  
```tsql
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
  
### <a name="example--freetexttable"></a>Пример FREETEXTTABLE  
 В следующем примере запрос FREETEXTTABLE расширяется таким образом, чтобы он возвратил первыми строки с самыми высокими ранжирующими значениями и добавил ранг каждой строки к списку выбора. Чтобы задать запрос, необходимо знать, что столбец **ProductDescriptionID** является уникальным ключевым столбцом для таблицы **ProductDescription** .  
  
```tsql 
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
  
Ниже приведено расширение того же запроса, которое возвращает только строки с ранжирующим значением 10 или выше.  
  
```tsql  
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

## <a name="pick-the-best-predicate-or-function"></a>Выбор самого подходящего предиката или функции

`CONTAINS`/`CONTAINSTABLE` и `FREETEXT`/`FREETEXTTABLE` полезны для различных типов сопоставления. Следующая таблица поможет выбрать самый подходящий предикат или функцию для запроса.

Примеры см. в разделе [Простые примеры предикатов и функций](#examples_simple) и [Примеры определенных типов операций поиска](#examples_specific). Кроме того, ознакомьтесь с разделом [Что можно искать](#supported).

| |CONTAINS/CONTAINSTABLE|FREETEXT/FREETEXTTABLE|
|---|---|---|
|**Тип запроса**|Поиск точных и неточных соответствий отдельных слов и фраз.|Поиск совпадений по смыслу, а не буквального совпадения задаваемых слов, фраз или предложений (*текст в свободной форме*).<br/><br/>Соответствие регистрируется, если в полнотекстовом индексе указанного столбца найден любой из терминов в любой форме.|
|**Дополнительные параметры запроса**|Вы можете задать уровень сходства похожих слов.<br/><br/>Вы можете возвращать взвешенные совпадения.<br/><br/>Вы можете использовать логическую операцию, чтобы комбинировать условия поиска. Дополнительные сведения см. в разделе [Использование логических операторов (AND, OR и NOT)](#Using_Boolean_Operators) далее в этой статье.|Недоступно|

## <a name="compare-predicates-and-functions"></a>Сравнение предикатов и функций

Синтаксис и параметры предикатов `CONTAINS`/`FREETEXT`, а также функций, возвращающих наборы строк, `CONTAINSTABLE`/`FREETEXTTABLE` отличаются. Следующая таблица поможет выбрать самый подходящий предикат или функцию для запроса.

Примеры см. в разделе [Простые примеры предикатов и функций](#examples_simple) и [Примеры определенных типов операций поиска](#examples_specific). Кроме того, ознакомьтесь с разделом [Что можно искать](#supported).

| |Предикаты<br/>CONTAINS/FREETEXT|Функции<br/>CONTAINSTABLE/FREETEXTTABLE|
|---|---|---|
|**Использование**|Полнотекстовые **предикаты** CONTAINS и FREETEXT используются в предложении WHERE или HAVING инструкции SELECT.|Полнотекстовые **функции** CONTAINSTABLE и FREETEXTTABLE можно использовать в предложении FROM инструкции SELECT, как обычное имя таблицы.|
|**Дополнительные параметры запроса**|Их можно объединить с любым из других предикатов [!INCLUDE[tsql](../../includes/tsql-md.md)], например LIKE и BETWEEN.<br/><br/>Вы можете указать, следует ли искать один столбец, список столбцов или все столбцы в таблице.<br/><br/>Вы также можете указать язык, ресурсы которого будут использоваться данным полнотекстовым запросом для разбиения слов и морфологического поиска, поиска в тезаурусе и удаления неучитываемых слов.|Вам нужно указать базовую таблицу для поиска при использовании любой из этих функций. Как и для предикатов, в таблице, где выполняется поиск, можно задавать один столбец, список столбцов или все столбцы и при необходимости язык, ресурсы которого будут использоваться данным полнотекстовым запросом.<br/><br/>Обычно результат функций CONTAINSTABLE или FREETEXTTABLE необходимо соединять с базовой таблицей. Для этого необходимо знать уникальное имя ключевого столбца. Этот столбец, имеющийся в каждой таблице с поддержкой полнотекстового поиска, используется для принудительного применения уникальных строк в таблице ( *уникальный**ключевой столбец*). Дополнительные сведения о ключевом столбце см. в статье [Создание полнотекстовых индексов и управление ими](../../relational-databases/search/create-and-manage-full-text-indexes.md).|
|**Результаты**|Предикаты CONTAINS и FREETEXT возвращают значение TRUE или FALSE, которое указывает, соответствует ли данная строка полнотекстовому запросу. Совпадающие строки возвращаются в результирующем наборе.|Эти функции возвращают пустую таблицу, либо таблицу с одной или несколькими строками, соответствующими полнотекстовому запросу. Возвращаемая таблица содержит только строки базовой таблицы, которые соответствуют критерию выбора, задаваемому в условии полнотекстового поиска функции.<br/><br/>Запросы, использующие одну из этих функций, также возвращают ранжирующие по релевантности значения (RANK) и полнотекстовый ключ (KEY) для каждой строки<br/><ul><li>**Столбец KEY**. Столбец KEY возвращает уникальные значения возвращаемых строк. С помощью столбца KEY можно задавать критерии выбора.</li><li>**Столбец RANK**. Столбец RANK содержит *ранжирующее значение* для каждой строки, указывающее степень соответствия этой строки критериям выбора. Чем выше ранжирующее значение текста или документа в строке, тем больше она релевантна данному полнотекстовому запросу. Следует отметить, что разные строки могут ранжироваться одинаково. Можно ограничить число возвращаемых совпадений. Для этого нужно задать необязательный параметр *top_n_by_rank* . Дополнительные сведения см. в разделе [Ограничение количества результатов поиска с использованием функции RANK](../../relational-databases/search/limit-search-results-with-rank.md).</li></ul>|
|**Дополнительные параметры**|Четырехкомпонентное имя может использоваться в предикате CONTAINS или FREETEXT для запроса по столбцам полнотекстового индекса целевых таблиц на связанном сервере. Чтобы подготовить удаленный сервер к приему полнотекстовых запросов, сначала необходимо создать полнотекстовые индексы для целевых таблиц и столбцов на удаленном сервере, а затем добавить удаленный сервер в качестве связанного сервера.|Недоступно|
|**Дополнительные сведения**|Дополнительные сведения о синтаксисе и аргументах этих предикатов см. в статьях о [CONTAINS](../../t-sql/queries/contains-transact-sql.md) и [FREETEXT](../../t-sql/queries/freetext-transact-sql.md).|Дополнительные сведения о синтаксисе и аргументах этих функций см. в статьях о [CONTAINSTABLE](../../relational-databases/system-functions/containstable-transact-sql.md) и [FREETEXTTABLE](../../relational-databases/system-functions/freetexttable-transact-sql.md).|

##  <a name="supported"></a>Что можно искать

В следующей таблице представлено описание типов слов и фраз, которые можно искать.
  
|Форма выражений запросов|Description|Поддерживаются|  
|----------------------|-----------------|------------------|  
|Одно или несколько конкретных слов или фраз<br/>(*простые выражения*)|Например, «круассан» — это слово, а «кофе с молоком» — фраза. Такие слова и фразы называются простыми выражениями.<br /><br /> В полнотекстовом поиске *слово* (или *токен*) представляет собой строку, границы которой определяются соответствующими словами согласно лингвистическим правилам указанного языка. Допустимая *фраза* состоит из нескольких слов со знаками препинания между ними или без них.<br /><br /> Дополнительные сведения см. в подразделе [Поиск конкретного слова или фразы (простое выражение)](#Simple_Term)далее в этом разделе.|Функции[CONTAINS](../../t-sql/queries/contains-transact-sql.md) и [CONTAINSTABLE](../../relational-databases/system-functions/containstable-transact-sql.md) выполняют поиск точного соответствия для фразы.<br /><br /> Функции[FREETEXT](../../t-sql/queries/freetext-transact-sql.md) и [FREETEXTTABLE](../../relational-databases/system-functions/freetexttable-transact-sql.md) разбивают фразу на отдельные слова.|  
|Слова, начинающиеся заданным текстом, или фразы с такими словами<br/>(*префиксные выражения*)|Для единственного префиксного выражения частью результирующего набора будет любое слово, начинающееся с указанного выражения. Например, для префиксного выражения «auto*» совпадениями будут «automatic», «automobile» и т. д.<br /><br /> Внутри фразы каждое слово считается префиксным выражением. Например, выражение "авто тран\*" соответствует фразам "автоматическая трансмиссия" и "автомобильный транспорт", но не "автомобильный личный транспорт".<br /><br /> Для создания производного слова или словоформ *префиксное выражение* обращается к строке, прикрепленной к началу слова.<br /><br /> Дополнительные сведения см. в подразделе [Поиск префиксных форм слов или фраз (префиксное выражение)](#Prefix_Term)далее в этом разделе.|[CONTAINS](../../t-sql/queries/contains-transact-sql.md) and [CONTAINSTABLE](../../relational-databases/system-functions/containstable-transact-sql.md)|  
|Словоформы конкретного слова<br/>(*производное выражение*)|Примером такого поиска может служить поиск словоформ слова «водить». Если разные строки таблицы содержат слова «водить», «водит», «водят», «водил» и «водите», все они войдут в результирующий набор, потому что каждое из этих слов можно образовать флективным способом от слова «водить».<br /><br /> *Словоформы* — это глаголы в различных временах и лицах или существительные в формах единственного или множественного числа. <br /><br /> Дополнительные сведения см. в подразделе [Поиск флективных форм конкретного слова (производного терма)](#Inflectional_Generation_Term)далее в этом разделе.|Запросы[FREETEXT](../../t-sql/queries/freetext-transact-sql.md) и [FREETEXTTABLE](../../relational-databases/system-functions/freetexttable-transact-sql.md) по умолчанию ищут словоформы всех указанных слов.<br /><br /> Запросы[CONTAINS](../../t-sql/queries/contains-transact-sql.md) и [CONTAINSTABLE](../../relational-databases/system-functions/containstable-transact-sql.md) поддерживают необязательный аргумент INFLECTIONAL.|  
|Синонимические формы конкретного слова<br/>(*тезаурус*)|Например, если в тезаурусе есть запись «{машина, автомобиль, грузовик, фургон}», можно искать синонимическую форму слова «машина». В результирующий набор войдут все строки таблицы, содержащие слова «автомобиль», «грузовик», «фургон» или «машина», потому что каждое из этих слов входит в состав расширяющего набора синонимов, содержащего и слово «машина».<br /><br />В *тезаурусе* определяются пользовательские синонимы терминов.<br /><br />  Дополнительные сведения о структуре файлов тезауруса см. в разделе [Настройка и управление файлами тезауруса для полнотекстового поиска](../../relational-databases/search/configure-and-manage-thesaurus-files-for-full-text-search.md).|По умолчанию тезаурус используется в запросах[FREETEXT](../../t-sql/queries/freetext-transact-sql.md) и [FREETEXTTABLE](../../relational-databases/system-functions/freetexttable-transact-sql.md) .<br /><br /> Предикат[CONTAINS](../../t-sql/queries/contains-transact-sql.md) и функция [CONTAINSTABLE](../../relational-databases/system-functions/containstable-transact-sql.md) поддерживают необязательный аргумент THESAURUS.|  
|Слова или фразы, находящиеся рядом с другими словами или фразами<br/>(*выражения с учетом расположения*)|Примером может служить поиск строк, в которых слово «лед» находится рядом со словом «хоккей» или фраза «хоккей на льду» — рядом с фразой «катание на коньках».<br /><br /> *Выражение с учетом расположения* указывает слова или фразы, находящиеся рядом друг с другом. Кроме того, вы можете указать максимальное количество не относящихся к поиску выражений, отделяющих первое и последнее поисковые выражения. Кроме того, можно искать два слова или две фразы в любом порядке или в порядке, в котором они указаны.<br /><br /> Дополнительные сведения см. в разделе [Поиск слов близких к другим с использованием оператора NEAR](../../relational-databases/search/search-for-words-close-to-another-word-with-near.md).|[CONTAINS](../../t-sql/queries/contains-transact-sql.md) and [CONTAINSTABLE](../../relational-databases/system-functions/containstable-transact-sql.md)|  
|Слова или фразы со взвешенными значениями<br/>(*взвешенное выражение*)|Например, в запросе для поиска нескольких выражений можно задать вес для каждого искомого слова, обозначающий его значимость по сравнению с другими словами в условии поиска. Результат выполнения такого типа запроса будет в начале содержать наиболее релевантные строки, исходя из соответствующего веса, присвоенного искомым словам. В результирующих наборах содержатся документы или строки с любыми из указанных выражений (или содержимым, которое находится между ними), однако некоторые из результатов будут считаться важнее остальных ввиду разницы во взвешенных значениях, связанных с различными выражениями, по которым выполнялся поиск.<br /><br /> *Взвешенное значение* показывает уровень важности каждого слова и фразы в наборе слов и фраз. Значение веса 0,0 является самым низким, значение 1,0 — самым высоким.<br /><br /> Дополнительные сведения см. в подразделе [Поиск слов или фраз с использованием взвешенных величин (взвешенное выражение)](#Weighted_Term)далее в этом разделе.|[CONTAINSTABLE](../../relational-databases/system-functions/containstable-transact-sql.md)|  

## <a name="examples_specific"></a>Примеры определенных типов поиска

###  <a name="Simple_Term"></a>Поиск конкретного слова или фразы (простое выражение)  
 Для поиска конкретной фразы в таблице можно использовать запросы [CONTAINS](../../t-sql/queries/contains-transact-sql.md), [CONTAINSTABLE](../../relational-databases/system-functions/containstable-transact-sql.md), [FREETEXT](../../t-sql/queries/freetext-transact-sql.md)или [FREETEXTTABLE](../../relational-databases/system-functions/freetexttable-transact-sql.md) . Например, для поиска в таблице **ProductReview** базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] всех комментариев о продукции, содержащих фразу "learning curve", можно использовать предикат CONTAINS следующим образом:  
  
```tsql
USE AdventureWorks2012  
GO  
  
SELECT Comments  
FROM Production.ProductReview  
WHERE CONTAINS(Comments, '"learning curve"')  
GO  
```  
  
 Условие поиска (в данном случае learning curve) может быть весьма сложным и включать одно или несколько выражений.  
  
###  <a name="Prefix_Term"></a>Поиск слова по префиксу (префиксное выражение)  
 Для поиска слов и фраз с указанным префиксом можно использовать функции [CONTAINS](../../t-sql/queries/contains-transact-sql.md) или [CONTAINSTABLE](../../relational-databases/system-functions/containstable-transact-sql.md) . Будут возвращены все записи в столбце, содержащие текст, который начинается с заданного префикса. Например, чтобы найти все строки, содержащие префикс `top`-, как в `top``ple`, `top``ping`и `top`. Запрос выглядит следующим образом:  
  
```tsql  
USE AdventureWorks2012  
GO  
  
SELECT Description, ProductDescriptionID  
FROM Production.ProductDescription  
WHERE CONTAINS (Description, '"top*"' )  
GO  
```  
  
 При выполнении этого запроса будут возвращены все фрагменты текста, соответствующие тексту, указанному перед звездочкой (*). Если текст и звездочка не ограничены двойными кавычками (например, `CONTAINS (DESCRIPTION, 'top*')`), звездочка не считается символом-шаблоном.  
  
 Если префиксный терм является фразой, каждый токен, составляющий фразу, считается отдельным префиксным термом. При выполнении такого запроса будут возвращены все строки со словами, начинающимися на префиксные термы. Например, если запрос включает префиксное выражение "light bread*", будут возвращены строки с текстом "light breaded", "lightly breaded" и "light bread", но не "Lightly toasted bread".  
  
###  <a name="Inflectional_Generation_Term"></a>Поиск словоформ конкретного слова (производное выражение)  
С помощью функций [CONTAINS](../../t-sql/queries/contains-transact-sql.md), [CONTAINSTABLE](../../relational-databases/system-functions/containstable-transact-sql.md), [FREETEXT](../../t-sql/queries/freetext-transact-sql.md)или [FREETEXTTABLE](../../relational-databases/system-functions/freetexttable-transact-sql.md) можно найти все грамматические формы глаголов и существительных (поиск словоформ) или синонимы указанного слова (поиск по тезаурусу).  
  
В следующем примере выполняется поиск любых форм слова «foot» («foot», «feet» и т. д.) в столбце `Comments` таблицы `ProductReview` в базе данных `AdventureWorks` .  
  
```tsql  
USE AdventureWorks2012  
GO  
  
SELECT Comments, ReviewerName  
FROM Production.ProductReview  
WHERE CONTAINS (Comments, 'FORMSOF(INFLECTIONAL, "foot")')  
GO  
```  
  
В полнотекстовом поиске используются *парадигматические модули*, которые позволяют найти глагол в различных временах и лицах или существительное в формах единственного или множественного числа. Дополнительные сведения о парадигматических модулях см. в разделе [Настройка и управление средством разбиения на слова и парадигматические модули для поиска](../../relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md).  
   
###  <a name="Weighted_Term"></a>Поиск слов или фраз с использованием взвешенных величин (взвешенное выражение)  
Для поиска слов и фраз можно использовать функцию [CONTAINSTABLE](../../relational-databases/system-functions/containstable-transact-sql.md) с взвешенными значениями. Вес, измеряемый числом от 0,0 до 1,0, обозначает степень важности каждого слова и фразы в наборе слов или фраз. Значение веса 0,0 является самым низким, значение 1,0 — самым высоким.  
  
В следующем примере показан запрос, выполняющий поиск (с использованием взвешенных значений) всех адресов заказчиков, в которых текст, начинающийся со строки «Bay», продолжается строкой «Street» или «View». В результатах более высокий ранг назначается тем строкам, в которых встречается больше заданных слов.  
  
```tsql  
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

##  <a name="Using_Boolean_Operators"></a>Операторы AND, OR и NOT
 
Функция CONTAINSTABLE и предикат CONTAINS используют одинаковые условия поиска. Они поддерживают объединение нескольких искомых терминов (с помощью логических операторов AND, OR и NOT) для выполнения логических операций. Например, оператор AND можно использовать для поиска строк, содержащих и "латте", и "пирожное с кремом". Например, с помощью оператора AND NOT можно находить строки, которые содержат слово «бублик», но не содержат «мак».  
  
Предикаты FREETEXT и FREETEXTTABLE, напротив, обрабатывают логические термины как слова, которые следует искать.  
  
 Сведения о сочетании предиката CONTAINS с другими предикатами, которые используют логические операторы AND, OR и NOT, см. в разделе [Условие поиска (Transact-SQL)](../../t-sql/queries/search-condition-transact-sql.md).  
  
### <a name="example"></a>Пример  
 Следующий пример использует предикат CONTAINS для поиска описаний, в которых идентификатор описания не равен 5, содержащих слова Aluminum и spindle. Условие поиска использует логический оператор AND. В следующем примере используется таблица ProductDescription базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].
  
```tsql  
USE AdventureWorks2012  
GO  
  
SELECT Description  
FROM Production.ProductDescription  
WHERE ProductDescriptionID <> 5 AND  
   CONTAINS(Description, 'aluminum AND spindle')  
GO  
```  
  
##  <a name="Additional_Considerations"></a>Дополнительные параметры запроса

 При написании полнотекстовых запросов можно также указать следующие параметры.
  
-   **Язык** с помощью параметра **LANGUAGE**. Многие выражения запроса в значительной степени зависят от поведения средства разбиения по словам. Чтобы гарантировать использование правильного средства разбиения по словам (и парадигматического модуля) и файла тезауруса, рекомендуется указывать параметр LANGUAGE. Дополнительные сведения см. в разделе [Выбор языка при создании полнотекстового индекса](../../relational-databases/search/choose-a-language-when-creating-a-full-text-index.md).  

-   **Учет регистра букв**. В запросах полнотекстового поиска не учитывается регистр букв. Однако в японском языке есть несколько фонетических орфографий, в которых концепция орфографической нормализации аналогична нечувствительности к регистру (например, японская азбука = нечувствительность). Этот тип орфографической нормализации не поддерживается.  

-   **Стоп-слова**. При определении полнотекстового запроса следует иметь в виду, что средство полнотекстового поиска не учитывает стоп-слова (также известные как пропускаемые слова), указанные в критерии поиска. Стоп-слова — это часто встречающиеся слова, которые не повышают эффективность поиска конкретного текста. Примерами могут служить слова «и», «или», «о» и «в». Стоп-слова перечислены в списке стоп-слов. Каждый полнотекстовый индекс связан с конкретным списком стоп-слов, который определяет, какие стоп-слова не указываются в запросе или в индексе во время индексирования. Дополнительные сведения см. в статье [Настройка стоп -слов и списков стоп-слов для полнотекстового поиска и управление ими](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md).  
  
-   **Тезаурус**. По умолчанию тезаурус используется в запросах FREETEXT и FREETEXTTABLE. Предикат CONTAINS и функция CONTAINSTABLE поддерживают необязательный аргумент THESAURUS. Дополнительные сведения см. в статье [Настройка файлов тезауруса для полнотекстового поиска и управление ими](configure-and-manage-thesaurus-files-for-full-text-search.md).
  
##  <a name="tokens"></a>Проверка результатов разметки

После применения сочетания заданного средства разбивки текста на слова, тезауруса и списка стоп-слов в запросе итоговый результат разметки можно просмотреть с помощью динамического административного представления **sys.dm_fts_parser**. Дополнительные сведения см. в разделе [sys.dm_fts_parser (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-fts-parser-transact-sql.md).  
  
## <a name="see-also"></a>См. также:  
 [CONTAINS (Transact-SQL)](../../t-sql/queries/contains-transact-sql.md)   
 [CONTAINSTABLE (Transact-SQL)](../../relational-databases/system-functions/containstable-transact-sql.md)   
 [FREETEXT (Transact-SQL)](../../t-sql/queries/freetext-transact-sql.md)   
 [FREETEXTTABLE (Transact-SQL)](../../relational-databases/system-functions/freetexttable-transact-sql.md)   
 [Создание запросов полнотекстового поиска (визуальные инструменты для баз данных)](http://msdn.microsoft.com/library/537fa556-390e-4c88-9b8e-679848d94abc)   
 [Улучшение производительности полнотекстовых запросов](../../relational-databases/search/improve-the-performance-of-full-text-queries.md)
 
