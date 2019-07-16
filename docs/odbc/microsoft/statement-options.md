---
title: Параметры инструкции | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- custom statement options [ODBC]
- statement options [ODBC]
- ODBC driver for Oracle [ODBC], statement options
ms.assetid: cd73b769-c8b5-43e0-9f80-b3011b7a6162
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 3bf99aace8b058e429898846466294cc42612070
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67948832"
---
# <a name="statement-options"></a>Параметры инструкции
> [!IMPORTANT]  
>  Этот компонент будет удален в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте драйвер ODBC, предоставляемого корпорацией Oracle.  
  
 Эти параметры позволяют настройки конкретного выполнения инструкции в пределах приложения.  
  
|Параметр инструкции|Примечания|  
|----------------------|-----------|  
|SQL_BIND_TYPE|Не может превышать 2 147 483 647 байт или доступной памяти.|  
|SQL_CONCURRENCY|Допустимые значения см. в разделе [типа курсора и параллелизма сочетания](../../odbc/microsoft/cursor-type-and-concurrency-combinations.md).|  
|SQL_CURSOR_TYPE|Драйвер не поддерживает SQL_CURSOR_DYNAMIC. См. в разделе [SQLSetScrollOptions](../../odbc/microsoft/level-2-api-functions-odbc-driver-for-oracle.md) Дополнительные сведения. Допустимые значения см. в разделе [типа курсора и параллелизма сочетания](../../odbc/microsoft/cursor-type-and-concurrency-combinations.md).|  
|SQL_GET_BOOKMARK|Возвращает значение 32-разрядное целое число, — это закладка для номер текущей записи. Get. Невозможно задать.|  
|SQL_KEYSET_SIZE|Можно установить только значение 0.|  
|SQL_MAX_ROWS|Задать максимальное число строк, возвращаемых из результата.|  
|SQL_ROW_NUMBER|Возвращает 32-разрядное целое число, указывающее позицию текущей строки в результирующем наборе. Get. Невозможно задать.|  
|SQL_ROWSET_SIZE|Не может превышать 4 294 967 296 строк; Тем не менее необходимо иметь достаточный объем виртуальной памяти в компьютер, чтобы обработать запрос.|  
|SQL_USE_BOOKMARKS|Поддерживает задание SQL_USE_BOOKMARKS для SQL_UB_ON и предоставляет закладки фиксированной длины.|
