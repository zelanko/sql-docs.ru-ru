---
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e34929315d3a3548799bc605dbb8f3c4a2f665d0
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62928166"
---
# <a name="sqlcolattributes-visual-foxpro-odbc-driver"></a>SQLColAttributes (драйвер ODBC для Visual FoxPro)
> [!NOTE]  
>  Этот раздел содержит сведения Visual FoxPro ODBC-драйвером. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Поддержка: Полное  
  
 Соответствие API ODBC: Уровня ядра  
  
 Возвращает данные дескриптора для столбца в результирующем наборе. Сведения о дескрипторе возвращается как символьная строка, значение дескриптора зависит от 32-разрядной или целочисленное значение.  
  
> [!NOTE]  
>  **SQLColAttributes** не может использоваться для возврата сведений о закладки столбца (0).  
  
 Драйвер ODBC для Visual FoxPro поддерживает все *fDescType* значения. В следующей таблице приведены комментарии к реализации драйвера выбранных значений.  
  
|*fDescType*|Комментарий|  
|-----------------|-------------|  
|SQL_COLUMN_AUTO_INCREMENT|Возвращает значение FALSE: Visual FoxPro не имеет счетчик полей.|  
|SQL_COLUMN_CASE_SENSITIVE|Всегда возвращает значение TRUE, если столбец имеет тип символа.|  
|SQL_COLUMN_LABEL|Возвращает имя столбца, который возвращается методом SQL_COLUMN_NAME также.|  
|SQL_COLUMN_MONEY|Возвращает значение TRUE, если столбец имеет тип валюте, («Y» на языке Visual FoxPro).|  
|SQL_COLUMN_OWNER_NAME|Всегда возвращает пустую строку.|  
|SQL_COLUMN_QUALIFIER_NAME|Всегда возвращает пустую строку.|  
|SQL_COLUMN_SEARCHABLE|Возвращает SQL_UNSEARCHABLE для столбцов с типом General; Эти столбцы не может использоваться в предложении WHERE.<br /><br /> Возвращает SQL_SEARCHABLE для столбцов с типом знак или Memo с NOCPTRANS не задан; Эти столбцы могут использоваться в предложении WHERE с любым оператором сравнения.<br /><br /> Возвращает SQL_ALL_EXCEPT_LIKE для всех других типов столбцов; Эти столбцы могут использоваться в предложении WHERE, со всеми операторами сравнения, за исключением LIKE.|  
|SQL_COLUMN_TABLE_NAME|Всегда возвращает пустую строку.|  
  
 Дополнительные сведения см. в разделе [SQLColAttributes](../../odbc/reference/syntax/sqlcolattributes-function.md) в *Справочник по программированию ODBC*.
