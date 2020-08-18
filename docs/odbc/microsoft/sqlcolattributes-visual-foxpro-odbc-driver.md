---
description: SQLColAttributes (драйвер ODBC для Visual FoxPro)
title: SQLColAttributes (драйвер ODBC для Visual FoxPro) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLColAttribute function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: d403dfa0-c26d-47d4-91d9-2f29aa387399
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 062a5af2e8aab4d71cf201284bd065242c588f6a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88412200"
---
# <a name="sqlcolattributes-visual-foxpro-odbc-driver"></a>SQLColAttributes (драйвер ODBC для Visual FoxPro)
> [!NOTE]  
>  В этом разделе содержатся сведения, относящиеся к драйверу ODBC для Visual FoxPro. Общие сведения об этой функции см. в соответствующем разделе [справочника по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Поддержка: полная  
  
 Соответствие API ODBC: уровень ядра  
  
 Возвращает сведения о дескрипторе для столбца в результирующем наборе. Сведения о дескрипторе возвращаются в виде символьной строки, 32-разрядного значения, зависящего от дескриптора, или целочисленного значения.  
  
> [!NOTE]  
>  **SQLColAttributes** нельзя использовать для получения сведений о столбце закладки (столбец 0).  
  
 Драйвер ODBC для Visual FoxPro поддерживает все значения *фдесктипе* . В следующей таблице содержатся комментарии к реализации выбранных значений драйвера.  
  
|*фдесктипе*|Комментарий|  
|-----------------|-------------|  
|SQL_COLUMN_AUTO_INCREMENT|Возвращает значение FALSE: в Visual FoxPro отсутствуют поля счетчика.|  
|SQL_COLUMN_CASE_SENSITIVE|Всегда возвращает значение TRUE, если столбец имеет тип character.|  
|SQL_COLUMN_LABEL|Возвращает имя столбца, которое также возвращается SQL_COLUMN_NAME.|  
|SQL_COLUMN_MONEY|Возвращает значение TRUE, если столбец имеет тип Currency (представленный "Y" в языке Visual FoxPro).|  
|SQL_COLUMN_OWNER_NAME|Всегда возвращает пустую строку.|  
|SQL_COLUMN_QUALIFIER_NAME|Всегда возвращает пустую строку.|  
|SQL_COLUMN_SEARCHABLE|Возвращает SQL_UNSEARCHABLE для столбцов типа General; Эти столбцы нельзя использовать в предложении WHERE.<br /><br /> Возвращает SQL_SEARCHABLE для столбцов типа character или MEMO с параметром НОКПТРАНС Not Set; Эти столбцы можно использовать в предложении WHERE с любым оператором сравнения.<br /><br /> Возвращает SQL_ALL_EXCEPT_LIKE для всех других типов столбцов; Эти столбцы можно использовать в предложении WHERE со всеми операторами сравнения, за исключением LIKE.|  
|SQL_COLUMN_TABLE_NAME|Всегда возвращает пустую строку.|  
  
 Дополнительные сведения см. в разделе [SQLColAttributes](../../odbc/reference/syntax/sqlcolattributes-function.md) в *справочнике программиста по ODBC*.
