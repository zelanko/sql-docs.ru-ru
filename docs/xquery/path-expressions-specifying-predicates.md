---
title: Определение предикатов в шаге выражения пути | Документация Майкрософт
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- axis step [XQuery]
- predicates [XQuery]
- qualifiers [XQuery]
- path expressions [XQuery]
ms.assetid: 2660ceca-b8b4-4a1f-98a0-719ad5f89f81
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: e4b5840671eca5ee26a7c8ab32bc6788e465cc5c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47715922"
---
# <a name="path-expressions---specifying-predicates"></a>Выражения пути — указание предикатов
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Как описано в разделе [выражения пути в XQuery](../xquery/path-expressions-xquery.md), шаг оси в выражении пути содержит следующие компоненты:  
  
-   [Оси](../xquery/path-expressions-specifying-axis.md).  
  
-   Тест узла. Дополнительные сведения см. в разделе [указание проверки узла в шаге выражения пути](../xquery/path-expressions-specifying-node-test.md).  
  
-   Ноль или более предикатов. Водить описание не обязательно.  
  
 Необязательный предикат является третьим компонентом шага оси в выражении пути.  
  
## <a name="predicates"></a>Предикаты  
 Предикат используется для фильтрации последовательности узлов при помощи заданного теста. Выражение предиката заключено в квадратные скобки и привязано к последнему узлу выражения пути.  
  
 Например, предположим, что значение параметра SQL (x) из **xml** объявлен тип данных, как показано в следующем:  
  
```  
declare @x xml  
set @x = '  
<People>  
  <Person>  
    <Name>John</Name>  
    <Age>24</Age>  
  </Person>  
  <Person>  
    <Name>Goofy</Name>  
    <Age>54</Age>  
  </Person>  
  <Person>  
    <Name>Daffy</Name>  
    <Age>30</Age>  
  </Person>  
</People>  
'  
```  
  
 В этом случае следующие выражения, использующие значение предиката, равное [1], на каждом из трех уровней узлов, будут допустимыми:  
  
```  
select @x.query('/People/Person/Name[1]')  
select @x.query('/People/Person[1]/Name')  
select @x.query('/People[1]/Person/Name')  
```  
  
 Обратите внимание, что в каждом случае предикат привязан к узлу выражения пути, где он применяется. Например, первое выражение пути выбирает первый элемент <`Name`> в каждом узле /People/Person и при помощи заданного экземпляра XML возвращает следующий результат:  
  
```  
<Name>John</Name><Name>Goofy</Name><Name>Daffy</Name>  
```  
  
 Однако второе выражение пути выбирает все элементы <`Name`> первого узла /People/Person. Таким образом, оно возвращает следующий результат:  
  
```  
<Name>John</Name>  
```  
  
 Порядок вычисления предикатов можно менять при помощи круглых скобок. Например, в следующем выражении круглые скобки используются для разделения пути (/People/Person/Name) от предиката [1]:  
  
```  
select @x.query('(/People/Person/Name)[1]')  
```  
  
 В этом примере порядок применения предикатов изменяется. Сначала вычисляется путь, заключенный в круглые скобки (/People/Person/Name), а затем оператор предиката [1] применяется к набору, содержащему все узлы, которые соответствуют этому пути. Если убрать круглые скобки, порядок операций будет другим; предикат [1] будет применяться в качестве теста узла `child::Name`, так же, как и в первом примере.  
  
### <a name="quantifiers-and-predicates"></a>Квалификаторы и предикаты  
 Квалификаторы можно использовать более одного раза в фигурных скобках предиката. Например, в предыдущем примере можно использовать более одного квалификатора в сложном подвыражении предиката следующим образом.  
  
```  
select @x.query('/People/Person[contains(Name[1], "J") and xs:integer(Age[1]) < 40]/Name/text()')  
```  
  
 Результат выражения предиката преобразуется в значение типа Boolean и называется истинностью предиката. Набор результатов содержит только те узлы последовательности, для которых значение предиката равно True. Остальные узлы отбрасываются.  
  
 Например, предикат содержит второй шаг следующего выражения пути:  
  
```  
/child::root/child::Location[attribute::LocationID=10]  
```  
  
 Условие, заданное при помощи предиката, применяется ко всем дочерним элементам узла <`Location`>. Возвращаются только те результаты, у которых значение атрибута LocationID равно 10.  
  
 Предыдущее выражение пути выполнялось в следующей инструкции SELECT:  
  
```  
SELECT Instructions.query('  
declare namespace AWMI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
 /child::AWMI:root/child::AWMI:Location[attribute::LocationID=10]  
')  
FROM Production.ProductModel  
WHERE ProductModelID=7  
```  
  
### <a name="computing-predicate-truth-values"></a>Проверка истинности предикатов  
 Чтобы определить истинность значения предиката согласно спецификации XQuery, применяются следующие правила:  
  
