---
title: пространство имен uri-from-QName (XQuery) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- fn:namespace-uri-from-QName function
- namespace-uri-from-QName function
ms.assetid: 4ab3f003-2a3b-4268-9e88-b615e35701b2
author: rothja
ms.author: jroth
ms.openlocfilehash: 96edefd5409520109e2b2155507dd8879ed4b0d3
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67946632"
---
# <a name="functions-related-to-qnames---namespace-uri-from-qname"></a>Функции, связанные с QName — namespace-uri-from-QName
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Возвращает строку, представляющую пространство имен uri QName, заданное *$arg*. Результатом является пустая последовательность, если *$arg* является пустая последовательность.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
namespace-uri-from-QName($arg as xs:QName?) as xs:string?  
```  
  
## <a name="arguments"></a>Аргументы  
 *$arg*  
 QName, для которого возвращается URI-код пространство имен.  
  
## <a name="examples"></a>Примеры  
 В этом разделе приведены примеры запросов XQuery к экземплярам XML, которые хранятся в различных **xml** -столбец базы данных AdventureWorks.  
  
### <a name="a-retrieve-the-namespace-uri-from-a-qname"></a>A. Получение URI-адреса пространства имен из QName  
 Работающий пример см. в разделе [local-name-from-QName &#40;XQuery&#41;](../xquery/functions-related-to-qnames-local-name-from-qname.md).  
  
### <a name="implementation-limitations"></a>Ограничения реализации  
 Существуют следующие ограничения:  
  
-   **Namespace-uri-from-QName()** функция возвращает экземпляры xs: String вместо xs: anyURI.  
  
## <a name="see-also"></a>См. также  
 [Функции, связанные с QName &#40;XQuery&#41;](https://msdn.microsoft.com/library/7e07eb26-f551-4b63-ab77-861684faff71)  
  
  
