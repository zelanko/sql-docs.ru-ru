---
title: "Длина типа данных Interval | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data types [ODBC], interval data types
- length of data types [ODBC]
- interval data type [ODBC], length
ms.assetid: e9eb38d8-f9db-4401-8c62-aa394054cbbf
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c3435106f53d791646a16e1ba9c1a55b75c73a79
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="interval-data-type-length"></a>Длина типа данных Interval
Следующие правила используются для определения длины типа данных интервал в символах. Длина выражается в символах. Число байтов зависит от набора символов. Включает сложением следующих значений:  
  
-   Два символа для каждого поля в интервале, который не является ведущим поля.  
  
-   Начальные в поле число символов, которое явных или неявных главного параметра точности. Если начальные точности не указан, значение по умолчанию — 2.  
  
-   Один символ в качестве разделителя между полями.  
  
-   Единица плюс явных или подразумеваемых секунды. Если точность секунды не указан, значение по умолчанию — 6.  
  
 Конкретные длина значения столбцов для каждого типа данных interval содержатся в [размер столбца](../../../odbc/reference/appendixes/column-size.md).
