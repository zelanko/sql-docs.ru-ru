---
title: "Типы данных Microsoft Access | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC desktop database drivers [ODBC], Access driver
- Jet-based ODBC drivers [ODBC], Access driver
- desktop database drivers [ODBC], Access driver
- Access driver [ODBC], data types
- access data types [ODBC]
- data types [ODBC], Access driver
ms.assetid: b537348a-bea0-4bd6-84a4-52a75292957f
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: bee1801eb581272762b2f80d25eeb64d0220a256
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="microsoft-access-data-types"></a>Типы данных Microsoft Access
В следующей таблице показаны типы данных Microsoft Access, типы данных, используемые для создания таблиц и типы данных ODBC SQL.  
  
|Тип данных Microsoft Access|Тип данных (CREATETABLE)|Тип данных ODBC SQL|  
|--------------------------------|-------------------------------|------------------------|  
|BIGBINARY [1]|LONGBINARY|SQL_LONGVARBINARY|  
|BINARY|BINARY|SQL_BINARY|  
|BIT|BIT|SQL_BIT|  
|СЧЕТЧИК|СЧЕТЧИК|SQL_INTEGER|  
|CURRENCY|CURRENCY|SQL_NUMERIC|  
|ДАТЫ И ВРЕМЕНИ|DATETIME|SQL_TIMESTAMP|  
|GUID|GUID|SQL_GUID|  
|ДЛИННАЯ ДВОИЧНАЯ|LONGBINARY|SQL_LONGVARBINARY|  
|ДЛИННЫЙ ТЕКСТ|LONGTEXT|SQL_WLONGVARCHAR SQL_LONGVARCHAR [2] [3]|  
|MEMO|LONGTEXT|SQL_WLONGVARCHAR SQL_LONGVARCHAR [2] [3]|  
|НОМЕР (FieldSize = один)|ОДИН|SQL_REAL|  
|НОМЕР (FieldSize = DOUBLE)|DOUBLE|SQL_DOUBLE|  
|НОМЕР (FieldSize = БАЙТ)|БАЙТ БЕЗ ЗНАКА|SQL_TINYINT|  
|НОМЕР (FieldSize = целое число)|КОРОТКИЙ|SQL_SMALLINT|  
|НОМЕР (FieldSize = ДЛИННОЕ целое число)|LONG|SQL_INTEGER|  
|NUMERIC|NUMERIC|SQL_NUMERIC|  
|OLE|LONGBINARY|SQL_LONGVARBINARY|  
|TEXT|VARCHAR|[1] SQL_VARCHAR, SQL_WVARCHAR [2]|  
ARBINARY|VARBINARY|SQL_VARBINARY|  
  
 [1] доступ 4.0 приложения. Максимальная длина 4 000 байт. Поведение аналогично LONGBINARY.  
  
 [2] ANSI приложения.  
  
 [3] Юникода и 4.0 доступ только для приложений.  
  
> [!NOTE]  
>  **SQLGetTypeInfo** возвращает типы данных ODBC. Он не будет возвращать все типы данных Microsoft Access, если более чем один тип Microsoft Access сопоставляется один и тот же тип данных ODBC SQL. Все преобразования в приложении D *справочнике программиста ODBC* поддерживается для типов данных SQL, перечисленные в предыдущей таблице.  
  
 Ниже приведены ограничения на типы данных Microsoft Access.  
  
|Тип данных|Description|  
|---------------|-----------------|  
|BINARY, VARBINARY и VARCHAR|Создание столбца BINARY, VARBINARY или VARCHAR нулевое или неизвестной длины фактически возвращает 510-байтовый столбец.|  
|BYTE|Несмотря на то, что поле номера доступа Microsoft с основании итогового, равно БАЙТОВ без знака, отрицательное значение могут вставляться в поле при использовании драйвера Microsoft Access.|  
|CHAR, VARCHAR и LONGVARCHAR|Символьного литерала могут содержать любой символ ANSI (1-255 в десятичном формате). Используйте две стоящие рядом одинарные кавычки ("") для представления символ одинарной кавычки (').<br /><br /> Процедуры следует использовать для передачи символьных данных при использовании специальных символов в символьный столбец типа данных.|  
|DATE|Значения дат должен с разделителями в соответствии с форматом даты канонические ODBC или разделитель даты и времени («#»). В противном случае Microsoft Access будет рассматривать значение как арифметического выражения и не будет создавать предупреждения или ошибки.<br /><br /> Например, «5 марта 1996» должны быть представлены как дата {d ' 1996-03-05 "} или #03/05/&#1996; в противном случае если только для отправки 03/05/1993 Microsoft Access значения этой как 3, разделенное на деления 5 на 1996. Это значение выполняет округление до целого числа 0, и поскольку нулевого дня сопоставляет 1899-12-31, это дата, используемая.<br /><br /> Знак вертикальной черты (&#124;) не может использоваться в значении даты, даже если они заключены обратно в кавычки.|  
|GUID|Тип данных ограничивается Microsoft Access 4.0.|  
|NUMERIC|Тип данных ограничивается Microsoft Access 4.0.|  
  
 Дополнительные ограничения на типы данных можно найти в [ограничения типа данных](../../odbc/microsoft/data-type-limitations.md).
