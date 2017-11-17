---
title: "FOR, предложение (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 08/09/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|queries
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- FOR
- FOR CLAUSE
- FOR_TSQL
- FOR_CLAUSE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- XML option [SQL Server]
- BROWSE option
- FOR clause [Transact-SQL]
ms.assetid: 08a6f084-8f73-4f2a-bae4-3c7513dc99b9
caps.latest.revision: 54
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: f092e78608e8fa2b44061056ef4e5b9e7e1649a7
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="select---for-clause-transact-sql"></a>SELECT - предложение FOR (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Предложение FOR используется для указания одного из следующих параметров для результатов запроса.  
  
-   Разрешить обновление при просмотре результатов запроса в курсора в режиме обзора, указав **FOR BROWSE**.  
  
-   Форматирование результатов запроса в формате XML, указав **FOR XML**.  
  
-   Форматирование результатов запроса как JSON, указав **FOR JSON**.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
[ FOR { BROWSE | <XML> | <JSON>} ]  
  
<XML> ::=  
XML   
{   
    { RAW [ ( 'ElementName' ) ] | AUTO }   
    [   
        <CommonDirectivesForXML>   
        [ , { XMLDATA | XMLSCHEMA [ ( 'TargetNameSpaceURI' ) ] } ]   
        [ , ELEMENTS [ XSINIL | ABSENT ]   
    ]  
  | EXPLICIT   
    [   
        <CommonDirectivesForXML>   
        [ , XMLDATA ]   
    ]  
  | PATH [ ( 'ElementName' ) ]   
    [  
        <CommonDirectivesForXML>   
        [ , ELEMENTS [ XSINIL | ABSENT ] ]  
    ]  
}   
  
<CommonDirectivesForXML> ::=   
[ , BINARY BASE64 ]  
[ , TYPE ]  
[ , ROOT [ ( 'RootName' ) ] ]  
  
<JSON> ::=  
JSON   
{   
    { AUTO | PATH }   
    [   
        [ , ROOT [ ( 'RootName' ) ] ]  
        [ , INCLUDE_NULL_VALUES ]  
        [ , WITHOUT_ARRAY_WRAPPER ]  
    ]  
  
}  
```  
  
## <a name="for-browse"></a>FOR BROWSE  
 BROWSE  
 Активирует возможность обновления данных во время их просмотра с помощью курсора в режиме обзора DB-Library. Таблицу можно просмотреть внутри приложения, если таблица содержит **timestamp** столбец, таблица имеет уникальный индекс, а параметр FOR BROWSE — в конце инструкции SELECT, отсылаемой экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Нельзя использовать \<lock_hint > HOLDLOCK в инструкции SELECT, включающей параметр FOR BROWSE.
  
 Параметр FOR BROWSE не может быть использован в инструкциях SELECT, соединенных оператором UNION.  
  
> [!NOTE]  
>  Если ключевые столбцы уникального индекса таблицы могут принимать неопределенные значения, а таблица находится внутри внешнего соединения, индексы в режиме обзора не поддерживаются.  
  
 Режим просмотра позволяет просматривать строки в таблице [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и обновлять данные в таблице по одной строке одновременно. Чтобы получить доступ к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таблицы в приложение в режиме просмотра, необходимо использовать один из следующих параметров:  
  
-   Инструкция SELECT, которая используется для доступа к данным из вашего [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таблица должна оканчиваться ключевыми словами **FOR BROWSE**. При включении **FOR BROWSE** параметр для использования режима просмотра, создаются временные таблицы.  
  
-   Необходимо выполнить следующую [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкцию, чтобы включить режим просмотра при помощи **NO_BROWSETABLE** параметр:  
  
    ```  
    SET NO_BROWSETABLE ON  
    ```  
  
     При включении **NO_BROWSETABLE** все инструкции SELECT действуют так, словно **FOR BROWSE** к инструкциям был добавлен параметр. Тем не менее **NO_BROWSETABLE** не создает временные таблицы, **FOR BROWSE** параметр обычно используется для отправки результатов в приложение.  
  
 При попытке доступа к данным из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таблицы в режиме просмотра с помощью запроса SELECT, содержащего инструкцию внешнего соединения, и если уникальный индекс определен для таблицы, которая присутствует во внутренней части инструкции внешнего соединения, режим просмотра не sup порт уникального индекса. В режиме просмотра уникальный индекс поддерживается, только если все ключевые столбцы уникального индекса могут принимать значения NULL. Уникальный индекс не поддерживается в режиме просмотра, если следующие условия являются истинными.  
  
-   При попытке доступа к данным из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таблицы в режиме просмотра с помощью запроса SELECT, содержащего инструкцию внешнего соединения.  
  
-   Уникальный индекс определен на таблице, которая присутствует во внутренней части инструкции внешнего соединения.  
  
 Чтобы воспроизвести это поведение в режиме просмотра, выполните следующие шаги.  
  
1.  В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] создайте базу данных с именем SampleDB.  
  
2.  В базе данных SampleDB создайте таблицы tleft и tright так, чтобы каждая содержала один столбец с именем c1. Определите уникальный индекс на столбце c1 в таблице tleft и предусмотрите, чтобы этот столбец принимал значения NULL. Чтобы это сделать, выполните в соответствующем окне запроса следующие инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)]:  
  
    ```  
    CREATE TABLE tleft(c1 INT NULL UNIQUE) ;  
    GO   
    CREATE TABLE tright(c1 INT NULL) ;  
    GO  
    ```  
  
3.  Вставьте несколько значений в таблицу tleft и таблицу tright. Обязательно вставьте значение NULL в таблицу tleft. Чтобы это сделать, выполните в окне запроса следующие инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)]:  
  
    ```  
    INSERT INTO tleft VALUES(2) ;  
    INSERT INTO tleft VALUES(NULL) ;  
    INSERT INTO tright VALUES(1) ;  
    INSERT INTO tright VALUES(3) ;  
    INSERT INTO tright VALUES(NULL) ;  
    GO  
    ```  
  
4.  Включите **NO_BROWSETABLE** параметр. Чтобы это сделать, выполните в окне запроса следующие инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)]:  
  
    ```  
    SET NO_BROWSETABLE ON ;  
    GO  
    ```  
  
5.  Получите доступ к данным в таблице tleft и таблице tright с помощью инструкции внешнего соединения в запросе SELECT. Убедитесь, что таблица tleft находится во внутренней части инструкции внешнего соединения. Чтобы это сделать, выполните в окне запроса следующие инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)]:  
  
    ```  
    SELECT tleft.c1   
    FROM tleft   
    RIGHT JOIN tright   
    ON tleft.c1 = tright.c1   
    WHERE tright.c1 <> 2 ;  
  
    ```  
  
     Обратите внимание на следующие выходные данные на панели «Результаты»:  
  
     c1  
  
     ---\-  
  
     NULL  
  
     NULL  
  
 После выполнения запроса SELECT для получения доступа к таблицам в режиме просмотра результирующий набор запроса SELECT содержит два значения NULL для столбца c1 в таблице tleft, поскольку таково определение инструкции правого внешнего соединения. Поэтому в результирующем наборе невозможно различить значения NULL, полученные из таблицы, и значения NULL, добавленные инструкцией правого внешнего соединения. Могут быть получены неверные результаты, если необходимо пропустить значения NULL из результирующего набора.  
  
> [!NOTE]  
>  Если столбцы, которые включены в уникальный индекс, не допускают значения NULL, это значит, что все значения NULL в результирующем наборе были добавлены инструкцией правого внешнего соединения.  
  
## <a name="for-xml"></a>FOR XML  
 XML  
 Задает возврат результатов запроса в виде XML-документа. Необходимо указать один из следующих режимов XML: RAW, AUTO, EXPLICIT. Дополнительные сведения об XML-данных и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], в разделе [FOR XML &#40; SQL Server &#41; ](../../relational-databases/xml/for-xml-sql-server.md).  
  
 НЕОБРАБОТАННЫЙ [ **("***ElementName***")** ]  
 Берет результаты запроса и преобразует каждую строку в результирующем наборе в элемент XML с универсальным идентификатором \<строк / > в качестве тега элемента. Дополнительно можно задать имя для элемента строки. Результирующий XML вывода использует указанный *ElementName* качестве элемента, сформированного для каждой строки. Дополнительные сведения см. в разделе [использование с RAW Mode для FOR XML](../../relational-databases/xml/use-raw-mode-with-for-xml.md) и [использование с RAW Mode для FOR XML](../../relational-databases/xml/use-raw-mode-with-for-xml.md).  
  
 AUTO  
 Возвращает результаты запроса в виде простого вложенного дерева XML. Каждая таблица предложения FROM, для которой в предложении SELECT приведен хотя бы один столбец, отображается как элемент XML. Столбцы, перечисленные в предложении SELECT, сопоставлены с соответствующими атрибутами элемента. Дополнительные сведения см. в статье [Использование с AUTO Mode для FOR XML](../../relational-databases/xml/use-auto-mode-with-for-xml.md).  
  
 EXPLICIT  
 Указывает, что форма конечного дерева XML определена явно. При использовании данного режима запросы должны записываться таким образом, чтобы дополнительные сведения о вложениях могли быть заданы явно. Дополнительные сведения см. в статье [Использование с EXPLICIT Mode для FOR XML](../../relational-databases/xml/use-explicit-mode-with-for-xml.md).  
  
 XMLDATA  
 Возвращает встроенную XDR-схему, не добавляя корневой элемент к результату. При задании параметра XMLDATA XDR-схема добавляется к документу.  
  
> [!IMPORTANT]  
>  Директива XMLDATA является устаревшей. В режимах RAW и AUTO следует использовать создание XSD-схем. В режиме EXPLICIT для директивы XMLDATA замены нет. [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 XMLSCHEMA [ **("***TargetNameSpaceURI***")** ]  
 Возвращает встроенную XSD-схему. При задании указанной директивы, возвращающей заданное пространство имен схемы, дополнительно можно задать URI целевого пространства имен. Дополнительные сведения см. в разделе [Создание встроенных схем XSD](../../relational-databases/xml/generate-an-inline-xsd-schema.md).  
  
 ELEMENTS  
 Задает возврат столбцов в виде вложенных элементов. В противном случае они сопоставляются с XML-атрибутами. Данный параметр поддерживается только в режимах RAW, AUTO и PATH. Дополнительные сведения см. в статье [Использование с RAW Mode для FOR XML](../../relational-databases/xml/use-raw-mode-with-for-xml.md).  
  
 XSINIL  
 Указывает, что элемент с **xsi: nil** атрибута **True** создаваться для столбцов со значением NULL. Данный параметр может быть указан только в директиве ELEMENTS. Дополнительные сведения см. в разделе [создание элементов для значений NULL с помощью параметра XSINIL](../../relational-databases/xml/generate-elements-for-null-values-with-the-xsinil-parameter.md).  
  
 ABSENT  
 Указывает, что соответствующие XML-элементы для столбцов со значениями NULL к XML-результату не добавляются. Указывайте данный параметр только с директивой ELEMENTS.  
  
 ПУТЬ [ **("***ElementName***")** ]  
 Приводит к возникновению ошибки \<строки > элемент программы-оболочки для каждой строки в результирующем наборе. При необходимости можно указать имя элемента для \<строки > элемент программы-оболочки. Если указан пустой строкой, например FOR XML PATH (**''**)), упаковщик элементов не создается. Использование директивы PATH дает более простой способ написания запросов, чем написание запросов с помощью директивы EXPLICIT. Дополнительные сведения см. в статье [Использование с PATH Mode для FOR XML](../../relational-databases/xml/use-path-mode-with-for-xml.md).  
  
 BINARY BASE64  
 Задает возврат двоичных данных запросом в двоичном зашифрованном формате base64. При извлечении двоичных данных с использованием режимов RAW и EXPLICIT необходимо указывать этот параметр. В режиме AUTO это указывается по умолчанию.  
  
 TYPE  
 Указывает, что запрос возвращает результаты в виде **xml** типа. Дополнительные сведения см. в статье [TYPE Directive in FOR XML Queries](../../relational-databases/xml/type-directive-in-for-xml-queries.md).  
  
 КОРНЕВОЙ [ **("***RootName***")** ]  
 Задает добавление единичного элемента высшего уровня к результирующему XML-документу. Дополнительно можно указать имя корневого элемента, который необходимо сформировать. Если имя корневого не указан, значение по умолчанию \<корневой > элемент добавляется.  
  
 Дополнительные сведения см. в разделе [FOR XML &#40; SQL Server &#41; ](../../relational-databases/xml/for-xml-sql-server.md).  
  
 **НАПРИМЕР, XML**  
  
 В данном примере задается параметр `FOR XML AUTO` с параметрами `TYPE` и `XMLSCHEMA`. Из-за `TYPE` параметр, результирующий набор возвращается клиенту как **xml** типа. Параметр `XMLSCHEMA` определяет встроенную XSD-схему, включаемую в возвращаемые XML-данные, а параметр `ELEMENTS` указывает, что результаты в формате XML основываются на элементах.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT p.BusinessEntityID, FirstName, LastName, PhoneNumber AS Phone  
FROM Person.Person AS p  
JOIN Person.PersonPhone AS pph ON p.BusinessEntityID  = pph.BusinessEntityID  
WHERE LastName LIKE 'G%'  
ORDER BY LastName, FirstName   
FOR XML AUTO, TYPE, XMLSCHEMA, ELEMENTS XSINIL;  
```  
  
## <a name="for-json"></a>FOR JSON  
 JSON  
 Укажите для JSON, чтобы вернуть результаты запроса в формате текста JSON. Также необходимо указать один из следующих режимов JSON: AUTO или путь. Дополнительные сведения о **FOR JSON** предложение, в разделе [форматирование результатов запроса как JSON с помощью FOR JSON &#40; SQL Server &#41; ](../../relational-databases/json/format-query-results-as-json-with-for-json-sql-server.md).  
  
 AUTO  
 Формат выходных данных автоматически JSON на основе структуры **ВЫБЕРИТЕ** инструкции  
            указав **FOR JSON AUTO**. Дополнительные сведения и примеры см. в разделе [Автоматическое форматирование выходных данных JSON в режиме AUTO (SQL Server)](../../relational-databases/json/format-json-output-automatically-with-auto-mode-sql-server.md).  
  
 PATH  
 Получить полный контроль над форматом выходных данных JSON, указав   
            **FOR JSON PATH**. Режим**PATH** позволяет создавать объекты-оболочки и вкладывать сложные свойства друг в друга. Дополнительные сведения и примеры см. в разделе [Форматирование вложенных выходных данных JSON в режиме PATH (SQL Server)](../../relational-databases/json/format-nested-json-output-with-path-mode-sql-server.md).  
  
 INCLUDE_NULL_VALUES  
 Для включения значений null в выходные данные JSON, указав **INCLUDE_NULL_VALUES** вариант с **FOR JSON** предложения. Если не указать этот параметр, выходные данные не будут включены свойства JSON для значений null в результатах запроса. Дополнительные сведения и примеры см. в разделе [включать значения Null в выходные данные JSON использование параметра INCLUDE_NULL_VALUES &#40; SQL Server &#41; ](../../relational-databases/json/include-null-values-in-json-include-null-values-option.md).  
  
 КОРНЕВОЙ [ **("***RootName***")** ]  
 Добавить один элемент верхнего уровня в выходные данные JSON, указав **КОРНЕВОЙ** вариант с **FOR JSON** предложения. Если не указать параметр **ROOT** , выходные данные JSON не будут содержать корневой элемент. Дополнительные сведения и примеры см. в разделе [Добавление корневого узла к выходным данным JSON с параметром ROOT &#40; SQL Server &#41; ](../../relational-databases/json/add-a-root-node-to-json-output-with-the-root-option-sql-server.md).  
  
 WITHOUT_ARRAY_WRAPPER  
 Удаление квадратных скобок, в которые выходные данные JSON по умолчанию, указав **WITHOUT_ARRAY_WRAPPER** вариант с **FOR JSON** предложения. Если не указать этот параметр, выходные данные JSON будут заключены в квадратные скобки. Используйте **WITHOUT_ARRAY_WRAPPER** параметр, чтобы создать единый объект JSON в качестве выходных данных.  Дополнительные сведения см. в разделе [Удаление квадратных скобок из выходных данных JSON с помощью параметра WITHOUT_ARRAY_WRAPPER (SQL Server)](../../relational-databases/json/remove-square-brackets-from-json-without-array-wrapper-option.md).  
  
 Дополнительные сведения см. в разделе [Форматирование результатов запроса как JSON с помощью предложения FOR JSON (SQL Server)](../../relational-databases/json/format-query-results-as-json-with-for-json-sql-server.md).  
  
## <a name="see-also"></a>См. также:  
 [SELECT (Transact-SQL)](../../t-sql/queries/select-transact-sql.md)  
  
  

