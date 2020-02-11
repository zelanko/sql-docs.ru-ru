---
title: 'Указание глубины рекурсивных связей с помощью SQL: max-depth | Документация Майкрософт'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4b247efb895f037965620c7430a3dc41c33fe550
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66013659"
---
# <a name="specifying-depth-in-recursive-relationships-by-using-sqlmax-depth"></a>Задание глубины рекурсивных связей с использованием sql:max-depth
  В реляционных базах данных участие таблицы в связи с самой собой называется рекурсивной связью. Например, таблица, в которой содержатся записи о сотрудниках и возможны связи «начальник-подчиненный», участвует в связи сама с собой. В этом случае таблица сотрудников выполняет роль начальника на одной стороне связи и та же таблица выполняет роль подчиненного на другой стороне.  
  
 Схемы сопоставления могут включать рекурсивные связи, в которых элемент и его предок относятся к одному типу.  
  
## <a name="example-a"></a>Пример A  
 Рассмотрим следующую таблицу.  
  
```  
Emp (EmployeeID, FirstName, LastName, ReportsTo)  
```  
  
 В этой таблице столбец ReportsTo содержит идентификатор служащего для менеджера.  
  
 Предположим, что нужно сформировать XML-иерархию служащих, на вершине которой находится менеджер, а служащие, подчиненные менеджеру, отображаются в соответствующей иерархии, как показано в следующем образце XML-фрагмента. Этот фрагмент показывает *рекурсивное дерево* для сотрудника 1.  
  
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
  
 Чтобы получить этот результат, можно использовать следующую схему XSD и указать запрос XPath к ней. Схема описывает элемент ** \<EMP>** типа типсотрудника, состоящий из дочернего элемента ** \<EMP>** того же типа, что и типсотрудника. Это рекурсивная связь (элемент и его предок относятся к одному типу). Кроме того, схема использует ** \<>SQL: relationship** для описания связи типа «родители-потомки» между супервизором и администратором. Обратите внимание, что в этом ** \<экземпляре SQL: relationship>**, EMP является как родительской, так и дочерней таблицей.  
  
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
  
 Поскольку связь рекурсивная, необходимо каким-то образом указать глубину рекурсии в схеме. В противном случае результатом будет бесконечная рекурсия (служащий, подчиненный служащему, подчиненному служащему, и т. д.). Заметка `sql:max-depth` позволяет указать максимальную глубину рекурсии. В данном конкретном примере, чтобы указать значение `sql:max-depth`, необходимо знать глубину иерархии менеджмента в компании.  
  
> [!NOTE]  
>  Схема задает заметку `sql:limit-field`, но не содержит заметку `sql:limit-value`. Это ограничивает верхний узел в результирующей иерархии только служащими, которые не подчиняются никому. (Подчиняется NULL.) При `sql:limit-field` указании и `sql:limit-value` не указании (значение по умолчанию NULL) это достигается. Если нужно, чтобы результирующий XML включал все возможные деревья подчиненности (дерево подчиненности для каждого служащего в таблице), удалите заметку `sql:limit-field` из схемы.  
  
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
  
