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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67948832"
---
# <a name="statement-options"></a>Параметры инструкции
> [!IMPORTANT]  
>  Эта функция будет удалена в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте драйвер ODBC, предоставляемый Oracle.  
  
 Эти параметры позволяют настраивать конкретную инструкцию выполнения в приложении.  
  
|Параметр инструкции|Заметки|  
|----------------------|-----------|  
|SQL_BIND_TYPE|Не может превышать 2 147 483 647 байт или объем доступной памяти.|  
|SQL_CONCURRENCY|Сведения о допустимых значениях см. в разделе [сочетания типа курсора и параллелизма](../../odbc/microsoft/cursor-type-and-concurrency-combinations.md).|  
|SQL_CURSOR_TYPE|Драйвер не допускает SQL_CURSOR_DYNAMIC. Дополнительные сведения см. в разделе [SQLSetScrollOptions](../../odbc/microsoft/level-2-api-functions-odbc-driver-for-oracle.md) . Сведения о допустимых значениях см. в разделе [сочетания типа курсора и параллелизма](../../odbc/microsoft/cursor-type-and-concurrency-combinations.md).|  
|SQL_GET_BOOKMARK|Возвращает 32-разрядное целочисленное значение, которое является закладкой для номера текущей записи. Только получение; не удается задать значение.|  
|SQL_KEYSET_SIZE|Можно задать только значение 0.|  
|SQL_MAX_ROWS|Максимальное число строк, возвращаемых из результирующего набора.|  
|SQL_ROW_NUMBER|Возвращает 32-разрядное целое число, указывающее расположение текущей строки в результирующем наборе. Только получение; не удается задать значение.|  
|SQL_ROWSET_SIZE|Не может превышать 4 294 967 296 строк; Однако для выполнения запроса требуется достаточно виртуальной памяти на компьютере.|  
|SQL_USE_BOOKMARKS|Поддерживает параметр SQL_USE_BOOKMARKS для SQL_UB_ON и предоставляет закладки фиксированной длины.|
