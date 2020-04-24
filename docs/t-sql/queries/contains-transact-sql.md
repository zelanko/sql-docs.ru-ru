---
title: CONTAINS (Transact-SQL) | Документы Майкрософт
description: Справочник по Transact-SQL для элемента языка CONTAINS. Используется для поиска слов или фраз в другом выражении.
ms.date: 08/23/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- CONTAINS_TSQL
- CONTAINS
dev_langs:
- TSQL
helpviewer_keywords:
- precise or fuzzy (less precise) matches [full-text search]
- CONTAINS predicate (Transact-SQL)
- conditions [SQL Server], CONTAINS
- fuzzy (less precise) word or phrase search [full-text search]
- word weighting values [full-text search]
- word searches [full-text search]
- weighted values [full-text search]
- LANGUAGE option
- word inflectionally generated from another [full-text search]
- NEAR option [full-text search]
- phrase searches [full-text search]
- word near another word search [full-text search]
- full-text search [SQL Server], searching on a property
- proximity searches [full-text search]
- less precise (fuzzy) searches [full-text search]
- property searching [SQL Server], searching on a property
- inflectional forms [full-text search]
- prefix searches [full-text search]
ms.assetid: 996c72fc-b1ab-4c96-bd12-946be9c18f84
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 98fc6b89cfe05b7c03d4d4211bea9387c5ef4e80
ms.sourcegitcommit: 8ffc23126609b1cbe2f6820f9a823c5850205372
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2020
ms.locfileid: "81635850"
---
# <a name="contains-transact-sql"></a>CONTAINS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]


  Производит поиск точных или нечетких (менее точных) совпадений с отдельными словами и фразами, слов на определенном расстоянии друг от друга или взвешенных совпадений [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. CONTAINS — предикат, используемый в предложении [WHERE](../../t-sql/queries/where-transact-sql.md) инструкции SELECT языка [!INCLUDE[tsql](../../includes/tsql-md.md)] для выполнения полнотекстового поиска [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] по столбцам полнотекстового индекса, содержащим символьные типы данных.  
  
 CONTAINS может производить поиск:  
  
-   слова или фразы;  
  
-   префикса слова или фразы;  
  
-   слова около другого слова;  
  
-   слова, флективно сформированного из другого (например, слово «drive» является флективной основой слов «drives», «drove», «driving» и «driven»);  
  
-   Слово, которое является синонимом другого слова согласно тезаурусу (например, у слова «металл» могут быть синонимы «алюминий» и «сталь»).  
  
 Сведения о формах и полнотекстовом поиске, поддерживаемых в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], см. в разделе [Запрос с полнотекстовым поиском](../../relational-databases/search/query-with-full-text-search.md).  
 
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```syntaxsql
CONTAINS (   
     {   
        column_name | ( column_list )   
      | *   
      | PROPERTY ( { column_name }, 'property_name' )    
     }   
     , '<contains_search_condition>'  
     [ , LANGUAGE language_term ]  
   )   
  
<contains_search_condition> ::=   
  {   
      <simple_term>   
    | <prefix_term>   
    | <generation_term>   
    | <generic_proximity_term>   
    | <custom_proximity_term>   
    | <weighted_term>   
    }   
  |   
    { ( <contains_search_condition> )   
        [ { <AND> | <AND NOT> | <OR> } ]   
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
   ( {   
        {   
          <simple_term>   
        | <prefix_term>   
        | <generation_term>   
        | <proximity_term>   
        }   
      [ WEIGHT ( weight_value ) ]   
      } [ ,...n ]   
   )   
  
<AND> ::=   
  { AND | & }  
  
<AND NOT> ::=   
  { AND NOT | &! }  
  
<OR> ::=   
  { OR | | }  
  
```  
  
