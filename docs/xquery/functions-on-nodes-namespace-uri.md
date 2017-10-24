---
title: "uri пространства имен, функция (XQuery) | Документы Microsoft"
ms.custom: 
ms.date: 08/09/2016
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
- fn:namespace-uri function
- namespace-uri function
ms.assetid: 9b48d216-26c8-431d-9ab4-20ab187917f4
caps.latest.revision: 14
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 89c8cf916143a1041c340aeea48642c87c1d17cd
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="functions-on-nodes---namespace-uri"></a>Функции на узлах - uri пространства имен
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает пространство имен URI QName, заданное в *$arg* как xs: String.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
fn:namespace-uri() as xs:string  
fn:namespace-uri($arg as node()?) as xs:string  
```  
  
## <a name="arguments"></a>Аргументы  
 *$arg*  
 Имя узла, для которого будет получена часть URI-кода пространства имен.  
  
## <a name="remarks"></a>Замечания  
  
-   Если аргумент опускается, значением по умолчанию является узел контекста.  
  
-   В SQL Server **fn:namespace-uri()** без аргумента может использоваться только в контексте контекстно зависимого предиката. Точнее, она может использоваться только внутри квадратных скобок ([ ]).  
  
-   Если *$arg* представляет собой пустую последовательность, возвращается строка нулевой длины.  
  
-   Если *$arg* — это элемент или узел атрибута которого расширенное имя QName не находится в пространстве имен, функция возвращает строку нулевой длины  
  
## <a name="examples"></a>Примеры  
 В этом разделе приведены примеры запросов XQuery к экземплярам XML, хранящимся в различных **xml** столбцов типа в базе данных AdventureWorks.  
  
### <a name="a-retrieve-namespace-uri-of-a-specific-node"></a>A. Получение URI-адреса пространства имен определенного узла  
 Следующий запрос обращается к нетипизированному экземпляру XML. В выражении запроса выражение `namespace-uri(/ROOT[1])` получает часть URI-кода пространства имен указанного узла.  
  
```  
set @x='<ROOT><a>111</a></ROOT>'  
SELECT @x.query('namespace-uri(/ROOT[1])')  
```  
  
 Так как указанное имя QName не содержит части URI-кода пространства имен, а только часть локального имени, результатом будет строка нулевой длины.  
  
 Следующий запрос адресован инструкциям типизированные **xml** столбца. Выражение `namespace-uri(/AWMI:root[1]/AWMI:Location[1])` возвращает URI-код пространства имен первого дочернего элемента <`Location`> элемента <`root`>.  
  
```  
SELECT Instructions.query('  
declare namespace AWMI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions" ;  
     namespace-uri(/AWMI:root[1]/AWMI:Location[1])') as Result  
FROM Production.ProductModel  
WHERE ProductModelID=7  
```  
  
 Результат:  
  
```  
http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions  
```  
  
### <a name="b-using-namespace-uri-without-argument-in-a-predicate"></a>Б. Использование функции namespace-uri() без аргумента в предикате  
 Следующий запрос указывается в типизированном столбце xml типа CatalogDescription. Выражение возвращает все узлы элементов, чей URI-код пространства имен является адресом `http://www.adventure-works.com/schemas/OtherFeatures`. Пространства имен -**uri()** функция указывается без аргумента и использует узел контекста.  
  
```  
SELECT CatalogDescription.query('  
declare namespace p1="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
   /p1:ProductDescription//*[namespace-uri() = "http://www.adventure-works.com/schemas/OtherFeatures"]  
') as Result  
FROM Production.ProductModel  
WHERE ProductModelID=19  
```  
  
 Частичный результат:  
  
```  
<p1:wheel xmlns:p1="http://www.adventure-works.com/schemas/OtherFeatures">High performance wheels.</p1:wheel>  
<p2:saddle xmlns:p2="http://www.adventure-works.com/schemas/OtherFeatures">  
  <p3:i xmlns:p3="http://www.w3.org/1999/xhtml">Anatomic design</p3:i> and made from durable leather for a full-day of riding in comfort.</p2:saddle>  
…  
```  
  
 Пространство имен URI в предыдущем запросе можно изменить на адрес `http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain`. Тогда будут получены все дочерние узлы элемента <`ProductDescription`>, чья часть URI-кода пространства имен расширенного QName является адресом `http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain`.  
  
### <a name="implementation-limitations"></a>Ограничения реализации  
 Существуют следующие ограничения:  
  
-   **Namespace-uri()** функция возвращает экземпляры типа xs: String вместо xs: anyURI.  
  
## <a name="see-also"></a>См. также:  
 [Функции на узлах](http://msdn.microsoft.com/library/09a8affa-3341-4f50-aebc-fdf529e00c08)   
 [Функция локального имени &#40; XQuery &#41;](../xquery/functions-on-nodes-local-name.md)  
  
  

