---
title: Длина типа данных Interval | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- data types [ODBC], interval data types
- length of data types [ODBC]
- interval data type [ODBC], length
ms.assetid: e9eb38d8-f9db-4401-8c62-aa394054cbbf
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 67cfccf9823f59e02ece652acc35f26b07e3ce89
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="interval-data-type-length"></a>Длина типа данных Interval
Следующие правила используются для определения длины типа данных интервал в символах. Длина выражается в символах. Число байтов зависит от набора символов. Включает сложением следующих значений:  
  
-   Два символа для каждого поля в интервале, который не является ведущим поля.  
  
-   Начальные в поле число символов, которое явных или неявных главного параметра точности. Если начальные точности не указан, значение по умолчанию — 2.  
  
-   Один символ в качестве разделителя между полями.  
  
-   Единица плюс явных или подразумеваемых секунды. Если точность секунды не указан, значение по умолчанию — 6.  
  
 Конкретные длина значения столбцов для каждого типа данных interval содержатся в [размер столбца](../../../odbc/reference/appendixes/column-size.md).