## <a name="arguments"></a>Аргументы  
 *column_name*  
 Имя столбца с полнотекстовым индексом в таблице, указанной в предложении FROM. Столбцы должны иметь тип **char**, **varchar**, **nchar**, **nvarchar**, **text**, **ntext**, **image**, **xml**, **varbinary** или **varbinary(max)** .  
  
 *column_list*  
 Задает несколько столбцов, разделенных запятыми. *column_list* должен быть заключен в скобки. Если задан аргумент *language_term*, то у всех столбцов в *column_list* должен быть одинаковый язык.  
  
 \*  
 Указывает, что запрос выполняет поиск по заданному условию во всех столбцах таблицы, указанной в предложении FROM, для которых существуют полнотекстовые индексы. Столбцы в предложении CONTAINS должны принадлежать одной таблице, для которой существует полнотекстовый индекс. Если не определен аргумент *language_term*, язык для всех столбцов таблицы должен быть одинаковым.  
  
 PROPERTY ( *column_name* , '*property_name*')  
**Область применения**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] и более поздних версий. 
  
 Указывает свойство документа, по которому нужно выполнить поиск по заданному условию.  
  
> [!IMPORTANT]  
>  Чтобы запрос вернул строки, значение *property_name* должно быть указано в списке свойств поиска полнотекстового индекса, а сам полнотекстовый индекс должен содержать связанные со свойствами записи для *property_name*. Дополнительные сведения см. в статье [Поиск свойств документа с использованием списков свойств поиска](../../relational-databases/search/search-document-properties-with-search-property-lists.md).  
  
 LANGUAGE *language_term*  
 Язык, используемый для разбиения по словам, морфологического поиска, расширения и замены тезауруса, а также для удаления пропускаемых слов (или [стоп-слов](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)) в ходе запроса. Это необязательный параметр.  
  
 Если в одном столбце хранятся документы на различных языках в виде больших двоичных объектов, то код локали (LCID) заданного документа определяет, какой язык должен использоваться для индексирования его содержимого. Указание аргумента LANGUAGE *language_term* при запросе к такому столбцу может повысить вероятность хорошего соответствия.  
  
 Аргумент *language_term* при необходимости может быть указан в виде строки, целого числа или шестнадцатеричного значения, соответствующего коду языка. Если аргумент *language_term* задан, то соответствующий язык будет применяться ко всем элементам условия поиска. Если значение не указано, то используется язык полнотекстового поиска, заданный для столбца.  
  
 Если аргумент *language_term* указан как строка, он соответствует значению столбца **alias** в представлении совместимости [sys.languages](../../relational-databases/system-compatibility-views/sys-syslanguages-transact-sql.md) (Transact-SQ). Строка должна быть заключена в одиночные кавычки: '*language_term*'. Если значением аргумента *language_term* является целое число, оно представляет собой действительный код языка. Если значение *language_term* задано в шестнадцатеричной форме, то после символов "0x" должна следовать шестнадцатеричная запись кода языка. Шестнадцатеричное значение не может иметь более восьми знаков, включая начальные нули.  
  
 Если значение указано в формате двухбайтовой кодировки (DBCS), [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] преобразует его в Юникод.  
  
 Если указанный язык является недопустимым или связанные с ним ресурсы не установлены, то [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращает сообщение об ошибке. Для использования нейтральных языковых ресурсов следует указать 0x0 в качестве значения аргумента *language_term*.  
  
 \<*contains_search_condition*>  
 Текст, который необходимо найти в столбце *column_name*, и условия соответствия.  
  
*\<contains_search_condition>* имеет тип **nvarchar**. Если в качестве входных данных используется другой тип символьных данных, производится неявное преобразование. Типы данных больших значений nvarchar(max) и varchar(max) использовать нельзя. В следующем примере переменная `@SearchWord`, тип которой определен как `varchar(30)`, вызывает неявное преобразование в предикате `CONTAINS`.
  
```sql  
USE AdventureWorks2012;  
GO  
DECLARE @SearchWord varchar(30)  
SET @SearchWord ='performance'  
SELECT Description   
FROM Production.ProductDescription   
WHERE CONTAINS(Description, @SearchWord);  
```  
  
 Так как пробное сохранение параметров не работает с преобразованием, для улучшения производительности следует использовать тип **nvarchar**. В данном примере следует объявить переменную `@SearchWord` с типом `nvarchar(30)`.  
  
```sql  
USE AdventureWorks2012;  
GO  
DECLARE @SearchWord nvarchar(30)  
SET @SearchWord = N'performance'  
SELECT Description   
FROM Production.ProductDescription   
WHERE CONTAINS(Description, @SearchWord);  
```  
  
 Можно также воспользоваться указанием запроса OPTIMIZE FOR в случаях, когда формируется неоптимальный план.  
  
 *word*  
 Строка символов без пробелов и знаков препинания.  
  
 *phrase*  
 Одно или несколько слов с пробелами между ними.  
  
> [!NOTE]  
>  Некоторые языки, например в ряде азиатских стран, которые могут содержать фразы, состоящие из одного или нескольких слов без пробелов между ними.  
  
\<simple_term>  
Указывает соответствие для точного слова или фразы. Примерами допустимых простых выражений являются "база данных", данные и "Microsoft SQL Server". Фразы должны заключаться в двойные кавычки (""). Слова во фразе должны стоять в таком же порядке, как задано в аргументе *\<contains_search_condition>* , по мере их появления в столбце базы данных. Поиск символов в слове или фразе проводится без учета регистра. Пропускаемые слова (или [стоп-слова](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md), такие как "a", "and" или "the"), содержащиеся в столбцах полнотекстового индекса, не хранятся в полнотекстовом индексе. Если при поиске по одному слову используется слово из числа пропускаемых, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращает сообщение об ошибке, в котором говорится, что запрос содержит только пропускаемые слова. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] хранит стандартный список пропускаемых слов в каталоге \Mssql\Binn\FTERef каждого экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Знаки препинания пропускаются. Поэтому предикат `CONTAINS(testing, "computer failure")` соответствует строке «Where is my computer? Failure to find it would be expensive». Дополнительные сведения о поведении разбиения по словам см. в разделе [Настройка средств разбиения текста на слова и парадигматических модулей и управление ими для поиска](../../relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md).  
  
 \<prefix_term>  
 Указывает совпадение слов или фраз, начинающихся с указанного текста. Префиксные выражения должны заключаться в двойные кавычки (""), и необходимо добавлять звездочку (\*) перед закрывающей кавычкой, чтобы совпадал весь текст, начинающийся с простого выражения, заданного до звездочки. Предложение должно быть задано таким образом: `CONTAINS (column, '"text*"')`. Звездочка заменяет ноль, один или более символов (корневого слова или слов в слове или фразе). Если текст и звездочка не заключены в двойные кавычки и предикат выглядит как `CONTAINS (column, 'text*')`, то полнотекстовый поиск считает звездочку символом и ищет точное совпадение с `text*`. Полнотекстовое ядро не найдет слов со звездочкой (\*), так как средства разбиения по словам обычно пропускают такие символы.  
  
 Если параметр *\<prefix_term>* является фразой, то каждое содержащееся во фразе слово считается отдельным префиксом. Этому запросу, задающему префиксное выражение «local wine*», отвечают все строки с текстом «local winery», «locally wined and dined» и т. д.  
  
 \<generation_term>  
 Задает совпадение слов, если включенные простые выражения содержат варианты начального искомого слова.  
  
 INFLECTIONAL  
 Задает языковой парадигматический модуль, который будет использован для заданного простого выражения. Поведение парадигматического модуля определено правилами формирования основ для каждого конкретного языка. У нейтрального языка нет ассоциированного с ним парадигматического модуля. Язык столбцов, к которым выполняется запрос, используется для обращения к необходимому парадигматическому модулю. Если указан аргумент *language_term*, используется парадигматический модуль, соответствующий этому языку.  
  
 Заданный *\<simple_term>* в *\<generation_term>* не будет соответствовать одновременно существительным и глаголам.  
  
 THESAURUS  
 Указывает, что используется тезаурус, соответствующий языку полнотекстового поиска столбца или языку, заданному в запросе. Самый длинный шаблон или шаблоны аргумента *\<simple_term>* сравниваются с тезаурусом, и создаются дополнительные условия, которые можно использовать для расширения или замены начального шаблона. Если совпадений не найдено для всего аргумента *\<simple_term>* или для его части, несовпадающая часть обрабатывается как *simple_term*. Дополнительные сведения о тезаурусах полнотекстового поиска см. в разделе [Настройка файлов тезауруса для полнотекстового поиска и управление ими](../../relational-databases/search/configure-and-manage-thesaurus-files-for-full-text-search.md).  
  
 \<generic_proximity_term>  
 Указывает совпадение слов или фраз, которые должны находиться в документе, где выполняется поиск.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Рекомендуется использовать \<custom_proximity_term>.  
  
 NEAR | ~  
 Показывает, что для получения соответствия необходимо, чтобы в документе встречались слово или фраза, указанные с каждой стороны оператора NEAR или ~. Должно быть указано два поисковых выражения. Это условие поиска может быть либо одним словом, либо фразой, заключенной в двойные кавычки ("*phrase*").  
  
 Несколько выражений с учетом расположения можно объединять в цепочки, например `a NEAR b NEAR c` или `a ~ b ~ c`. Для получения соответствия необходимо, чтобы все выражения с учетом расположения, входящие в цепочку, находились в документе.  
  
 Например, `CONTAINS(*column_name*, 'fox NEAR chicken')` и `CONTAINSTABLE(*table_name*, *column_name*, 'fox ~ chicken')` вернут все документы в указанном столбце, которые содержат оба слова "fox" и "chicken". Кроме того, функция CONTAINSTABLE возвращает для каждого документа ранг, основанный на схожести слов «лиса» и «курица». Например, если документ содержит предложение «The fox ate the chicken», то оно будет иметь высокий рейтинг, поскольку эти выражения расположены ближе друг к другу, чем в других документах.  
  
 Дополнительные сведения о похожих словах см. в разделе [Поиск слов, близких к другим, с использованием оператора NEAR](../../relational-databases/search/search-for-words-close-to-another-word-with-near.md).  
  
 \<custom_proximity_term>  
