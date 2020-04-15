---
title: Параметры заявления Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ca40765dff98e9102fbe36e88c7e79535f311d97
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299214"
---
# <a name="statement-options"></a>Параметры инструкции
> [!IMPORTANT]  
>  Эта функция будет удалена в будущей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте драйвер ODBC, предоставленный Oracle.  
  
 Эти параметры позволяют настроить конкретную выписку исполнения в приложении.  
  
|Опция оператора|Примечания|  
|----------------------|-----------|  
|SQL_BIND_TYPE|Не может превышать 2 147 483 647 байтов или доступной памяти.|  
|SQL_CONCURRENCY|Для допустимых значений см. [Cursor Type and Concurrency Combinations](../../odbc/microsoft/cursor-type-and-concurrency-combinations.md)|  
|SQL_CURSOR_TYPE|Водитель не позволяет SQL_CURSOR_DYNAMIC. Для получения [дополнительной информации ознакомьтесь с информацией о S'LSetScrollOptions.](../../odbc/microsoft/level-2-api-functions-odbc-driver-for-oracle.md) Для допустимых значений см. [Cursor Type and Concurrency Combinations](../../odbc/microsoft/cursor-type-and-concurrency-combinations.md)|  
|SQL_GET_BOOKMARK|Возвращает 32-битное значение, которое является закладкой для текущего рекордного числа. Получить только; не может установить.|  
|SQL_KEYSET_SIZE|Может быть установлен только до 0.|  
|SQL_MAX_ROWS|Максимальное количество строк, чтобы вернуться из набора результатов.|  
|SQL_ROW_NUMBER|Возвращает 32-битный ряд с указанием положения текущей строки в наборе результатов. Получить только; не может установить.|  
|SQL_ROWSET_SIZE|Не может превышать 4 294 967 296 строк; однако, вы должны иметь достаточно виртуальной памяти в вашем компьютере для обработки вашего запроса.|  
|SQL_USE_BOOKMARKS|Поддерживает настройку SQL_USE_BOOKMARKS для SQL_UB_ON и предоставляет закладки фиксированной длины.|
