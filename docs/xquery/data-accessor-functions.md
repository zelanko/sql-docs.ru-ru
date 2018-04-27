---
title: Функции доступа к данным | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql
ms.service: ''
ms.component: xquery
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
dev_langs:
- XML
helpviewer_keywords:
- data-accessor functions [XQuery]
ms.assetid: 31bad04f-7c74-4773-9f83-612704fdd21c
caps.latest.revision: 30
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f70f14b553182c4f52d9c27ec0972fd3d5978026
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="data-accessor-functions"></a>Функции метода доступа к данным
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  В темах этого раздела приводятся и обсуждаются образцы кода с использованием функций доступа к данным.  
  
## <a name="understanding-fndata-fnstring-and-text"></a>Основные сведения о функциях fn:data(), fn:string(), и text()  
 Язык XQuery включает функцию **fn: Data()** для извлечения скалярных типизированных значений из узлов, проверку узла **text()** для возврата текстовых узлов, а функция **fn: String()** , возвращающий Строковое значение узла. Их применение понятно далеко не всем. Ниже приведены рекомендации по правильному использованию этих функций в [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Экземпляр XML \<age > 12 \< /age > используется исключительно в демонстрационных целях.  
  
-   Нетипизированный XML: Выражение пути /age/text() возвращает текстовый узел «12». Функции fn:data(/age) и fn:string(/age) возвращают строковое значение«12».  
  
-   Типизированный XML: Выражение /age/text() возвращает статическую ошибку для любого простого типизированного \<age > элемент. С другой стороны, функция fn:data(/age) возвращает целое число 12. Функция fn:string(/age) возвращает строку «12».  
  
## <a name="in-this-section"></a>В этом разделе  
  
-   [Функция String &#40;XQuery&#41;](../xquery/data-accessor-functions-string-xquery.md)  
  
-   [данные функции &#40;XQuery&#41;](../xquery/data-accessor-functions-data-xquery.md)  
  
## <a name="see-also"></a>См. также  
 [Выражения пути &#40;XQuery&#41;](../xquery/path-expressions-xquery.md)  
  
  
