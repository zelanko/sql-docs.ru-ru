---
title: Выражения последовательности (XQuery) | Документация Майкрософт
description: Сведения о выражениях последовательности XQuery, которые создают, фильтруют и объединяют последовательность элементов.
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- sequence [XQuery]
- expressions [XQuery], sequence
- filtering sequences [XQuery]
ms.assetid: 41e18b20-526b-45d2-9bd9-e3b7d7fbce4e
author: rothja
ms.author: jroth
ms.openlocfilehash: 5e7ae12dd658b6b5affde321666d84b010771699
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/22/2020
ms.locfileid: "86916130"
---
# <a name="sequence-expressions-xquery"></a>Выражения последовательности (XQuery)
[!INCLUDE[sqlserver](../includes/applies-to-version/sqlserver.md)]

  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] поддерживает операторы XQuery, предназначенные для конструирования, фильтрации и комбинирования последовательностей элементов. Элемент может быть атомарным значением или узлом.  
  
## <a name="constructing-sequences"></a>Конструирование последовательностей  
 Оператор «запятая» позволяет сцеплять элементы в единую последовательность.  
  
 Последовательность может содержать повторяющиеся значения. Вложенные последовательности (последовательность в последовательности) всегда сворачиваются. Например, последовательность (1, 2, (3, 4, (5))) превращается в (1, 2, 3, 4, 5). Ниже приведены примеры конструирования последовательностей.  
  
### <a name="example-a"></a>Пример A  
 Следующий запрос возвращает последовательность из пяти атомарных значений:  
  
```  
declare @x xml  
set @x=''  
select @x.query('(1,2,3,4,5)')  
go  
-- result 1 2 3 4 5  
```  
  
 Следующий запрос возвращает последовательность из двух узлов:  
  
```  
-- sequence of 2 nodes  
declare @x xml  
set @x=''  
select @x.query('(<a/>, <b/>)')  
go  
-- result  
<a />  
<b />  
```  
  
 Следующий запрос возвращает ошибку, так как конструируется последовательность из атомарных значений и узлов. Разнородные последовательности не поддерживаются.  
  
```  
declare @x xml  
set @x=''  
select @x.query('(1, 2, <a/>, <b/>)')  
go  
```  
  
### <a name="example-b"></a>Пример Б  
 Следующий запрос конструирует последовательность из атомарных значений, соединяя последовательности разной длины в единую последовательность.  
  
```  
declare @x xml  
set @x=''  
select @x.query('(1,2),10,(),(4, 5, 6)')  
go  
-- result = 1 2 10 4 5 6  
```  
  
 Сортировку последовательности можно произвести по FLOWR и ORDER BY:  
  
```  
declare @x xml  
set @x=''  
select @x.query('for $i in ((1,2),10,(),(4, 5, 6))  
                  order by $i  
                  return $i')  
go  
```  
  
 Количество элементов в последовательности можно подсчитать с помощью функции **fn: count ()** .  
  
```  
declare @x xml  
set @x=''  
select @x.query('count( (1,2,3,(),4) )')  
go  
-- result = 4  
```  
  
### <a name="example-c"></a>Пример В  
 Следующий запрос задается для столбца AdditionalContactInfo типа **XML** в таблице Contact. В этом столбце хранятся дополнительные контактные данные: адреса, номера телефонов и пейджеров. \<telephoneNumber>Узлы, \<pager> и могут находиться в любом месте документа. Запрос формирует последовательность, которая содержит все \<telephoneNumber> дочерние узлы контекстного узла, за которыми следуют \<pager> дочерние элементы. Обратите внимание на применение оператора последовательности в возвращаемом выражении `($a//act:telephoneNumber, $a//act:pager)`.  
  