**Область применения**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] и более поздних версий.
  
 Указывает совпадение слов или фраз и (необязательно) максимально допустимое расстояние между поисковыми выражениями. Можно также указать, что поисковые слова должны находиться точно в том порядке, в котором они заданы (\<match_order>).  
  
 Это условие поиска может быть либо одним словом, либо фразой, заключенной в двойные кавычки ("*phrase*"). Для возвращения документа в нем должно быть найдено каждое из указанных выражений. Необходимо указать не менее двух поисковых выражений. Максимальное количество поисковых выражений — 64.  
  
 По умолчанию настраиваемое выражение с учетом расположения возвращает строки, которые содержат указанные выражения, вне зависимости от расстояния между ними и порядка расположения. Например, для соответствия следующему запросу документ должен просто содержать `term1` и «`term3 term4`» в любом месте, в любом порядке:  
  
```  
CONTAINS(column_name, 'NEAR(term1,"term3 term4")')  
```  
  
 Необязательные параметры:  
  
 \<maximum_distance>  
 Указывает максимальное допустимое расстояние между поисковыми выражениями в начале и конце строки, при котором эта строка еще считается совпадением.  
  
 *integer*  
 Указывает положительное целое число от 0 до 4294967295. Это значение управляет тем, как много непоисковых выражений может находиться между первым и последним поисковыми выражениями, исключая все прочие указанные поисковые выражения.  
  
 Например, следующий запрос ищет `AA` и `BB` в любом порядке с максимальным расстоянием в пять выражений.  
  
