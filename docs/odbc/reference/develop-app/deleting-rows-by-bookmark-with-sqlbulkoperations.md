---
title: Удаление строк по закладке с SQLBulkOperations | Документы Microsoft
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
- data updates [ODBC], SQLBulkOperations
- SQLBulkOperations function [ODBC], deleting rows
- updating data [ODBC], SQLBulkOperations
ms.assetid: 46139ec9-7095-481a-bf45-20200a2fdc03
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 34f328788a48e46a2a6a6cd5759521ce37146943
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="deleting-rows-by-bookmark-with-sqlbulkoperations"></a>Удаление строк по закладке с SQLBulkOperations
При удалении строки с закладкой, **SQLBulkOperations** позволяет удалить один или несколько выбранных строк таблицы источника данных. Строки идентифицируются по закладки в столбце привязанного закладки.  
  
 Для удаления строк по закладке с **SQLBulkOperations**, приложение делает следующее:  
  
1.  Получает и кэширует закладки всех строк для удаления. Если имеется более одного закладки и используется привязка на уровне столбцов, закладки хранятся в массиве; Если имеется более одного закладки и привязка, закладки, хранятся в массив структур строк.  
  
2.  Устанавливает атрибут SQL_ATTR_ROW_ARRAY_SIZE инструкции количество закладок и привязывает буфер, содержащий значение или массив закладки для столбца с номером 0.  
  
3.  Вызовы **SQLBulkOperations** с *операции* значение SQL_DELETE_BY_BOOKMARK.
