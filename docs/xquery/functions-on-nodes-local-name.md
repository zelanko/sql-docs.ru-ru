---
title: "Функция local-name (XQuery) | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
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
- fn:local-name function
- local-name function
ms.assetid: c901ef5d-89c5-482a-bf64-3eefbcf3098d
caps.latest.revision: 14
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 2e14710fd6503744b93988b004f394164a5b3fa3
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="functions-on-nodes---local-name"></a>Функции на узлах - локального имени
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Возвращает локальную часть имени *$arg* типа xs: String, которое может быть строка нулевой длины или будет иметь лексическую форму xs: NCName. Если аргумент не указан, по умолчанию используется узел контекста.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
fn:local-name() as xs:string  
fn:local-name($arg as node()?) as xs:string  
```  
  
## <a name="arguments"></a>Аргументы  
 *$arg*  
 Имя узла, локальную часть имени которого нужно получить.  
  
## <a name="remarks"></a>Замечания  
  
-   В SQL Server **fn: local-name()** без аргумента может использоваться только в контексте контекстно зависимого предиката. Точнее, ее использование возможно только внутри квадратных скобок (`[ ]`).  
  
-   Если аргумент указан и представляет собой пустую последовательность, функция возвращает строку нулевой длины.  
  
-   Если целевой узел не имеет имени (например, узел документа, комментарий или текстовый узел), функция возвращает строку нулевой длины.  
  
## <a name="examples"></a>Примеры  
 В этом разделе приведены примеры запросов XQuery к экземплярам XML, которые хранятся в различных **xml** столбцов типа в базе данных AdventureWorks.  
  
### <a name="a-retrieve-local-name-of-a-specific-node"></a>A. Получение локального имени конкретного узла  
 Следующий запрос обращается к нетипизированному экземпляру XML. Выражение запроса `local-name(/ROOT[1])` получает локальную часть имени указанного узла.  
  
```  
declare @x xml  
set @x='<ROOT><a>111</a></ROOT>'  
SELECT @x.query('local-name(/ROOT[1])')  
-- result = ROOT  
```  
  
 Следующий запрос обращается к столбцу «Instructions» типа xml таблицы ProductModel. Выражение `local-name(/AWMI:root[1]/AWMI:Location[1])` возвращает локальное имя `Location` указанного узла.  
  
```  
SELECT Instructions.query('  
declare namespace AWMI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions" ;  
     local-name(/AWMI:root[1]/AWMI:Location[1])') as Result  
FROM Production.ProductModel  
WHERE ProductModelID=7  
-- result = Location  
```  
  
### <a name="b-using-local-name-without-argument-in-a-predicate"></a>Б. Использование локального имени без аргумента в предикате  
 Следующий запрос адресован столбцу Instructions, типизированного **xml** столбец в таблице ProductModel. Выражение возвращает все дочерние элементы, узла <`root`>, у которого локальная часть имени QName равна «Location». **Local-name()** функция указаны в предикате и не имеет аргументов функция использует узел контекста.  
  
```  
SELECT Instructions.query('  
declare namespace AWMI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions" ;  
  /AWMI:root//*[local-name() = "Location"]') as Result  
FROM Production.ProductModel  
WHERE ProductModelID=7  
```  
  
 Запрос возвращает все дочерние элементы <`Location`> узла <`root`>.  
  
## <a name="see-also"></a>См. также:  
 [Функции на узлах](http://msdn.microsoft.com/library/09a8affa-3341-4f50-aebc-fdf529e00c08)   
 [uri пространства имен функция &#40; XQuery &#41;](../xquery/functions-on-nodes-namespace-uri.md)  
  
  
