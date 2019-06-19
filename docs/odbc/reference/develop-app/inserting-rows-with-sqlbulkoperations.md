---
title: Вставка строк с помощью SQLBulkOperations | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2b5dac8ae14f01dd464aab42eaed42480f1e715c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62446805"
---
# <a name="inserting-rows-with-sqlbulkoperations"></a>Вставка строк с помощью SQLBulkOperations
Вставка данных с **SQLBulkOperations** аналогично обновлению данных с помощью **SQLBulkOperations** , так как он использует данные из связанного приложения буферов.  
  
 Таким образом, чтобы каждый столбец в новой строке имеет значение, все присоединенные столбцы со значением длины и индикатора SQL_COLUMN_IGNORE и все непривязанные столбцы должны либо принимать значения NULL или иметь значение по умолчанию.  
  
 Вставить строки с **SQLBulkOperations**, приложение выполняет следующие:  
  
1.  Устанавливает атрибут SQL_ATTR_ROW_ARRAY_SIZE инструкции число вставляемых строк и помещает новые значения данных в буферах привязанного приложения. Сведения о том, как для отправления объемных данных с помощью **SQLBulkOperations**, см. в разделе [длинных данных и функции SQLSetPos и SQLBulkOperations](../../../odbc/reference/develop-app/long-data-and-sqlsetpos-and-sqlbulkoperations.md).  
  
2.  Задает значение в буфер длины/индикатора каждого столбца, при необходимости. Это байтовая длина данных или SQL_NTS для столбцов, привязанных к буферам строк байтовая длина данных для столбцов, привязанных к двоичных буферах и SQL_NULL_DATA для всех столбцов будет присвоено значение NULL. Приложение задает значение в буфер длины/индикатора тех столбцов, которые требуется задать по умолчанию (если он существует) или значение NULL (если нет) SQL_COLUMN_IGNORE.  
  
3.  Вызовы **SQLBulkOperations** с *операции* аргумент значение SQL_ADD.  
  
 После **SQLBulkOperations** возвращает текущую строку без изменений. Если закладка столбца (0) привязаны, **SQLBulkOperations** возвращает закладки вставляемых строк в буфере строк, привязанного к этому столбцу.
