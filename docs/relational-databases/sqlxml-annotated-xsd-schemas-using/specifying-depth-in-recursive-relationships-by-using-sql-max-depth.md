---
title: 'Задание глубины рекурсивных связей с использованием SQL: max-depth | Документация Майкрософт'
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- max-depth annotation
- XPath queries [SQLXML], recursive relationships
- depth in recursive relationships [SQLXML]
- annotated XSD schemas, recursive relationships
- relationships [SQLXML], recursive relationships
- self joins
- recursive relationships [SQLXML]
- recursion [SQLXML]
- sql:max-depth
- recursive joins [SQLXML]
ms.assetid: 0ffdd57d-dc30-44d9-a8a0-f21cadedb327
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: acac24b36f5eefcc1490e016d43c4ef014fb813d
ms.sourcegitcommit: bfa10c54e871700de285d7f819095d51ef70d997
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/14/2019
ms.locfileid: "54256129"
---
# <a name="specifying-depth-in-recursive-relationships-by-using-sqlmax-depth"></a>Задание глубины рекурсивных связей с использованием sql:max-depth
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  В реляционных базах данных участие таблицы в связи с самой собой называется рекурсивной связью. Например, таблица, в которой содержатся записи о сотрудниках и возможны связи «начальник-подчиненный», участвует в связи сама с собой. В этом случае таблица сотрудников выполняет роль начальника на одной стороне связи и та же таблица выполняет роль подчиненного на другой стороне.  
  
 Схемы сопоставления могут включать рекурсивные связи, в которых элемент и его предок относятся к одному типу.  
  
## <a name="example-a"></a>Пример A  
 Рассмотрим следующую таблицу.  
  
```  
Emp (EmployeeID, FirstName, LastName, ReportsTo)  
```  
  
 В этой таблице столбец ReportsTo содержит идентификатор служащего для менеджера.  
  
 Предположим, что нужно сформировать XML-иерархию служащих, на вершине которой находится менеджер, а служащие, подчиненные менеджеру, отображаются в соответствующей иерархии, как показано в следующем образце XML-фрагмента. То, что этот фрагмент показывает *рекурсивного дерева* для служащего 1.  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<root>  
  <Emp FirstName="Nancy" EmployeeID="1" LastName="Devolio">  
     <Emp FirstName="Andrew" EmployeeID="2" LastName="Fuller" />   
     <Emp FirstName="Janet" EmployeeID="3" LastName="Leverling">  
        <Emp FirstName="Margaret" EmployeeID="4" LastName="Peacock">  
          <Emp FirstName="Steven" EmployeeID="5" LastName="Devolio">  
...  
...  
</root>  
```  
  
 В этом фрагменте служащий 5 подчинен служащему 4, служащий 4 подчинен служащему 3, а служащие 3 и 2 подчинены служащему 1.  
  
 Чтобы получить этот результат, можно использовать следующую схему XSD и указать запрос XPath к ней. Схема описывает  **\<Emp >** элемент типа EmployeeType, состоящий из  **\<Emp >** дочерний элемент одного типа, EmployeeType. Это рекурсивная связь (элемент и его предок относятся к одному типу). Кроме того, использует схемы  **\<SQL: Relationship >** для описания связи "родители потомки" между начальником и подчиненным. Обратите внимание, что в этом  **\<SQL: Relationship >**, Emp является родительской и дочерней таблицы.  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:dt="urn:schemas-microsoft-com:datatypes"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:annotation>  
    <xsd:appinfo>  
      <sql:relationship name="SupervisorSupervisee"  
                                  parent="Emp"  
                                  parent-key="EmployeeID"  
                                  child="Emp"  
                                  child-key="ReportsTo" />  
    </xsd:appinfo>  
  </xsd:annotation>  
  <xsd:element name="Emp" type="EmployeeType"   
                          sql:relation="Emp"   
                          sql:key-fields="EmployeeID"   
                          sql:limit-field="ReportsTo" />  
  <xsd:complexType name="EmployeeType">  
    <xsd:sequence>  
      <xsd:element name="Emp" type="EmployeeType"   
                              sql:relation="Emp"   
                              sql:key-fields="EmployeeID"  
                              sql:relationship="SupervisorSupervisee"  
                              sql:max-depth="6" />  
    </xsd:sequence>   
    <xsd:attribute name="EmployeeID" type="xsd:ID" />  
    <xsd:attribute name="FirstName" type="xsd:string"/>  
    <xsd:attribute name="LastName" type="xsd:string"/>  
  </xsd:complexType>  
</xsd:schema>  
```  
  
 Поскольку связь рекурсивная, необходимо каким-то образом указать глубину рекурсии в схеме. В противном случае результатом будет бесконечная рекурсия (служащий, подчиненный служащему, подчиненному служащему, и т. д.). **SQL: max-depth** заметки позволяет указать максимальную глубину рекурсии. В данном конкретном примере, чтобы указать значение для **SQL: max-depth**, необходимо знать глубину иерархии менеджмента в компании.  
  