```  
WITH XMLNAMESPACES ('https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes' AS act,  
 'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactInfo' AS aci)  
  
SELECT AdditionalContactInfo.query('  
   for $a in /aci:AdditionalContactInfo   
   return ($a//act:telephoneNumber, $a//act:pager)  
') As Result  
FROM Person.Contact  
WHERE ContactID=3  
```  
  
 Результат:  
  
```  
<act:telephoneNumber xmlns:act="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">  
  <act:number>333-333-3333</act:number>  
</act:telephoneNumber>  
<act:telephoneNumber xmlns:act="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">  
  <act:number>333-333-3334</act:number>  
</act:telephoneNumber>  
<act:pager xmlns:act="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">  
  <act:number>999-555-1244</act:number>  
  <act:SpecialInstructions>  
Page only in case of emergencies.  
</act:SpecialInstructions>  
</act:pager>  
```  
  
## <a name="filtering-sequences"></a>Фильтрация последовательностей  
 Можно отфильтровать возвращаемую последовательность по выражению, добавив предикат. Дополнительные сведения см. в разделе [выражения пути &#40;XQuery&#41;](../xquery/path-expressions-xquery.md). Например, следующий запрос возвращает последовательность из трех <`a`> узлов элементов:  
  
```  
declare @x xml  
set @x = '<root>  
<a attrA="1">111</a>  
<a></a>  
<a></a>  
</root>'  
SELECT @x.query('/root/a')  
```  
  
 Результат:  
  
```  
<a attrA="1">111</a>  
<a />  
<a />  
```  
  
 Чтобы получить только <`a`> элементов, имеющих атрибут attr, можно указать фильтр в предикате. Результирующая последовательность будет содержать только один `a` элемент> <.  
  
```  
declare @x xml  
set @x = '<root>  
<a attrA="1">111</a>  
<a></a>  
<a></a>  
</root>'  
SELECT @x.query('/root/a[@attrA]')  
```  
  
 Результат:  
  
```  
<a attrA="1">111</a>  
```  
  
 Дополнительные сведения об указании предикатов в выражении пути см. в разделе [Указание предикатов в шаге выражения пути](../xquery/path-expressions-specifying-predicates.md).  
  
 Следующий пример производит построение выражения последовательности из поддеревьев, а затем применяет к последовательности фильтр.  
  
```  
declare @x xml  
set @x = '  
<a>  
  <c>C under a</c>  
</a>  
<b>    
   <c>C under b</c>  
</b>  
<c>top level c</c>  
<d></d>  
'  
```  
  
 Выражение в `(/a, /b)` конструирует последовательность с поддеревьями `/a` и `/b`, и из результирующей последовательности отфильтровывается элемент `<c>`.  
  
```  
SELECT @x.query('  
  (/a, /b)/c  
')  
```  
  
 Результат:  
  
```  
<c>C under a</c>  
<c>C under b</c>  
```  
  
 Следующий пример показывает применение фильтра предиката. Выражение находит элементы <`a`> и <`b`>, содержащих элемент <`c`>.  
  
```  
declare @x xml  
set @x = '  
<a>  
  <c>C under a</c>  
</a>  
<b>    
   <c>C under b</c>  
</b>  
  
<c>top level c</c>  
<d></d>  
'  
SELECT @x.query('  
  (/a, /b)[c]  
')  
```  
  
 Результат:  
  
```  
<a>  
  <c>C under a</c>  
</a>  
<b>  
  <c>C under b</c>  
</b>  
```  
  
### <a name="implementation-limitations"></a>Ограничения реализации  
 Существуют следующие ограничения:  
  
-   Не поддерживается XQuery-выражение RANGE.  
  
-   Последовательности должны быть однородными. В частности, все элементы последовательности должны быть узлами или атомарными значениями. Эта проверка выполняется статически.  
  
-   Не поддерживается комбинирование последовательностей узлов операторами union, intersect и except.  
  
## <a name="see-also"></a>См. также  
 [Выражения языка XQuery](../xquery/xquery-expressions.md)  
  
  
