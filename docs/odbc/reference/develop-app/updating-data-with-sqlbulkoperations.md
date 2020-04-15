---
title: Обновление данных с помощью S'LBulkOperations (ru) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLBulkOperations function [ODBC], updating data
- data updates [ODBC], SQLBulkOperations
- updating data [ODBC], SQLBulkOperations
ms.assetid: 7645a704-341e-4267-adbe-061a9fda225b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9b96e3a43b8385910e4260cf51dea7e4ff508200
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298488"
---
# <a name="updating-data-with-sqlbulkoperations"></a>Обновление данных с помощью SQLBulkOperations
Приложения могут выполнять операции по массовому обновлению, удалению, извлечению или вставке в основной таблице в источнике данных с вызовом на **S'LBulkOperations.** Вызов **sLBulkOperations** является удобной альтернативой построению и исполнинию оператора S'L. Это позволяет драйверу ODBC поддерживать позиционированные обновления, даже если источник данных не поддерживает позиционированные операторы S'L. Это часть парадигмы достижения полного доступа к базе данных с помощью функциональных вызовов.  
  
 **СЗЛБалКОперации** работают на текущей панели и могут быть использованы только после звонка в **S'LFetch** или **S'LFetchScroll.** Приложение определяет строки для обновления, удаления или обновления путем кэширования их закладок. Драйвер извлекает новые данные для обновления строк или новые данные, которые будут вставлены в базовую таблицу, из буферов строки.  
  
 Размер строки, который будет использоваться в **S'LBulkOperations,** устанавливается вызовом в **S'LSetStmtAttr** с аргументом *атрибута* SQL_ATTR_ROW_ARRAY_SIZE. В отличие от **S'LSetPos,** который использует новый размер рядового только после звонка в **S'LFetch,** **sLFetchScroll,** **S'LBulkOperations** использует новый размер строки после звонка в **S'LSetStmtAttr.**  
  
 Поскольку большинство взаимодействий с реляционными базами данных осуществляется с помощью S'L, **S'LBulkOperations** не пользуется широкой поддержкой. Тем не менее, водитель может легко подражать ему, сооружая и исполняя **ОБНОВЛЕНИЕ,** **DELETE**, или **заявление INSERT.**  
  
 Чтобы определить, какие операции поддерживает **sLBulkOperation,** приложение вызывает **s'LGetInfo** с SQL_DYNAMIC_CURSOR_ATTRIBUTES1, SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1, SQL_KEYSET_CURSOR_ATTRIBUTES1 или SQL_STATIC_CURSOR_ATTRIBUTES1 информации (в зависимости от типа курсора).  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Обновление строк по закладкам с помощью SQLBulkOperations](../../../odbc/reference/develop-app/updating-rows-by-bookmark-with-sqlbulkoperations.md)  
  
-   [Удаление строк по закладкам с помощью SQLBulkOperations](../../../odbc/reference/develop-app/deleting-rows-by-bookmark-with-sqlbulkoperations.md)  
  
-   [Вставка строк с помощью SQLBulkOperations](../../../odbc/reference/develop-app/inserting-rows-with-sqlbulkoperations.md)  
  
-   [Выборка строк с помощью SQLBulkOperations](../../../odbc/reference/develop-app/fetching-rows-with-sqlbulkoperations.md)
