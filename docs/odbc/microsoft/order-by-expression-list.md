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
ms.openlocfilehash: cd88673c4b5309b7463256b85df4f92d6d360b16
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68100796"
---
# <a name="order-by-expression-list"></a>Список выражений ORDER BY
Выражения могут использоваться в предложении ORDER BY. Например, в следующих предложениях Таблица упорядочена по три ключевых выражения: a + b, c + d и e.  
  
```  
SELECT * FROM emp  
ORDER BY a+b,c+d,e  
```  
  
 Упорядочение не разрешена для набора функций или выражение, содержащее функцию set.
