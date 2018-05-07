---
title: Вставка строк с SQLBulkOperations | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQLBulkOperations function [ODBC], inserting rows
- data updates [ODBC], SQLBulkOperations
- updating data [ODBC], SQLBulkOperations
ms.assetid: ed585ea7-4d56-4df9-8dc3-53ca82382450
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fbeb779917c2029576bc78ec4a1d144716b7242f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="inserting-rows-with-sqlbulkoperations"></a>Вставка строк с SQLBulkOperations
Вставка данных с **SQLBulkOperations** похож на обновление данных с **SQLBulkOperations** , так как он использует данные из привязанного приложения буферов.  
  
 Каждый столбец в новой строке имеет значение, все присоединенные столбцы со значением длины/индикатора SQL_COLUMN_IGNORE, а все непривязанные столбцы должны либо принимать значения NULL или иметь значение по умолчанию.  
  
 Для вставки строк с **SQLBulkOperations**, приложение делает следующее:  
  
1.  Устанавливает атрибут SQL_ATTR_ROW_ARRAY_SIZE инструкции число вставляемых строк и помещает новые значения данных в буферах привязанного приложения. Сведения о том, как для отправления объемных данных с **SQLBulkOperations**, в разделе [большие объемы данных и SQLSetPos и SQLBulkOperations](../../../odbc/reference/develop-app/long-data-and-sqlsetpos-and-sqlbulkoperations.md).  
  
2.  Задает значение в буфер длины/индикатора каждого столбца при необходимости. Это байтовая длина данных или SQL_NTS для столбцов, привязанных к буферам строк байтовая длина данных для столбцов, привязанных к двоичных буферов и SQL_NULL_DATA для всех столбцов будет присвоено значение NULL. Приложение задает значение в буфер длины/индикатора те столбцы, которые должны быть заданы по умолчанию (если он существует) или значение NULL (если нет) SQL_COLUMN_IGNORE.  
  
3.  Вызовы **SQLBulkOperations** с *операции* аргументу присвоено SQL_ADD.  
  
 После **SQLBulkOperations** возвращает текущую строку без изменений. Если связанное закладки столбца (0) **SQLBulkOperations** возвращает закладки вставляемых строк в буфере строк привязан к этому столбцу.
