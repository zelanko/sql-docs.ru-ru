---
title: Длина типа данных Interval | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], interval data types
- length of data types [ODBC]
- interval data type [ODBC], length
ms.assetid: e9eb38d8-f9db-4401-8c62-aa394054cbbf
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 16d0590d3297b52891bf399822ce984674022583
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63188919"
---
# <a name="interval-data-type-length"></a>Длина интервального типа данных
Следующие правила используются для определения длины типа данных интервал в символах. Длина выражается в символах. Число байтов, которое зависит от набора символов. Длина включает в себя следующие значения, добавленные друг с другом:  
  
-   Двух символов для каждого поля в интервале, который не является ведущим поля.  
  
-   Ведущие в поле число символов, явных или неявных главного параметра точности. Если начальные точности не указан, значение по умолчанию — 2.  
  
-   Один символ в качестве разделителя между полями.  
  
-   Один, а также точность секунд явных или подразумеваемых. Если точность секунды не указан, значение по умолчанию — 6.  
  
 Конкретные длина значения столбцов для каждого типа данных interval содержатся в [размер столбца](../../../odbc/reference/appendixes/column-size.md).