```  
CONTAINS(column_name, 'NEAR((AA,BB),5)')  
```  
  
 Строка `AA one two three four five BB` будет найдена. В следующем примере запрос содержит три поисковых выражения — `AA`, `BB` и `CC` с максимальным расстоянием в пять слов:  
  
```  
CONTAINS(column_name, 'NEAR((AA,BB,CC),5)')  
```  
  
 Этот запрос найдет следующую строку, в которой общее расстояние составляет пять слов:  
  
 `BB   one two   CC   three four five A  A`  
  
 Обратите внимание, что внутренний поисковый запрос `CC` не учитывается при подсчете расстояния.  
  
 **MAX**  
 Возвращает строки, содержащие указанные поисковые выражения, вне зависимости от расстояния между ними. Это значение по умолчанию.  
  
 \<match_order>  
 Определяет, должны ли поисковые выражения располагаться в указанном порядке для возврата в поисковом запросе. При указании \<match_order> необходимо также указать \<maximum_distance>.  
  
 Параметр \<match_order> может иметь одно из следующих значений:  
  
 **TRUE**  
 Налагает ограничение, по которому выражения должны находиться в заданном порядке. Например, `NEAR(A,B)` найдет только `A ... B`.  
  
 **FALSE**  
 Указанный порядок не учитывается. Например, `NEAR(A,B)` найдет и `A ... B`, и `B ... A`.  
  
 Это значение по умолчанию.  
  
 Например, следующее выражение с учетом расположения ищет слова «`Monday`», «`Tuesday`» и «`Wednesday`» в заданном порядке вне зависимости от расстояния между ними:  
  
