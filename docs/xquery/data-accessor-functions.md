---
title: "Функции доступа к данным | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
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
- data-accessor functions [XQuery]
ms.assetid: 31bad04f-7c74-4773-9f83-612704fdd21c
caps.latest.revision: 30
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 456d359fd407e305bc8bfb3b85bd29b7bada8382
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="data-accessor-functions"></a>Функции метода доступа к данным
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  В темах этого раздела приводятся и обсуждаются образцы кода с использованием функций доступа к данным.  
  
## <a name="understanding-fndata-fnstring-and-text"></a>Основные сведения о функциях fn:data(), fn:string(), и text()  
 Язык XQuery включает функцию **fn: Data()** для извлечения скалярных типизированных значений из узлов, проверку узла **text()** для возврата текстовых узлов, а функция **fn: String()** , возвращающий Строковое значение узла. Их применение понятно далеко не всем. Ниже приведены рекомендации по правильному использованию этих функций в [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Экземпляр XML \<age > 12 \< /age > используется исключительно в демонстрационных целях.  
  
-   Нетипизированный XML: Выражение пути /age/text() возвращает текстовый узел «12». Функции fn:data(/age) и fn:string(/age) возвращают строковое значение«12».  
  
-   Типизированный XML: Выражение /age/text() возвращает статическую ошибку для любого простого типизированного \<age > элемент. С другой стороны, функция fn:data(/age) возвращает целое число 12. Функция fn:string(/age) возвращает строку «12».  
  
## <a name="in-this-section"></a>В этом разделе  
  
-   [Строка, функция &#40; XQuery &#41;](../xquery/data-accessor-functions-string-xquery.md)  
  
-   [Функция Data &#40; XQuery &#41;](../xquery/data-accessor-functions-data-xquery.md)  
  
## <a name="see-also"></a>См. также:  
 [Выражения пути &#40; XQuery &#41;](../xquery/path-expressions-xquery.md)  
  
  
