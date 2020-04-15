---
title: Вставка строк с помощью S'LBulkOperations (ru) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLBulkOperations function [ODBC], inserting rows
- data updates [ODBC], SQLBulkOperations
- updating data [ODBC], SQLBulkOperations
ms.assetid: ed585ea7-4d56-4df9-8dc3-53ca82382450
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a6fa384292f02026b8390aa92525144dce6f549b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300114"
---
# <a name="inserting-rows-with-sqlbulkoperations"></a>Вставка строк с помощью SQLBulkOperations
Вставка данных с **помощью S'LBulkOperations** аналогична обновлению данных с **помощью S'LBulkOperations,** поскольку в ней используются данные из буферов связанных приложений.  
  
 Так что каждый столбец в новой строке имеет значение, все связанные столбцы со значением длины/индикатора SQL_COLUMN_IGNORE и все несвязанные столбцы должны либо принимать значения NULL, либо иметь значение по умолчанию.  
  
 Для вставки строк с **помощью S'LBulkOperations**приложение выполняет следующее:  
  
1.  Устанавливает атрибут SQL_ATTR_ROW_ARRAY_SIZE оператора на количество строк для вставки и помещает новые значения данных в связанные буферы приложения. Для получения информации о том, как отправлять [Long Data and SQLSetPos and SQLBulkOperations](../../../odbc/reference/develop-app/long-data-and-sqlsetpos-and-sqlbulkoperations.md)длинные данные с **помощью S'LBulkOperations,** см.  
  
2.  Устанавливает значение в буфере длины/индикатора каждого столбца по мере необходимости. Это длина данных или SQL_NTS для столбцов, привязанных к строке буферов, длина байт данных для столбцов, привязанных к бинарным буферам, и SQL_NULL_DATA для любых столбцов, которые будут установлены на NULL. Приложение устанавливает значение в буфере длины/индикатора тех столбцов, которые должны быть установлены по умолчанию (если он существует) или NULL (если нет) для SQL_COLUMN_IGNORE.  
  
3.  Вызывает **S'LBulkOperations** с аргументом *операции,* установленным для SQL_ADD.  
  
 После возврата **s'LBulkOperations** текущая строка остается неизменной. Если столбец закладки (колонка 0) связан, **S'LBulkOperations** возвращает закладки вставленных строк в буфере строки, привязанные к этому столбику.