```  
CONTAINS(column_name, 'NEAR ((Monday, Tuesday, Wednesday), MAX, TRUE)')  
```  
  
 Дополнительные сведения об использовании похожих словах см. в разделе [Поиск слов близких к другим с использованием оператора NEAR](../../relational-databases/search/search-for-words-close-to-another-word-with-near.md).  
  
 \<weighted_term>  
 Указывает на то, что совпадающие строки (возвращенные запросом) соответствуют списку слов и фраз, каждому из которых при необходимости дано взвешенное значение.  
  
 ISABOUT  
 Указывает ключевое слово *\<weighted_term>* .  
  
 WEIGHT(*weight_value*)  
 Указывает взвешенное значение, которое может принимать значение от 0,0 до 1,0. Каждый компонент в *\<weighted_term>* может включать *weight_value*. *weight_value* — это способ изменения того, как различные части запроса влияют на ранжирующее значение, назначенное каждой строке, удовлетворяющей условию запроса. Параметр WEIGHT не влияет на результаты запросов CONTAINS, но влияет на ранг в запросах [CONTAINSTABLE](../../relational-databases/system-functions/containstable-transact-sql.md).  
  
> [!NOTE]  
>  В качестве десятичного разделителя всегда используется точка, независимо от кода локали операционной системы.  
  
 { AND | & } | { AND NOT | &! } | { OR | | }  
 Задает логическую операцию между двумя условиями поиска на вхождение.  
  
 { AND | & }  
 Указывает на то, что для совпадения оба условия поиска на вхождение должны быть удовлетворены. Символ амперсанда (&) может быть использован вместо ключевого слова AND для представления оператора AND.  
  
 { AND NOT | &! }  
 Указывает на то, что для совпадения второе условие поиска на вхождение не должно быть удовлетворено. Символ амперсанда с последующим восклицательным знаком (&!) может быть использован вместо ключевого слова AND NOT для представления оператора AND NOT.  
  
 { OR | | }  
 Указывает на то, что для совпадения любое из условий поиска на вхождение должно быть удовлетворено. Символ черты (|) может быть использован вместо ключевого слова OR для представления оператора OR.  
  
 Если аргумент *\<contains_search_condition>* содержит группы, заключенные в круглые скобки, эти группы вычисляются в первую очередь. После вычисления групп, заключенных в скобки, эти правила применяются при использовании следующих логических операторов с условиями поиска на вхождение.  
  
-   NOT применяется перед AND.  
  
