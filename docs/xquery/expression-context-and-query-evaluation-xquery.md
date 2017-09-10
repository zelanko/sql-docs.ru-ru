---
title: "Контекст выражения и вычисление запросов (XQuery) | Документы Microsoft"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
dev_langs:
- XML
helpviewer_keywords:
- expression context [XQuery]
- XQuery, expression context
- XQuery, query evaluation
- static context
- dynamic context [XQuery]
ms.assetid: 5059f858-086a-40d4-811e-81fedaa18b06
caps.latest.revision: 19
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 0aaa0fb28aa648018a4d9f562e5ac2452e0d2309
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="expression-context-and-query-evaluation-xquery"></a>Контекст выражения и вычисление запросов (XQuery)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Контекст выражения представляет собой данные, используемые для анализа и оценки. Ниже приводятся две фазы оценки XQuery:  
  
-   **Статический контекст** — это фаза компиляции запроса. Иногда ошибки могут возникать в процессе такого статического анализа запроса, основанного на доступных данных.  
  
-   **Динамический контекст** — это фаза выполнения запроса. Даже если в запросе нет статических ошибок, таких как ошибки компиляции, он может вернуть ошибки во время исполнения.  
  
## <a name="static-context"></a>Статический контекст  
 Инициализация статического контекста относится к процессу объединения данных для статического анализа выражения. В рамках инициализации статического контекста выполняются следующие операции:  
  
-   **Пробела границы** политики устанавливается на чередование. Таким образом, пробел границы не сохраняется **любой элемент** и **атрибута** конструкторы в запросе. Например:  
  
    ```  
    declare @x xml  
    set @x=''  
    select @x.query('<a>  {"Hello"}  </a>,  
  
        <b> {"Hello2"}  </b>')  
    ```  
  
     Этот запрос возвращает следующий результат, поскольку граничные пробелы удаляются во время анализа выражения XQuery:  
  
    ```  
    <a>Hello</a><b>Hello2</b>  
    ```  
  
-   Инициализируются связывания префикса с пространством имен для:  
  
    -   Набор стандартных пространств имен.  
  
    -   Любых пространств имен, определенных при помощи WITH XMLNAMESPACES. Дополнительные сведения см. в разделе [добавление пространств имен в запросы с WITH XMLNAMESPACES](../relational-databases/xml/add-namespaces-to-queries-with-with-xmlnamespaces.md)).  
  
    -   Любых пространств имен, определенных в прологе запроса. Обратите внимание на то, что объявления пространств имен в прологе могут отменять объявления пространств имен в WITH XMLNAMESPACES. Например, в следующем запросе WITH XMLNAMESPACES объявляет префикс (pd), который привязывает его к пространству имен (`http://someURI`). Однако пролог запроса отменяет связывание в предложении WHERE.  
  
        ```  
        WITH XMLNAMESPACES ('http://someURI' AS pd)  
        SELECT ProductModelID, CatalogDescription.query('  
            <Product   
                ProductModelID= "{ sql:column("ProductModelID") }"   
                />  
        ') AS Result  
        FROM Production.ProductModel  
        WHERE CatalogDescription.exist('  
            declare namespace  pd="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
             /pd:ProductDescription[(pd:Specifications)]'  
            ) = 1  
        ```  
  
     Все такие связывания пространств имен разрешаются в процессе инициализации статического контекста.  
  
-   При запросе типизированного **xml** столбца или переменной, компоненты коллекции XML-схем, связанные со столбцом или переменной, импортируются в статический контекст. Дополнительные сведения см. в статье [Сравнение типизированного и нетипизированного XML](../relational-databases/xml/compare-typed-xml-to-untyped-xml.md).  
  
-   Функция приведения также становится доступной в статическом контексте для каждого атомарного типа в импортированных схемах. Это продемонстрировано в следующем примере. В этом примере запрос производится к типизированному **xml** переменной. Коллекция XML-схем, связанная с данной переменной, определяет атомный тип myType. Для этого типа, функция приведения **myType()**, во время статического анализа доступна. Выражение запроса (`ns:myType(0)`) возвращает значение myType.  
  
    ```  
    -- DROP XML SCHEMA COLLECTION SC  
    -- go  
    CREATE XML SCHEMA COLLECTION SC AS '<schema xmlns="http://www.w3.org/2001/XMLSchema"   
    targetNamespace="myNS" xmlns:ns="myNS"  
    xmlns:s="http://schemas.microsoft.com/sqlserver/2004/sqltypes">  
          <import namespace="http://schemas.microsoft.com/sqlserver/2004/sqltypes"/>  
          <simpleType name="myType">  
                <restriction base="int">  
                 <enumeration value="0" />  
                  <enumeration value="1"/>  
                </restriction>  
          </simpleType>  
          <element name="root" type="ns:myType"/>  
    </schema>'  
    go  
  
    DECLARE @var XML(SC)  
    SET @var = '<root xmlns="myNS">0</root>'  
    -- specify myType() casting function in the query  
    SELECT @var.query('declare namespace ns="myNS"; ns:myType(0)')  
    ```  
  
     В следующем примере функция приведения для **int** встроенного типа XML, указанный в выражении.  
  
    ```  
    declare @x xml  
    set @x = ''  
    select @x.query('xs:int(5)')  
    go  
    ```  
  
 После инициализации статического контекста анализируется (компилируется) выражение запроса. Статический анализ включает следующее:  
  
