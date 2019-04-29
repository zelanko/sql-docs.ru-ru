---
title: Удаление строк по закладкам с помощью SQLBulkOperations | Документация Майкрософт
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
manager: craigg
ms.openlocfilehash: 5895a106c389afe2d1979cf8d9c16e92f570538a
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63049947"
---
# <a name="deleting-rows-by-bookmark-with-sqlbulkoperations"></a>Удаление строк по закладкам с помощью SQLBulkOperations
При удалении строки по закладкам, **SQLBulkOperations** позволяет удалить один или несколько выбранных строк таблицы источника данных. Строки идентифицируются по закладкам в столбце привязанного закладки.  
  
 Для удаления строк по закладкам с **SQLBulkOperations**, приложение выполняет следующие:  
  
1.  Получает и кэширует закладки всех строк для удаления. Если имеется более одного закладки и используется привязка на уровне столбцов, закладки, хранятся в массиве. Если имеется более одного закладки и используется привязка на уровне строки, закладки, хранятся в массив структур строк.  
  
2.  Устанавливает атрибут SQL_ATTR_ROW_ARRAY_SIZE инструкции число закладок и привязывает буфер, содержащий значение, или массив, закладок, столбец 0.  
  
3.  Вызовы **SQLBulkOperations** с *операции* присвоено SQL_DELETE_BY_BOOKMARK.