-   NOT может стоять только после AND, как в AND NOT. Оператор OR NOT недопустим. NOT не может быть указано перед первым условием. Например, условие `CONTAINS (mycolumn, 'NOT "phrase_to_search_for" ' )` недопустимо.  
  
-   AND применяется перед OR.  
  
-   Логические операторы одного типа (AND, OR) являются ассоциативными, и поэтому они могут быть применены в любом порядке.  
  
 *n*  
 Заполнитель, указывающий, что могут быть заданы несколько условий поиска CONTAINS и входящих в них выражений.  
  
## <a name="general-remarks"></a>Общие замечания  
 Полнотекстовые предикаты и функции работают в одной таблице, что следует из наличия предиката FROM. Для поиска в нескольких таблицах используйте в предложении FROM соединенную таблицу, чтобы выполнять поиск в результирующем наборе, который получен в результате соединения нескольких таблиц.  
  
 Полнотекстовые предикаты не допускаются в [предложении OUTPUT](../../t-sql/queries/output-clause-transact-sql.md), если уровень совместимости базы данных установлен в значение 100.  
  
## <a name="querying-remote-servers"></a>Запрос к удаленному серверу  
 Четырехкомпонентное имя может использоваться в предикате CONTAINS или [FREETEXT](../../t-sql/queries/freetext-transact-sql.md) для запроса по столбцам полнотекстового индекса целевых таблиц на связанном сервере. Чтобы подготовить удаленный сервер к приему полнотекстовых запросов, сначала необходимо создать полнотекстовые индексы для целевых таблиц и столбцов на удаленном сервере, а затем добавить удаленный сервер в качестве связанного сервера.  
  
## <a name="comparison-of-like-to-full-text-search"></a>Сравнение предиката LIKE с полнотекстовым поиском  
 В отличие от полнотекстового поиска предикат [LIKE](../../t-sql/language-elements/like-transact-sql.md)[!INCLUDE[tsql](../../includes/tsql-md.md)] работает только с комбинациями символов. Кроме того, предикат LIKE нельзя использовать в запросах к форматированным двоичным данным. Более того, запрос с предикатом LIKE к большому количеству неструктурированных текстовых данных выполняется гораздо медленнее, чем эквивалентный полнотекстовый запрос к тем же данным. Выполнение запроса LIKE к миллионам строк текстовых данных может занять несколько минут, в то время как полнотекстовый запрос к тем же данным занимает всего несколько секунд или даже меньше, в зависимости от количества и размера возвращаемых строк. Еще одно соображение состоит в том, что LIKE выполняет лишь простое сканирование по шаблону для всей таблицы. В то же время полнотекстовый запрос производится с учетом языка, применением определенных преобразований как при индексировании, так и при выполнении запроса. Например, выполняется фильтрация стоп-слов, расширение тезауруса и добавление флексий. Такие преобразования улучшают показатели повторного вызова и конечный рейтинг результатов полнотекстовых запросов.  
  
## <a name="querying-multiple-columns-full-text-search"></a>Запросы к нескольким столбцам (компонент Full-Text Search)  
 Можно выполнить запрос к нескольким столбцам, задав список столбцов, в которых будет проводиться поиск. Столбцы должны быть из той же таблицы.  
  
 Например, следующий запрос CONTAINS ищет термин `Red` в столбцах `Name` и `Color` таблицы `Production.Product` в образце базы данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].  
  
```sql  
Use AdventureWorks2012;  
GO  
SELECT Name, Color   
FROM Production.Product  
WHERE CONTAINS((Name, Color), 'Red');  
```  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-contains-with-simple_term"></a>A. Использование CONTAINS с \<simple_term>  
 В следующем примере выполняется поиск всех продуктов с ценой `$80.99` , которые содержат слово `Mountain`.  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT Name, ListPrice  
FROM Production.Product  
WHERE ListPrice = 80.99  
   AND CONTAINS(Name, 'Mountain');  
