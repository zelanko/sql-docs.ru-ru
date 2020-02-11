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
ms.openlocfilehash: 05b8f71d6f4c885c7dc64887dd92b1f600005ca7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68138921"
---
# <a name="inserting-rows-with-sqlbulkoperations"></a>Вставка строк с помощью SQLBulkOperations
Вставка данных с помощью **SQLBulkOperations** аналогична обновлению данных с помощью **SQLBulkOperations** , поскольку они используют данные из привязанных буферов приложений.  
  
 Чтобы каждый столбец в новой строке имел значение, все связанные столбцы с значением длины или индикатора SQL_COLUMN_IGNORE и всеми несвязанными столбцами должны принимать значения NULL или иметь значение по умолчанию.  
  
 Чтобы вставить строки с помощью **SQLBulkOperations**, приложение выполняет следующие действия:  
  
1.  Устанавливает атрибут инструкции SQL_ATTR_ROW_ARRAY_SIZE в число вставляемых строк и помещает новые значения в связанные буферы приложения. Сведения о том, как отправить длинные данные с помощью **SQLBulkOperations**, см. в разделе [Long Data and SQLSetPos and SQLBulkOperations](../../../odbc/reference/develop-app/long-data-and-sqlsetpos-and-sqlbulkoperations.md).  
  
2.  При необходимости устанавливает значение в буфере длины и индикатора для каждого столбца. Это длина байта данных или SQL_NTS для столбцов, привязанных к буферам строк, длина байтов данных для столбцов, привязанных к двоичным буферам, и SQL_NULL_DATA для всех столбцов, для которых задано значение NULL. Приложение задает значение в буфере длины или индикатора для столбцов, которые должны быть установлены в значения по умолчанию (если они существуют), или значение NULL (если оно не определено) для SQL_COLUMN_IGNORE.  
  
3.  Вызывает **SQLBulkOperations** с аргументом *операции* , для которого задано значение SQL_ADD.  
  
 После возврата **SQLBulkOperations** текущая строка не изменяется. Если столбец закладки (столбец 0) привязан, **SQLBulkOperations** возвращает закладки вставленных строк в буфере набора строк, привязанном к этому столбцу.
