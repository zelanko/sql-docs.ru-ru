---
title: Параметры инструкции | Документы Microsoft
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
ms.topic: conceptual
helpviewer_keywords:
- custom statement options [ODBC]
- statement options [ODBC]
- ODBC driver for Oracle [ODBC], statement options
ms.assetid: cd73b769-c8b5-43e0-9f80-b3011b7a6162
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 75a4eef546e37fea71e88fa5d8926c7b5bd95ac2
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="statement-options"></a>Параметры инструкции
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте драйвер ODBC, предоставляемого корпорацией Oracle.  
  
 Эти параметры позволяют настройки конкретного выполнения инструкции в пределах приложения.  
  
|Параметр инструкции|Примечания|  
|----------------------|-----------|  
|SQL_BIND_TYPE|Не может превышать 2 147 483 647 байт или доступной памятью.|  
|SQL_CONCURRENCY|Допустимые значения см. в разделе [типа курсора и параллелизма сочетания](../../odbc/microsoft/cursor-type-and-concurrency-combinations.md).|  
|SQL_CURSOR_TYPE|Драйвер не допускает SQL_CURSOR_DYNAMIC. В разделе [SQLSetScrollOptions](../../odbc/microsoft/level-2-api-functions-odbc-driver-for-oracle.md) для получения дополнительной информации. Допустимые значения см. в разделе [типа курсора и параллелизма сочетания](../../odbc/microsoft/cursor-type-and-concurrency-combinations.md).|  
|SQL_GET_BOOKMARK|Возвращает 32-разрядное целое значение, — это закладка для номер текущей записи. Получить только; не удалось установить.|  
|SQL_KEYSET_SIZE|Можно присвоить только значение 0.|  
|SQL_MAX_ROWS|Задайте максимальное число строк, возвращаемых из результата.|  
|SQL_ROW_NUMBER|Возвращает 32-разрядное целое число, указывающее позицию текущей строки в результирующем наборе. Получить только; не удалось установить.|  
|SQL_ROWSET_SIZE|Не может превышать 4 294 967 296 строк; Тем не менее необходимо иметь достаточный объем виртуальной памяти в компьютер, чтобы обработать вашу заявку.|  
|SQL_USE_BOOKMARKS|Поддерживает настройку SQL_USE_BOOKMARKS для SQL_UB_ON и предоставляет закладки фиксированной длины.|
