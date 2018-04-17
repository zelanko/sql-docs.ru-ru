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
ms.topic: article
helpviewer_keywords:
- data updates [ODBC], SQLBulkOperations
- SQLBulkOperations function [ODBC], deleting rows
- updating data [ODBC], SQLBulkOperations
ms.assetid: 46139ec9-7095-481a-bf45-20200a2fdc03
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 017286f36c7747e02f1c120d56d38ae47a6e2008
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="deleting-rows-by-bookmark-with-sqlbulkoperations"></a>Удаление строк по закладке с SQLBulkOperations
При удалении строки с закладкой, **SQLBulkOperations** позволяет удалить один или несколько выбранных строк таблицы источника данных. Строки идентифицируются по закладки в столбце привязанного закладки.  
  
 Для удаления строк по закладке с **SQLBulkOperations**, приложение делает следующее:  
  
1.  Получает и кэширует закладки всех строк для удаления. Если имеется более одного закладки и используется привязка на уровне столбцов, закладки хранятся в массиве; Если имеется более одного закладки и привязка, закладки, хранятся в массив структур строк.  
  
2.  Устанавливает атрибут SQL_ATTR_ROW_ARRAY_SIZE инструкции количество закладок и привязывает буфер, содержащий значение или массив закладки для столбца с номером 0.  
  
3.  Вызовы **SQLBulkOperations** с *операции* значение SQL_DELETE_BY_BOOKMARK.
