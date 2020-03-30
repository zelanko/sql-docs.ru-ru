---
title: Предложение FOR (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 01/08/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
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
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: ad3852f0bb935371fd141cc4ceb98f90c7aa9c19
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "67904356"
---
# <a name="select---for-clause-transact-sql"></a>SELECT - FOR, предложение (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Предложение FOR используется для указания одного из следующих параметров для результатов запроса.
  
-   Разрешение обновлений при просмотре результатов запроса в курсоре режима просмотра с помощью **FOR BROWSE**.  
  
-   Форматирование результатов запроса в формате XML с помощью **FOR XML**.  
  
-   Форматирование результатов запроса в формате JSON с помощью **FOR JSON**.  

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
 Активирует возможность обновления данных во время их просмотра с помощью курсора в режиме обзора DB-Library. Таблицу можно просмотреть внутри приложения, если в таблице содержится столбец **timestamp**, таблице присвоен уникальный индекс или в конце инструкции SELECT, отсылаемой экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], имеется параметр FOR BROWSE.  
  
> [!NOTE]
> Нельзя использовать синтаксис \<lock_hint> HOLDLOCK для инструкции SELECT, включающей в себя параметр FOR BROWSE.
  
 Параметр FOR BROWSE не может быть использован в инструкциях SELECT, соединенных оператором UNION.  
  
> [!NOTE]
> Если ключевые столбцы уникального индекса таблицы могут принимать неопределенные значения, а таблица находится внутри внешнего соединения, индексы в режиме обзора не поддерживаются.  
  
 Режим просмотра позволяет просматривать строки в таблице [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и обновлять данные в таблице по одной строке одновременно. Чтобы получить доступ к таблице [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в приложении в режиме просмотра, необходимо использовать один из следующих вариантов.  
  
-   Инструкция SELECT, применяемая для получения доступа к данным таблицы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], должна оканчиваться ключевыми словами **FOR BROWSE**. Если для использования режима просмотра включен параметр **FOR BROWSE**, создаются временные таблицы.  
  
-   Необходимо выполнить следующую инструкцию [!INCLUDE[tsql](../../includes/tsql-md.md)], чтобы включить режим просмотра с параметром **NO_BROWSETABLE**:  
  
    ```sql
    SET NO_BROWSETABLE ON  
    ```  
  
     После включения параметра **NO_BROWSETABLE** все инструкции SELECT действуют так, как если бы к инструкциям был добавлен параметр **FOR BROWSE**. Однако параметр **NO_BROWSETABLE** не создает временные таблицы, которые обычно используются параметром **FOR BROWSE**, чтобы передать результаты в приложение.  
  
 Если предпринимается попытка получить доступ к данным таблиц [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в режиме просмотра с помощью запроса SELECT, содержащего инструкцию внешнего соединения, и если определен уникальный индекс в таблице, которая присутствует во внутренней части инструкции внешнего соединения, в режиме просмотра не поддерживается уникальный индекс. В режиме просмотра уникальный индекс поддерживается, только если все ключевые столбцы уникального индекса могут принимать значения NULL. Уникальный индекс не поддерживается в режиме просмотра, если следующие условия являются истинными.  
  
-   Предпринимается попытка получить доступ к данным таблиц [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в режиме просмотра с использованием запроса SELECT, содержащего инструкцию внешнего соединения.  
  
-   Уникальный индекс определен на таблице, которая присутствует во внутренней части инструкции внешнего соединения.  
  
 Чтобы воспроизвести это поведение в режиме просмотра, выполните следующие шаги.  
  
1.  В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] создайте базу данных с именем SampleDB.  
  
2.  В базе данных SampleDB создайте таблицы tleft и tright так, чтобы каждая содержала один столбец с именем c1. Определите уникальный индекс на столбце c1 в таблице tleft и предусмотрите, чтобы этот столбец принимал значения NULL. Чтобы это сделать, выполните в соответствующем окне запроса следующие инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)]:  
  
    ```sql
    CREATE TABLE tleft(c1 INT NULL UNIQUE) ;  
    GO   
    CREATE TABLE tright(c1 INT NULL) ;  
    GO  
    ```  
  