GO  
```  
  
### <a name="b-using-contains-and-phrase-with-simple_term"></a>Б. Использование CONTAINS и фразы с \<simple_term>  
 В следующем примере возвращаются все товары, которые содержат фразу `Mountain` или `Road`.  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT Name  
FROM Production.Product  
WHERE CONTAINS(Name, ' Mountain OR Road ')  
GO  
```  
  
### <a name="c-using-contains-with-prefix_term"></a>В. Использование CONTAINS с \<prefix_term>  
 Следующий пример возвращает все имена товаров, содержащие по крайней мере одно слово, начинающееся с префикса «chain» в столбце `Name`.  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT Name  
FROM Production.Product  
WHERE CONTAINS(Name, ' "Chain*" ');  
GO  
```  
  
### <a name="d-using-contains-and-or-with-prefix_term"></a>Г. Использование CONTAINS и OR с \<prefix_term>  
 В следующем примере возвращаются все описания категорий, которые содержат строки с префиксами `chain` или `full`.  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT Name  
FROM Production.Product  
WHERE CONTAINS(Name, '"chain*" OR "full*"');  
GO  
```  
  
### <a name="e-using-contains-with-proximity_term"></a>Д. Использование CONTAINS с \<proximity_term>  
  
**Область применения**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] и более поздних версий. 
  
 В следующем примере производится поиск в таблице `Production.ProductReview` всех комментариев, содержащих слово `bike`, на расстоянии до 10 выражений от слова `control` и в заданном порядке (то есть слово "`bike`" должно предшествовать слову "`control`").  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT Comments  
FROM Production.ProductReview  
WHERE CONTAINS(Comments , 'NEAR((bike,control), 10, TRUE)');  
GO  
```  
  
### <a name="f-using-contains-with-generation_term"></a>Е. Использование CONTAINS с \<generation_term>  
 В следующем примере выполняется поиск всех товаров с формами слова `ride`: riding, ridden и т. д.  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT Description  
FROM Production.ProductDescription  
WHERE CONTAINS(Description, ' FORMSOF (INFLECTIONAL, ride) ');  
GO  
```  
  
### <a name="g-using-contains-with-weighted_term"></a>Ж. Использование CONTAINS с \<weighted_term>  
 В следующем примере выполняется поиск всех названий продуктов, содержащих слова `performance`, `comfortable` или `smooth`, при этом для каждого слова задается определенный вес.  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT Description  
FROM Production.ProductDescription  
WHERE CONTAINS(Description, 'ISABOUT (performance weight (.8),   
comfortable weight (.4), smooth weight (.2) )' );  
GO  
```  
  
### <a name="h-using-contains-with-variables"></a>З. Использование CONTAINS с переменными  
 Нижеприведенные примеры используют переменную вместо конкретного термина для поиска.  
  
```sql  
USE AdventureWorks2012;  
GO  
DECLARE @SearchWord nvarchar(30)  
SET @SearchWord = N'Performance'  
SELECT Description   
FROM Production.ProductDescription   
WHERE CONTAINS(Description, @SearchWord);  
GO  
```  
  
### <a name="i-using-contains-with-a-logical-operator-and"></a>И. Использование CONTAINS с логическим оператором (AND)  
 В следующем примере используется таблица ProductDescription базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] . Запрос использует предикат CONTAINS для поиска описаний, в которых идентификатор описания не равен 5, а описание содержит слова `Aluminum` и `spindle`. Условие поиска использует логический оператор AND.  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT Description  
FROM Production.ProductDescription  
WHERE ProductDescriptionID <> 5 AND  
   CONTAINS(Description, 'Aluminum AND spindle');  
GO  
```  
  
### <a name="j-using-contains-to-verify-a-row-insertion"></a>К. Использование CONTAINS для проверки вставки строки  
 В следующем примере предикат CONTAINS используется во вложенном запросе SELECT. Используя базу данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)], запрос получает значение комментария из всех комментариев в таблице ProductReview для конкретного велосипеда. Условие поиска использует логический оператор AND.  
  