5.  Создайте и запустите тестовый скрипт SQLXML 4.0 (Sqlxml4test.vbs), чтобы выполнить шаблон. Дополнительные сведения см. [в разделе Использование ADO для выполнения запросов SQLXML 4,0](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Результат:  
  
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
>  Чтобы получить различные глубины иерархий в результате, измените значение заметки `sql:max-depth` в схеме и вновь выполните шаблон после каждого изменения.  
  
 В предыдущей схеме все элементы ** \<>EMP** имели один и тот же набор атрибутов (**EmployeeID**, **FirstName**и **LastName**). Следующая схема была немного изменена, чтобы вернуть дополнительный атрибут **подчиняется** для всех элементов ** \<>EMP** , которые сообщают руководителю.  
  
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
  
 Используйте заметку `sql:max-depth` в схеме, чтобы указать глубину рекурсии в рекурсивной связи, описанной в схеме. Значение `sql:max-depth` заметки является положительным целым числом (от 1 до 50), которое указывает количество рекурсий: значение 1 останавливает рекурсию в элементе, для которого указана `sql:max-depth` заметка. значение 2 останавливает рекурсию на следующем уровне из элемента, в котором `sql:max-depth` указан параметр. и т. д.  
  
> [!NOTE]  
>  В базовой реализации запрос XPath, заданный для схемы сопоставления, преобразуется в SELECT... Запрос FOR XML EXPLICIT. Для этого запроса необходимо указать конечную глубину рекурсии. Чем выше значение, указанное для `sql:max-depth`, тем больше формируемый запрос FOR XML EXPLICIT. Это может увеличить время выборки.  
  
> [!NOTE]  
>  Диаграммы обновления и массовая загрузка XML не учитывают заметку max-depth. Это означает, что рекурсивные обновления и вставки будут происходить независимо от значения, заданного для max-depth.  
  
## <a name="specifying-sqlmax-depth-on-complex-elements"></a>Задание sql:max-depth для сложных элементов  
 Заметка `sql:max-depth` может быть указана в любом сложном элементе содержимого.  
  
### <a name="recursive-elements"></a>Рекурсивные элементы  
 Если заметка `sql:max-depth` указана как на родительском элементе, так и на дочернем элементе в рекурсивной связи, то заметка `sql:max-depth` на родительском элементе имеет приоритет. Например, в следующей схеме заметка `sql:max-depth` указана как для родительского, так и для дочернего элемента сотрудников. В данном случае `sql:max-depth=4`, заданное в элементе управления ** \<EMP>** родительский элемент (играет роль супервизора), имеет приоритет. `sql:max-depth` Указанный в дочернем ** \<элементе EMP>** (воспроизведение роли "контролируемый") игнорируется.  
  
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
 Заметка `sql:max-depth` не учитывается, если она указана для элемента в схеме, которая не вызывает рекурсии. В следующей схеме элемент ** \<EMP>** состоит из ** \<постоянного>** дочернего элемента, который, в свою очередь, имеет дочерний элемент ** \<EMP>** .  
  
 В этой `sql:max-depth` схеме заметка, указанная в ** \<элементе Constant>** , игнорируется, так как между родительским ** \<>ом EMP** и ** \<константой>** дочернего элемента отсутствует рекурсия. Но существует рекурсия между предком ** \<>EMP** и дочерним элементом ** \<EMP>** . В схеме заметка `sql:max-depth` указывается для обоих элементов. Поэтому приоритет имеет `sql:max-depth` заметку, указанную для предка (**\<>EMP** в роли супервизора).  
  
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
 При наличии сложного типа, производного от ** \<restriction>**, элементы соответствующего базового сложного типа не могут указать `sql:max-depth` заметку. В этих случаях заметка `sql:max-depth` может быть добавлена к элементу производного типа.  
  
 С другой стороны, при наличии сложного типа, производного от ** \<расширения>**, элементы соответствующего базового сложного типа могут указывать `sql:max-depth` заметку.  
  
 Например, следующая схема XSD вызывает ошибку, так как заметка `sql:max-depth` указывается в базовом типе. Эта заметка не поддерживается для типа, производного от ** \<restriction,>** из другого типа. Чтобы устранить эту проблему, необходимо изменить схему и указать заметку `sql:max-depth` в элементе производного типа.  
  
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
  
 В схеме задана заметка `sql:max-depth` в сложном типе `CustomerBaseType`. В схеме также указан элемент ** \<Customer>** типа `CustomerType`, который является производным от `CustomerBaseType`. Запрос XPath, указанный для такой схемы, выдаст ошибку, так как заметка `sql:max-depth` не поддерживается в элементе, определенном в базовом типе по ограничению.  
  
## <a name="schemas-with-a-deep-hierarchy"></a>Схемы с глубокой иерархией  
 Схема может иметь глубокую иерархию, в которой элемент содержит дочерний элемент, который в свою очередь содержит другой дочерний элемент, и т. д. Если заметка `sql:max-depth`, указанная в такой схеме, формирует XML-документ, включающий иерархию из более чем 500 уровней (элемент верхнего уровня считается уровнем 1, его потомок считается уровнем 2, и т. д.), то возвращается ошибка.  
  
  