1.  Если значение выражения предиката представляет пустую последовательность, значение предиката равно False.  
  
     Пример:  
  
    ```  
    SELECT Instructions.query('  
    declare namespace AWMI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
     /child::AWMI:root/child::AWMI:Location[attribute::LotSize]  
    ')  
    FROM Production.ProductModel  
    WHERE ProductModelID=7  
    ```  
  
     Выражение пути в этом запросе возвращает только такие узлы элемента <`Location`>, у которых задан атрибут LotSize. Если предикат возвращает пустую последовательность для некоторого элемента <`Location`>, то данное расположение цеха не включается в результат.  
  
2.  Предикат, значения могут быть только в том случае, xs: Integer, xs: Boolean или узел\*. Для узла\*, предикат возвращает значение True, если такие узлы существуют и значение False, если для пустой последовательности. При использовании других числовых типов, например double или float, возникает ошибка статической типизации. Значение предиката выражения равно True тогда и только тогда, когда полученное значение типа integer равно значению позиции контекста. Кроме того, только целые литеральные значения и **last()** функция уменьшают количество элементов шага фильтрации выражения до 1.  
  
     Например, следующий запрос возвращает третий дочерний узел элемента <`Features`>.  
  
    ```  
    SELECT CatalogDescription.query('  
    declare namespace PD="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
    declare namespace wm="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain";  
     /child::PD:ProductDescription/child::PD:Features/child::*[3]  
    ')  
    FROM Production.ProductModel  
    WHERE ProductModelID=19  
    ```  
  
     Обратите внимание на следующие данные из предыдущего запроса:  
  
    -   Третий шаг выражения задает выражение предиката со значением, равным 3. Таким образом, значение истинности предиката равно True только для тех узлов, у которых позиция контекста равна 3.  
  
    -   Третий шаг также содержит символ-шаблон (*), который указывает на все узлы в тесте узлов. Тем не менее предикат фильтрует узлы и возвращает только те из них, которые находятся на третьей позиции.  
  
    -   Запрос возвращает третий дочерний узел элемента <`Features`> дочерних узлов элемента <`ProductDescription`> корневого узла.  
  
3.  Если значение выражения предиката представляет собой простое значение типа Boolean, значение истинности предиката совпадает с ним.  
  
     Например, следующий запрос адресован **xml**переменной типа, которая содержит экземпляр XML, экземпляр XML опроса клиента. Запрос получает только тех клиентов, у которых есть дети. В этом запросе, это было бы \<HasChildren > 1\</HasChildren >.  
  
    ```  
    declare @x xml  
    set @x='  
    <Survey>  
      <Customer CustomerID="1" >  
      <Age>27</Age>  
      <Income>20000</Income>  
      <HasChildren>1</HasChildren>  
      </Customer>  
      <Customer CustomerID="2" >  
      <Age>27</Age>  
      <Income>20000</Income>  
      <HasChildren>0</HasChildren>  
      </Customer>  
    </Survey>  
    '  
    declare @y xml  
    set @y = @x.query('  
      for $c in /child::Survey/child::Customer[( child::HasChildren[1] cast as xs:boolean ? )]  
      return   
          <CustomerWithChildren>  
              { $c/attribute::CustomerID }  
          </CustomerWithChildren>  
    ')  
    select @y  
    ```  
  
     Обратите внимание на следующие данные из предыдущего запроса:  
  
    -   Выражение в **для** цикл состоит из двух шагов, а второй шаг содержит предикат. Значение предиката имеет тип Boolean. Если это значение равно True, значение истинности предиката также равно True.  
  
    -   Запрос возвращает <`Customer`> дочерние элементы, в которых значение предиката равно True, из \<Survey > дочерние элементы корневого элемента документа. Результат:  
  
        ```  
        <CustomerWithChildren CustomerID="1"/>   
        ```  
  
4.  Если значение выражения предиката представляет последовательность как минимум из одного узла, значение истинности предиката равно True.  
  
 Например, следующий запрос получает идентификатор ProductModelID моделей продукции, описания каталога XML включает по крайней мере один компонент, дочерний элемент элемента <`Features`> элемент, из пространства имен, связанный с **wm**префикс.  
  
```  
SELECT ProductModelID  
FROM   Production.ProductModel  
WHERE CatalogDescription.exist('  
             declare namespace PD="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
             declare namespace wm="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain";  
             /child::PD:ProductDescription/child::PD:Features[wm:*]  
             ') = 1  
```  
  
 Обратите внимание на следующие данные из предыдущего запроса:  
  
-   В предложении WHERE указано [метод exist() (тип данных XML)](../t-sql/xml/exist-method-xml-data-type.md).  
  
-   Выражения пути внутри **exist()** метод задает предикат на втором шаге. Если выражение предиката возвращает последовательность как минимум из одной функции, значение истинности выражения предиката равно True. В этом случае так как **exist()** метод возвращает значение True, возвращается ProductModelID.  
  
## <a name="static-typing-and-predicate-filters"></a>Статическая типизация и фильтры предикатов  
 Предикаты также могут влиять на статически выведенный тип выражения. Целые литеральные значения и **last()** функция уменьшают количество элементов шага фильтрации выражения до одного.  
  
  
