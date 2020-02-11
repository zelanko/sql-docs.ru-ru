---
title: Удаление строк по закладке с помощью SQLBulkOperations | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data updates [ODBC], SQLBulkOperations
- SQLBulkOperations function [ODBC], deleting rows
- updating data [ODBC], SQLBulkOperations
ms.assetid: 46139ec9-7095-481a-bf45-20200a2fdc03
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a34f96dd7f5c2f0e2ac4bbb3feae06ea4856a248
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68076808"
---
# <a name="deleting-rows-by-bookmark-with-sqlbulkoperations"></a>Удаление строк по закладкам с помощью SQLBulkOperations
При удалении строки по закладке **SQLBulkOperations** позволяет источнику данных удалить одну или несколько выбранных строк таблицы. Строки определяются закладкой в связанном столбце закладки.  
  
 Чтобы удалить строки по закладке с помощью **SQLBulkOperations**, приложение выполняет следующие действия:  
  
1.  Извлекает и кэширует закладки всех удаляемых строк. Если используется более одной закладки и привязки на уровне столбца, закладки хранятся в массиве. Если используется более одной закладки и привязки на уровне строк, закладки хранятся в массиве структур строк.  
  
2.  Задает для атрибута SQL_ATTR_ROW_ARRAY_SIZE инструкции число закладок и привязывает буфер, содержащий значение закладки, или массив закладок к столбцу 0.  
  
3.  Вызывает **SQLBulkOperations** с параметром *Operation* , имеющим значение SQL_DELETE_BY_BOOKMARK.