```sql  
USE AdventureWorks2012;  
GO  
INSERT INTO Production.ProductReview   
  (ProductID, ReviewerName, EmailAddress, Rating, Comments)   
VALUES  
  (780, 'John Smith', 'john@fourthcoffee.com', 5,   
'The Mountain-200 Silver from AdventureWorks2008 Cycles meets and exceeds expectations. I enjoyed the smooth ride down the roads of Redmond');  
  
-- Given the full-text catalog for these tables is Adv_ft_ctlg,   
-- with change_tracking on so that the full-text indexes are updated automatically.  
WAITFOR DELAY '00:00:30';     
-- Wait 30 seconds to make sure that the full-text index gets updated.  
  
SELECT r.Comments, p.Name  
FROM Production.ProductReview AS r  
JOIN Production.Product AS p   
    ON r.ProductID = p.ProductID  
    AND r.ProductID = (SELECT ProductID  
FROM Production.ProductReview  
WHERE CONTAINS (Comments,   
    ' AdventureWorks2008 AND   
    Redmond AND   
    "Mountain-200 Silver" '));  
GO  
```  
  
### <a name="k-querying-on-a-document-property"></a>Л. Запрос по свойству документа  
  
**Область применения**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] и более поздних версий. 
  
 Следующий запрос выполняет поиск по индексированному свойству `Title` в столбце `Document` таблицы `Production.Document`. Запрос возвращает только те документы, у которых свойство `Title` содержит строку `Maintenance` или `Repair`.  
  
> [!NOTE]  
>  Поиск по свойству возвратит строки только при условии, что фильтры, производящие синтаксический анализ столбца во время индексирования, извлекут указанное свойство. Кроме того, полнотекстовый индекс указанной таблицы необходимо настроить таким образом, чтобы он включал это свойство. Дополнительные сведения см. в статье [Поиск свойств документа с использованием списков свойств поиска](../../relational-databases/search/search-document-properties-with-search-property-lists.md).  
  
```sql  
Use AdventureWorks2012;  
GO  
SELECT Document 
FROM Production.Document  
WHERE CONTAINS(PROPERTY(Document,'Title'), 'Maintenance OR Repair');  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Приступая к работе с компонентом Full-Text Search](../../relational-databases/search/get-started-with-full-text-search.md)   
 [Создание полнотекстовых каталогов и управление ими](../../relational-databases/search/create-and-manage-full-text-catalogs.md)   
 [CREATE FULLTEXT CATALOG (Transact-SQL)](../../t-sql/statements/create-fulltext-catalog-transact-sql.md)   
 [CREATE FULLTEXT INDEX (Transact-SQL)](../../t-sql/statements/create-fulltext-index-transact-sql.md)   
 [Создание и управление полнотекстовыми индексами](../../relational-databases/search/create-and-manage-full-text-indexes.md)   
 [Запрос с полнотекстовым поиском](../../relational-databases/search/query-with-full-text-search.md)   
 [CONTAINSTABLE (Transact-SQL)](../../relational-databases/system-functions/containstable-transact-sql.md)   
 [FREETEXT (Transact-SQL)](../../t-sql/queries/freetext-transact-sql.md)   
 [FREETEXTTABLE (Transact-SQL)](../../relational-databases/system-functions/freetexttable-transact-sql.md)   
 [Запрос с полнотекстовым поиском](../../relational-databases/search/query-with-full-text-search.md)   
 [Компонент Full-text Search](../../relational-databases/search/full-text-search.md)   
 [Создание запросов полнотекстового поиска (визуальные инструменты для баз данных)](https://msdn.microsoft.com/library/537fa556-390e-4c88-9b8e-679848d94abc)   
 [WHERE (Transact-SQL)](../../t-sql/queries/where-transact-sql.md)   
 [Поиск свойств документа с помощью списков свойств поиска](../../relational-databases/search/search-document-properties-with-search-property-lists.md)  
  
  