> [!NOTE]  
>  Схема указывает **SQL: Limit-поле** заметки, но не указывает **SQL: Limit-значение** заметки. Это ограничивает верхний узел в результирующей иерархии только служащими, которые не подчиняются никому. (ReportsTo имеет значение NULL.) Указание **SQL: Limit-поле** , не указывая **SQL: Limit-значение** (которое по умолчанию равно NULL) примечания выполняет эту задачу. Если нужно, чтобы результирующий XML включал каждые возможных reporting дерева (дерево подчиненности для каждого служащего в таблице), удалите **SQL: Limit-поле** заметки из схемы.  
  
> [!NOTE]  
>  В следующей процедуре используется база данных tempdb.  
  
#### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>Проверка образца запроса XPath к схеме  
  
1.  Создайте образец таблицы с именем Emp в базе данных tempdb, на которую указывает виртуальный корневой каталог.  
  
    ```  
    USE tempdb  
    CREATE TABLE Emp (  
           EmployeeID int primary key,   
           FirstName  varchar(20),   
           LastName   varchar(20),   
           ReportsTo int)  
    ```  
  
2.  Добавьте следующий образец данных:  
  
    ```  
    INSERT INTO Emp values (1, 'Nancy', 'Devolio',NULL)  
    INSERT INTO Emp values (2, 'Andrew', 'Fuller',1)  
    INSERT INTO Emp values (3, 'Janet', 'Leverling',1)  
    INSERT INTO Emp values (4, 'Margaret', 'Peacock',3)  
    INSERT INTO Emp values (5, 'Steven', 'Devolio',4)  
    INSERT INTO Emp values (6, 'Nancy', 'Buchanan',5)  
    INSERT INTO Emp values (7, 'Michael', 'Suyama',6)  
    ```  
  
3.  Скопируйте приведенный выше код схемы и вставьте его в текстовый файл. Сохраните файл под именем maxDepth.xml.  
  
4.  Скопируйте следующий шаблон и вставьте его в текстовый файл. Сохраните файл под именем maxDepthT.xml в том же каталоге, где был сохранен файл maxDepth.xml. Запрос в шаблоне возвращает всех сотрудников в таблице Emp.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="maxDepth.xml">  
        /Emp  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Путь к каталогу схемы сопоставления (файл maxDepth.xml) задается относительно каталога, в котором сохранен шаблон. Можно также задать абсолютный путь, например:  
  
    ```  
    mapping-schema="C:\MyDir\maxDepth.xml"  
    ```  
  
