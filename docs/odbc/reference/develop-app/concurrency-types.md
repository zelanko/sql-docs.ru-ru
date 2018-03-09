---
title: "Типы параллелизма | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- transactions [ODBC], concurrency control
- concurrency control [ODBC]
- locking concurrency control [ODBC]
- optimistic concurrency [ODBC]
- read-only concurrency control [ODBC]
ms.assetid: 46762ae5-17dd-4777-968e-58156f470fe1
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8f911bf93a0a61e911ef0795059fbbaadd2cfff7
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="concurrency-types"></a>Типы параллелизма
Для решения проблемы снижения параллелизма курсоров ODBC предоставляет четыре различных типа параллелизм курсоров:  
  
-   **Только для чтения** курсора можно считывать данные, но не может обновлять или удалять данные. Это тип параллелизма по умолчанию. Несмотря на то, что СУБД могут привести к блокировке строк для обеспечения изоляции Repeatable Read и уровни изоляции Serializable, его можно использовать блокировки чтения вместо блокировки записи. Это приводит к повышению параллелизма, так как другие транзакции могут как минимум на чтение данных.  
  
-   **Блокировка** курсор использует нижнего уровня блокировки, необходимые, чтобы убедиться в том, он может обновлять или удалять строки в результирующем наборе. Это обычно приводит к очень небольшое число параллельных уровней, особенно на уровнях изоляции транзакции Repeatable Read и Serializable.  
  
-   **Оптимистичного параллелизма при помощи версий строк и оптимистический параллелизм, используя значения** курсор использует оптимистический параллелизм: он обновляет или удаляет строки только в том случае, если они не были изменены, так как они были последнего чтения. Для обнаружения изменений, он сравнивает версии строк или значений. Нет никакой гарантии, курсор будет иметь возможность обновить или удалить строку, что значительно больше, чем при использовании блокировки параллелизма. Дополнительные сведения в следующем разделе, [оптимистичного параллелизма](../../../odbc/reference/develop-app/optimistic-concurrency.md).  
  
 Приложение указывает, какой тип параллелизма ему курсор для использования с помощью атрибута инструкции SQL_ATTR_CONCURRENCY. Чтобы определить, какие типы поддерживаются, он вызывает **SQLGetInfo** с параметром SQL_SCROLL_CONCURRENCY.
