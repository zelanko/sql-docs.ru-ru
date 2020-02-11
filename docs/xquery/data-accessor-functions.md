---
title: Функции методов доступа к данным | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- data-accessor functions [XQuery]
ms.assetid: 31bad04f-7c74-4773-9f83-612704fdd21c
author: rothja
ms.author: jroth
ms.openlocfilehash: b3726686a2c0e5229a0fccf4d9f51c0e1404f1a3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68038949"
---
# <a name="data-accessor-functions"></a>Функции метода доступа к данным
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  В темах этого раздела приводятся и обсуждаются образцы кода с использованием функций доступа к данным.  
  
## <a name="understanding-fndata-fnstring-and-text"></a>Основные сведения о функциях fn:data(), fn:string(), и text()  
 В XQuery имеется функция **fn: data ()** для извлечения скалярных, типизированных значений из узлов, тестового **текста узла ()** для возврата текстовых узлов и функции **fn: String ()** , возвращающей строковое значение узла. Их применение понятно далеко не всем. Ниже приведены рекомендации по правильному использованию этих функций в [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. В целях иллюстрации \<используется экземпляр XML\<age>12/Age>.  
  
-   Нетипизированный XML: выражение пути/аже/текст () возвращает текстовый узел "12". Функции fn:data(/age) и fn:string(/age) возвращают строковое значение«12».  
  
-   Типизированный XML: выражение/аже/текст () возвращает статическую ошибку для любого простого типизированного \<элемента> Age. С другой стороны, функция fn:data(/age) возвращает целое число 12. Функция fn:string(/age) возвращает строку «12».  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Строковая функция &#40;XQuery&#41;](../xquery/data-accessor-functions-string-xquery.md)  
  
-   [Функция данных &#40;XQuery&#41;](../xquery/data-accessor-functions-data-xquery.md)  
  
## <a name="see-also"></a>См. также:  
 [Выражения пути &#40;XQuery&#41;](../xquery/path-expressions-xquery.md)  
  
  