5.  Создайте и запустите тестовый скрипт SQLXML 4.0 (Sqlxml4test.vbs), чтобы выполнить шаблон. Дополнительные сведения см. в разделе [использование объектов ADO для выполнения запросов SQLXML 4.0](../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Это результат:  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<root>  
  <Emp FirstName="Nancy" EmployeeID="1" LastName="Devolio">  
  <Emp FirstName="Andrew" EmployeeID="2" LastName="Fuller" />   
    <Emp FirstName="Janet" EmployeeID="3" LastName="Leverling">  
      <Emp FirstName="Margaret" EmployeeID="4" LastName="Peacock">  
        <Emp FirstName="Steven" EmployeeID="5" LastName="Devolio">  
          <Emp FirstName="Nancy" EmployeeID="6" LastName="Buchanan">  
            <Emp FirstName="Michael" EmployeeID="7" LastName="Suyama" />   
          </Emp>  
        </Emp>  
      </Emp>  
    </Emp>  
  </Emp>  
</root>  
```  
  
> [!NOTE]  
>  Чтобы получить различные глубины иерархий в результате, измените значение **SQL: max-depth** заметки в схеме и выполняла шаблон еще раз после каждого изменения.  
  
 В предшествующей схеме все  **\<Emp >** элементов были точно тот же набор атрибутов (**EmployeeID**, **FirstName**, и  **LastName**). Следующая схема была незначительно изменена для возврата дополнительных **ReportsTo** атрибутов для всех  **\<Emp >** элементы, сообщающие с диспетчером.  
  
 Например, этот XML-фрагмент показывает подчиненных служащего 1:  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<root>  
<Emp FirstName="Nancy" EmployeeID="1" LastName="Devolio">  
  <Emp FirstName="Andrew" EmployeeID="2"   
       ReportsTo="1" LastName="Fuller" />   
  <Emp FirstName="Janet" EmployeeID="3"   
       ReportsTo="1" LastName="Leverling">  
...  
...  
```  
  
 Ниже приведена измененная схема:  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:dt="urn:schemas-microsoft-com:datatypes"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:annotation>  
    <xsd:documentation>  
      Customer-Order-Order Details Schema  
      Copyright 2000 Microsoft. All rights reserved.  
    </xsd:documentation>  
    <xsd:appinfo>  
      <sql:relationship name="SupervisorSupervisee"   
                  parent="Emp"  
                  parent-key="EmployeeID"  
                  child="Emp"  
                  child-key="ReportsTo" />  
    </xsd:appinfo>  
  </xsd:annotation>  
  <xsd:element name="Emp"   
                   type="EmpType"   
                   sql:relation="Emp"   
                   sql:key-fields="EmployeeID"   
                   sql:limit-field="ReportsTo" />  
  <xsd:complexType name="EmpType">  
    <xsd:sequence>  
       <xsd:element name="Emp"   
                    type="EmpType"   
                    sql:relation="Emp"   
                    sql:key-fields="EmployeeID"  
                    sql:relationship="SupervisorSupervisee"  
                    sql:max-depth="6"/>  
    </xsd:sequence>   
    <xsd:attribute name="EmployeeID" type="xsd:int" />  
    <xsd:attribute name="FirstName" type="xsd:string"/>  
    <xsd:attribute name="LastName" type="xsd:string"/>  
    <xsd:attribute name="ReportsTo" type="xsd:int" />  
  </xsd:complexType>  
</xsd:schema>  
```  
  
## <a name="sqlmax-depth-annotation"></a>Заметка sql:max-depth  
 В схеме, состоящей из рекурсивных связей, глубина рекурсии должна быть явно указана в схеме. Это необходимо для успешной подготовки соответствующего запроса FOR XML EXPLICIT, который возвращает запрошенные результаты.  
  
 Используйте **SQL: max-depth** заметки в схеме, чтобы указать глубину рекурсии в рекурсивной связи, описанный в схеме. Значение **SQL: max-depth** заметки — положительное целое число (от 1 до 50), указывающее количество рекурсий:  Значение 1 останавливает рекурсию на элементе, для которого **SQL: max-глубины** заметки указана, значение 2 останавливает рекурсию на следующем уровне от элемента, по которому **SQL: max-depth** указан ; и т. д.  
  
> [!NOTE]  
>  В базовой реализации запрос XPath, заданный для схемы сопоставления, преобразуется в запрос SELECT ... Запрос FOR XML EXPLICIT. Для этого запроса необходимо указать конечную глубину рекурсии. Чем выше значение, указываемое для **SQL: max-depth**, чем запрос FOR XML EXPLICIT, создается. Это может увеличить время выборки.  
  
> [!NOTE]  
>  Диаграммы обновления и массовая загрузка XML не учитывают заметку max-depth. Это означает, что рекурсивные обновления и вставки будут происходить независимо от значения, заданного для max-depth.  
  
## <a name="specifying-sqlmax-depth-on-complex-elements"></a>Задание sql:max-depth для сложных элементов  
 **SQL: max-depth** заметки могут быть заданы в любом сложном элементе содержимого.  
  
### <a name="recursive-elements"></a>Рекурсивные элементы  
 Если **SQL: max-depth** задан как родительский элемент, так и дочерний элемент в рекурсивной связи, **SQL: max-глубина** заметки на родительском элементе имеет более высокий приоритет. Например, в следующей схеме **SQL: max-depth** задана заметка для у родительского и дочернего элемента сотрудников. В этом случае **SQL: max-depth = 4**, определенный на  **\<Emp >** родительского элемента (выполняет роль начальника), имеет приоритет. **SQL: max-depth** указанное на дочернем  **\<Emp >** элементе (выполняет роль подчиненного) учитывается.  
  
#### <a name="example-b"></a>Пример Б  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:dt="urn:schemas-microsoft-com:datatypes"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:annotation>  
    <xsd:appinfo>  
      <sql:relationship name="SupervisorSupervisee"  
                                  parent="Emp"  
                                  parent-key="EmployeeID"  
                                  child="Emp"  
                                  child-key="ReportsTo" />  
    </xsd:appinfo>  
  </xsd:annotation>  
  <xsd:element name="Emp" type="EmployeeType"   
                          sql:relation="Emp"   
                          sql:key-fields="EmployeeID"   
                          sql:limit-field="ReportsTo"   
                          sql:max-depth="3" />  
  <xsd:complexType name="EmployeeType">  
    <xsd:sequence>  
      <xsd:element name="Emp" type="EmployeeType"   
                              sql:relation="Emp"   
                              sql:key-fields="EmployeeID"  
                              sql:relationship="SupervisorSupervisee"  
                              sql:max-depth="2" />  
    </xsd:sequence>   
    <xsd:attribute name="EmployeeID" type="xsd:ID" />  
    <xsd:attribute name="FirstName" type="xsd:string"/>  
    <xsd:attribute name="LastName" type="xsd:string"/>  
  </xsd:complexType>  
</xsd:schema>  
```  
  
 Для проверки этой схемы выполните шаги, приведенные для образца А ранее в этом разделе.  
  
### <a name="nonrecursive-elements"></a>Нерекурсивные элементы  
 Если **SQL: max-depth** задана заметка для элемента в схеме, которая не вызывает рекурсии, он учитывается. В следующей схеме  **\<Emp >** элемент состоит из  **\<константы >** дочерний элемент, который в свою очередь, имеет  **\<Emp >** дочерний элемент.  
  
 В этой схеме **SQL: max-depth** заметка, указанная на  **\<константы >** элемент пропускается из-за отсутствия рекурсии между  **\<Emp >** родительского и  **\<константы >** дочерний элемент. Но существует рекурсия между  **\<Emp >** предка и  **\<Emp >** дочерних. Схема задает **SQL: max-depth** заметки на обоих. Таким образом **SQL: max-depth** заметка, указанная для предка (**\<Emp >** в роли начальника) имеет более высокий приоритет.  
  
#### <a name="example-c"></a>Пример В  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:annotation>  
    <xsd:appinfo>  
      <sql:relationship name="SupervisorSupervisee"   
                  parent="Emp"   
                  child="Emp"   
                  parent-key="EmployeeID"   
                  child-key="ReportsTo"/>  
    </xsd:appinfo>  
  </xsd:annotation>  
  <xsd:element name="Emp"   
               sql:relation="Emp"   
               type="EmpType"  
               sql:limit-field="ReportsTo"  
               sql:max-depth="1" />  
    <xsd:complexType name="EmpType" >  
      <xsd:sequence>  
       <xsd:element name="Constant"   
                    sql:is-constant="1"   
                    sql:max-depth="20" >  
         <xsd:complexType >  
           <xsd:sequence>  
            <xsd:element name="Emp"   
                         sql:relation="Emp" type="EmpType"  
                         sql:relationship="SupervisorSupervisee"   
                         sql:max-depth="3" />  
         </xsd:sequence>  
         </xsd:complexType>  
         </xsd:element>  
      </xsd:sequence>  
      <xsd:attribute name="EmployeeID" type="xsd:int" />  
    </xsd:complexType>  
</xsd:schema>  
```  
  
 Для проверки этой схемы выполните шаги, приведенные для примера А ранее в этом разделе.  
  
## <a name="complex-types-derived-by-restriction"></a>Сложные типы, наследуемые по ограничению  
 Если при наследовании сложного типа по  **\<ограничение >**, элементы соответствующего базового сложного типа не может указывать **SQL: max-depth** заметки. В этих случаях **SQL: max-depth** можно добавить заметки к элементу производного типа.  
  
 С другой стороны, если при наследовании сложного типа по  **\<расширения >**, элементы соответствующего базового сложного типа могут указывать **SQL: max-depth** заметки.  
  
 Например, следующая схема XSD возникает ошибка, поскольку **SQL: max-depth** задана заметка для базового типа. Эта заметка не поддерживается для типа, который является производным,  **\<ограничение >** от другого типа. Чтобы устранить эту проблему, необходимо изменить схему и указать **SQL: max-depth** заметки в элементе производного типа.  
  
#### <a name="example-d"></a>Пример Г  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:dt="urn:schemas-microsoft-com:datatypes"  
            xmlns:msdata="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:complexType name="CustomerBaseType">   
    <xsd:sequence>  
       <xsd:element name="CID" msdata:field="CustomerID" />  
       <xsd:element name="CompanyName"/>  
       <xsd:element name="Customers" msdata:max-depth="3">  
         <xsd:annotation>  
           <xsd:appinfo>  
             <msdata:relationship  
                     parent="Customers"  
                     parent-key="CustomerID"  
                     child-key="CustomerID"  
                     child="Customers" />  
           </xsd:appinfo>  
         </xsd:annotation>  
       </xsd:element>  
    </xsd:sequence>  
  </xsd:complexType>  
  <xsd:element name="Customers" type="CustomerType"/>  
  <xsd:complexType name="CustomerType">  
    <xsd:complexContent>  
       <xsd:restriction base="CustomerBaseType">  
          <xsd:sequence>  
            <xsd:element name="CID"   
                         type="xsd:string"/>  
            <xsd:element name="CompanyName"   
                         type="xsd:string"  
                         msdata:field="CName" />  
            <xsd:element name="Customers"   
                         type="CustomerType" />  
          </xsd:sequence>  
       </xsd:restriction>  
    </xsd:complexContent>  
  </xsd:complexType>  
</xsd:schema>   
```  
  
 В схеме **SQL: max-depth** заметка указывается для **CustomerBaseType** сложного типа. Схема также задает  **\<клиента >** элемент типа **CustomerType**, который является производным от **CustomerBaseType**. Запрос XPath, указанный для такой схемы приведет к ошибке, так как **SQL: max-depth** не поддерживается в элементе, который определен в базовом типе по ограничению.  
  
## <a name="schemas-with-a-deep-hierarchy"></a>Схемы с глубокой иерархией  
 Схема может иметь глубокую иерархию, в которой элемент содержит дочерний элемент, который в свою очередь содержит другой дочерний элемент, и т. д. Если **SQL: max-depth** заметки, указанных в такой схеме формирует XML-документ, включающий иерархию из более чем 500 уровней (элемент верхнего уровня на уровень 1, его потомок считается уровнем 2 и т. д.), будет возвращена ошибка.  
  
  
