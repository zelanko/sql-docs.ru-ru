---
title: "пространство имен uri с-имя QName (XQuery) | Документы Microsoft"
ms.custom: 
ms.date: 03/04/2017
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
- fn:namespace-uri-from-QName function
- namespace-uri-from-QName function
ms.assetid: 4ab3f003-2a3b-4268-9e88-b615e35701b2
caps.latest.revision: 13
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: be3af81f884ff54ff6bea5f07f97d31cf0ad2342
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="functions-related-to-qnames---namespace-uri-from-qname"></a>Функции, связанные с QNames - uri пространства имен из QName
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Возвращает строку, представляющую пространство имен uri QName, заданное *$arg*. Результатом является пустая последовательность, если *$arg* представляет собой пустую последовательность.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
namespace-uri-from-QName($arg as xs:QName?) as xs:string?  
```  
  
## <a name="arguments"></a>Аргументы  
 *$arg*  
 QName, для которого возвращается URI-код пространство имен.  
  
## <a name="examples"></a>Примеры  
 В этом разделе приведены примеры запросов XQuery к экземплярам XML, которые хранятся в различных **xml** столбцов типа в базе данных AdventureWorks.  
  
### <a name="a-retrieve-the-namespace-uri-from-a-qname"></a>A. Получение URI-адреса пространства имен из QName  
 Работающий пример см. в разделе [локального имени из QName &#40; XQuery &#41; ](../xquery/functions-related-to-qnames-local-name-from-qname.md).  
  
### <a name="implementation-limitations"></a>Ограничения реализации  
 Существуют следующие ограничения:  
  
-   **Namespace-uri-from-QName()** функция возвращает экземпляры xs: String вместо xs: anyURI.  
  
## <a name="see-also"></a>См. также:  
 [Функции, связанные с QNames &#40; XQuery &#41;](http://msdn.microsoft.com/library/7e07eb26-f551-4b63-ab77-861684faff71)  
  
  