1.  Анализ запроса.  
  
2.  Разрешение функции и имен типа, указанного в выражении.  
  
3.  Статическую типизацию запроса. Это гарантирует безопасность типа запроса.  Например, следующий запрос возвращает статическую ошибку, так как  **+**  оператор требует аргументы простого числового типа:  
  
    ```  
    declare @x xml  
    set @x=''  
    SELECT @x.query('"x" + 4')  
    ```  
  
     В следующем примере **value()** оператор требует одноэлементного запроса. Как указано в схеме XML, может существовать несколько \<Elem > элементов. Статический анализ выражения определяет, что это небезопасный тип, и возвращает статическую ошибку. Чтобы устранить ошибку, выражение должно быть переписано таким образом, чтобы явно указать одноэлементный запрос (`data(/x:Elem)[1]`).  
  
    ```  
    DROP XML SCHEMA COLLECTION SC  
    go  
    CREATE XML SCHEMA COLLECTION SC AS '<schema xmlns="http://www.w3.org/2001/XMLSchema"   
    targetNamespace="myNS" xmlns:ns="myNS"  
    xmlns:s="http://schemas.microsoft.com/sqlserver/2004/sqltypes">  
          <import namespace="http://schemas.microsoft.com/sqlserver/2004/sqltypes"/>  
          <element name="Elem" type="string"/>  
    </schema>'  
    go  
  
    declare @x xml (SC)  
    set @x='<Elem xmlns="myNS">test</Elem><Elem xmlns="myNS">test2</Elem>'  
    SELECT @x.value('declare namespace x="myNS"; data(/x:Elem)[1]','varchar(20)')  
    ```  
  
     Дополнительные сведения см. в разделе [XQuery и Статическая типизация](../xquery/xquery-and-static-typing.md).  
  
### <a name="implementation-restrictions"></a>Ограничения реализации  
 Далее приводятся ограничения, связанные со статическим контекстом:  
  
-   Режим совместимости XPath не поддерживается.  
  
-   Для структуры XML доступен только режим структуры чередования. Это параметр по умолчанию. Таким образом, тип узла создаваемых элементов имеют **xdt: нетипизированный** и атрибуты имеют **xdt: untypedAtomic** типа.  
  
-   Поддерживается только режим упорядоченной сортировки.  
  
-   Поддерживается только политика чередующегося пробела XML.  
  
-   Основная функциональность URI не поддерживается.  
  
-   **fn:doc()** не поддерживается.  
  
-   **fn:Collection()** не поддерживается.  
  
-   Детектор запросов XQuery со статической типизацией не предоставляется.  
  
-   Параметры сортировки, связанные с **xml** используется тип данных. Всегда используются параметры сортировки по кодовым точкам Юникода.  
  
## <a name="dynamic-context"></a>Динамический контекст  
 Динамический контекст связан с данными, которые должны быть доступны во время выполнения выражения. Помимо статического контекста происходит инициализация следующих данных как части динамического контекста:  
  
-   Фокус выражения, такой как элемент контекста, положение контекста и размер контекста, инициализируется следующим образом. Обратите внимание, что эти значения могут быть переопределены [метода nodes()](../t-sql/xml/nodes-method-xml-data-type.md).  
  
    -   **Xml** тип данных устанавливает элемент контекста и обрабатываемый узел документа узел.  
  
    -   Положение контекста — это положение элемента контекста, который относится к обрабатываемому узлу изначально устанавливается в 1.  
  
    -   Размер контекста — это количество элементов в обрабатываемой последовательности изначально устанавливается в 1, поскольку всегда существует один узел документа.  
  
### <a name="implementation-restrictions"></a>Ограничения реализации  
 Далее приводятся ограничения, связанные с динамическим контекстом:  
  
-   **Текущую дату и время** функции контекста **fn:current-Дата**, **fn:current-время**, и **fn:current-dateTime**, не являются поддерживается.  
  
-   **Неявные временные зоны** фиксируется на UTC + 0 и не может быть изменено.  
  
-   **Fn:doc()** функция не поддерживается. Все запросы выполняются для **xml** столбцов или переменных типа.  
  
-   **Fn:collection()** функция не поддерживается.  
  
## <a name="see-also"></a>См. также:  
 [Основы языка XQuery](../xquery/xquery-basics.md)   
 [Сравнение типизированного и нетипизированного XML](../relational-databases/xml/compare-typed-xml-to-untyped-xml.md)   
 [Коллекции XML-схем (SQL Server)](../relational-databases/xml/xml-schema-collections-sql-server.md)  
  
  
