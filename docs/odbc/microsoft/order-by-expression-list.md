---
title: Список выражений ORDER BY | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ORDER BY clause [ODBC]
- SQL grammar [ODBC], order by clause
ms.assetid: 5ef88186-a99f-4e2c-a3f3-98a42d4f03a5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4c6be518211edb07251ff9234b095f3d3dde248b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63024275"
---
# <a name="order-by-expression-list"></a>Список выражений ORDER BY
Выражения могут использоваться в предложении ORDER BY. Например, в следующих предложениях Таблица упорядочена по три ключевых выражения: a + b, c + d и e.  
  
```  
SELECT * FROM emp  
ORDER BY a+b,c+d,e  
```  
  
 Упорядочение не разрешена для набора функций или выражение, содержащее функцию set.