3.  Вставьте несколько значений в таблицу tleft и таблицу tright. Обязательно вставьте значение NULL в таблицу tleft. Чтобы это сделать, выполните в окне запроса следующие инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)]:  
  
    ```sql
    INSERT INTO tleft VALUES(2) ;  
    INSERT INTO tleft VALUES(NULL) ;  
    INSERT INTO tright VALUES(1) ;  
    INSERT INTO tright VALUES(3) ;  
    INSERT INTO tright VALUES(NULL) ;  
    GO  
    ```  
  
4.  Включите параметр **NO_BROWSETABLE**. Чтобы это сделать, выполните в окне запроса следующие инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)]:  
  
    ```sql
    SET NO_BROWSETABLE ON ;  
    GO  
    ```  
  
5.  Получите доступ к данным в таблице tleft и таблице tright с помощью инструкции внешнего соединения в запросе SELECT. Убедитесь, что таблица tleft находится во внутренней части инструкции внешнего соединения. Чтобы это сделать, выполните в окне запроса следующие инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)]:  
  
    ```sql
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
> Если столбцы, которые включены в уникальный индекс, не допускают значения NULL, это значит, что все значения NULL в результирующем наборе были добавлены инструкцией правого внешнего соединения.  
  
## <a name="for-xml"></a>FOR XML

 XML  
 Задает возврат результатов запроса в виде XML-документа. Должен быть задан один из следующих режимов XML: RAW, AUTO, EXPLICIT. Дополнительные сведения о данных XML и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] см. в статье [FOR XML (SQL Server)](../../relational-databases/xml/for-xml-sql-server.md).  
  
 RAW [ **('** _имя_элемента_ **')** ]  
 Получает результат запроса и преобразует каждую строку результирующего набора в элемент XML, для которого в качестве тега используется общий идентификатор \<row />. Дополнительно можно задать имя для элемента строки. Полученный в результате выходной XML-файл будет использовать указанное имя *ElementName* в качестве элемента, сформированного для каждой строки. Дополнительные сведения см. в статье [Использование с RAW Mode для FOR XML](../../relational-databases/xml/use-raw-mode-with-for-xml.md).
  
 AUTO  
 Возвращает результаты запроса в виде простого вложенного дерева XML. Каждая таблица предложения FROM, для которой в предложении SELECT приведен хотя бы один столбец, отображается как элемент XML. Столбцы, перечисленные в предложении SELECT, сопоставлены с соответствующими атрибутами элемента. Дополнительные сведения см. в статье [Использование с AUTO Mode для FOR XML](../../relational-databases/xml/use-auto-mode-with-for-xml.md).  
  
 EXPLICIT  
 Указывает, что форма конечного дерева XML определена явно. При использовании данного режима запросы должны записываться таким образом, чтобы дополнительные сведения о вложениях могли быть заданы явно. Дополнительные сведения см. в статье [Использование с EXPLICIT Mode для FOR XML](../../relational-databases/xml/use-explicit-mode-with-for-xml.md).  
  
 XMLDATA  
 Возвращает встроенную XDR-схему, не добавляя корневой элемент к результату. При задании параметра XMLDATA XDR-схема добавляется к документу.  
  
> [!IMPORTANT]
> Директива XMLDATA **не рекомендуется к использованию**. В режимах RAW и AUTO следует использовать создание XSD-схем. В режиме EXPLICIT для директивы XMLDATA замены нет. [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  

_Подавление нежелательных разрывов строки:_ вы можете использовать SQL Server Management Studio (SSMS) для выдачи запроса, использующего предложение FOR XML. Иногда большой объем кода XML возвращается и отображается в одной ячейке. Длина этой строки XML может превышать максимальную длину одной строки в ячейке сетки SSMS. В этих случаях SSMS может вставить символы разрыва строки между длинными сегментами одной строки XML. Такие разрывы строки могут возникнуть в середине подстроки, которую недопустимо разбивать между двумя строками. Вы можете запретить эти разрывы строки с помощью приведения AS XMLDATA. Это решение также можно применять при использовании FOR JSON PATH. Эта методика описана на форму Stack Overflow и приведена в следующем примере инструкции SELECT на языке Transact-SQL:

- [Using SQL Server FOR XML: Convert Result Datatype to Text/varchar/string whatever?](https://stackoverflow.com/questions/5655332/using-sql-server-for-xml-convert-result-datatype-to-text-varchar-string-whate/5658758#5658758) (Использование SQL Server FOR XML: преобразование типа данных результата в текст/varchar/строку и т. п.)

    ```sql
    SELECT CAST(
        (SELECT column1, column2
            FROM my_table
            FOR XML PATH('')
        )
            AS VARCHAR(MAX)
    ) AS XMLDATA ;
    ```

<!-- The preceding Stack Overflow example is per MicrosoftDocs/sql-docs Issue 1501.  2019-01-06 -->

 XMLSCHEMA [ **('** _URI_целевого_пространства_имен_ **')** ]  
 Возвращает встроенную XSD-схему. При задании указанной директивы, возвращающей заданное пространство имен схемы, дополнительно можно задать URI целевого пространства имен. Дополнительные сведения см. в разделе [Создание встроенных схем XSD](../../relational-databases/xml/generate-an-inline-xsd-schema.md).  
  
 ELEMENTS  
 Задает возврат столбцов в виде вложенных элементов. В противном случае они сопоставляются с XML-атрибутами. Данный параметр поддерживается только в режимах RAW, AUTO и PATH. Дополнительные сведения см. в статье [Использование с RAW Mode для FOR XML](../../relational-databases/xml/use-raw-mode-with-for-xml.md).  
  
 XSINIL  
 Задает создание элемента с атрибутом **xsi:nil**, установленного в значение **True**, для столбцов со значениями NULL. Данный параметр может быть указан только в директиве ELEMENTS. Дополнительные сведения см. в разделе:

- [Создание элементов для значений NULL с помощью параметра XSINIL](../../relational-databases/xml/generate-elements-for-null-values-with-the-xsinil-parameter.md).
- [FOR XML в инструкции SELECT](../../relational-databases/xml/for-xml-sql-server.md)
  
 ABSENT  
 Указывает, что соответствующие XML-элементы для столбцов со значениями NULL к XML-результату не добавляются. Указывайте данный параметр только с директивой ELEMENTS.  
  
 PATH [ **('** _имя_элемента_ **')** ]  
 Создает упаковщик элементов \<row> для каждой строки в результирующем наборе. Для упаковщика элементов \<row> можно дополнительно задать имя элемента. При задании пустой строки, например FOR XML PATH ( **''** ) ), упаковщик элементов не создается. Использование директивы PATH дает более простой способ написания запросов, чем написание запросов с помощью директивы EXPLICIT. Дополнительные сведения см. в статье [Использование с PATH Mode для FOR XML](../../relational-databases/xml/use-path-mode-with-for-xml.md).  
  
 BINARY BASE64  
 Задает возврат двоичных данных запросом в двоичном зашифрованном формате base64. При извлечении двоичных данных с использованием режимов RAW и EXPLICIT необходимо указывать этот параметр. В режиме AUTO это указывается по умолчанию.  
  
 TYPE  
 Задает следующий формат выдаваемых запросом данных: тип **xml**. Дополнительные сведения см. в статье [TYPE Directive in FOR XML Queries](../../relational-databases/xml/type-directive-in-for-xml-queries.md).  
  
 ROOT [ **('** _имя_корневого_элемента_ **')** ]  
 Задает добавление единичного элемента высшего уровня к результирующему XML-документу. Дополнительно можно указать имя корневого элемента, который необходимо сформировать. Если имя корневого элемента не задано, то добавляется элемент \<root> по умолчанию.  
  
 Дополнительные сведения см. в разделе [FOR XML (SQL Server)](../../relational-databases/xml/for-xml-sql-server.md).  
  
 **Пример FOR XML**  
  
 В данном примере задается параметр `FOR XML AUTO` с параметрами `TYPE` и `XMLSCHEMA`. Благодаря параметру `TYPE` результирующий набор возвращается клиенту в формате **xml**. Параметр `XMLSCHEMA` определяет встроенную XSD-схему, включаемую в возвращаемые XML-данные, а параметр `ELEMENTS` указывает, что результаты в формате XML основываются на элементах.  
  
```sql
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
 Укажите FOR JSON, чтобы вернуть результаты запроса в формате текста JSON. Также нужно указать один из следующих режимов JSON: AUTO или PATH. Дополнительные сведения о предложении **FOR JSON** см. в разделе [Форматирование результатов запроса как JSON с помощью предложения FOR JSON (SQL Server)](../../relational-databases/json/format-query-results-as-json-with-for-json-sql-server.md).  
  
 AUTO  
 Форматируйте выходные данные JSON автоматически на основе структуры инструкции **SELECT**,  
            указав **FOR JSON AUTO**. Дополнительные сведения и примеры см. в разделе [Автоматическое форматирование выходных данных JSON в режиме AUTO (SQL Server)](../../relational-databases/json/format-json-output-automatically-with-auto-mode-sql-server.md).  
  
 PATH  
 Чтобы сохранить полный контроль над форматом выходных данных JSON, используйте   
            **FOR JSON PATH**. Режим**PATH** позволяет создавать объекты-оболочки и вкладывать сложные свойства друг в друга. Дополнительные сведения и примеры см. в разделе [Форматирование вложенных выходных данных JSON в режиме PATH (SQL Server)](../../relational-databases/json/format-nested-json-output-with-path-mode-sql-server.md).  
  
 INCLUDE_NULL_VALUES  
 Включайте значения NULL в выходные данные JSON, указав параметр **INCLUDE_NULL_VALUES** для предложения **FOR JSON**. Если не указать этот параметр, в выходные данные не будут включены свойства JSON для значений NULL в результатах запроса. Дополнительные сведения и примеры см. в статье [Использование параметра INCLUDE_NULL_VALUES для включения значений NULL в выходные данные JSON (SQL Server)](../../relational-databases/json/include-null-values-in-json-include-null-values-option.md).  
  
 ROOT [ **('** _имя_корневого_элемента_ **')** ]  
 Добавьте один элемент верхнего уровня к выходным данным JSON, указав параметр **ROOT** с предложение **FOR JSON**. Если не указать параметр **ROOT** , выходные данные JSON не будут содержать корневой элемент. Дополнительные сведения и примеры см. в разделе [Добавление корневого узла в выходные данные JSON с параметром ROOT (SQL Server)](../../relational-databases/json/add-a-root-node-to-json-output-with-the-root-option-sql-server.md).  
  
 WITHOUT_ARRAY_WRAPPER  
 Удалите квадратные скобки, в которые заключаются выходные данные JSON по умолчанию, указав параметр **WITHOUT_ARRAY_WRAPPER** с предложением **FOR JSON**. Если не указать этот параметр, выходные данные JSON будут заключены в квадратные скобки. Параметр **WITHOUT_ARRAY_WRAPPER** позволяет создать в качестве выходных данных единый объект JSON.  Дополнительные сведения см. в разделе [Удаление квадратных скобок из выходных данных JSON с помощью параметра WITHOUT_ARRAY_WRAPPER (SQL Server)](../../relational-databases/json/remove-square-brackets-from-json-without-array-wrapper-option.md).  
  
 Дополнительные сведения см. в разделе [Форматирование результатов запроса как JSON с помощью предложения FOR JSON (SQL Server)](../../relational-databases/json/format-query-results-as-json-with-for-json-sql-server.md).  
  
## <a name="see-also"></a>См. также:

 [SELECT (Transact-SQL)](../../t-sql/queries/select-transact-sql.md)

