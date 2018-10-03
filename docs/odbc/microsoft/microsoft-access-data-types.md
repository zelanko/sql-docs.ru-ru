---
title: Типы данных Microsoft Access | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC desktop database drivers [ODBC], Access driver
- Jet-based ODBC drivers [ODBC], Access driver
- desktop database drivers [ODBC], Access driver
- Access driver [ODBC], data types
- access data types [ODBC]
- data types [ODBC], Access driver
ms.assetid: b537348a-bea0-4bd6-84a4-52a75292957f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 11f45698a5ad8b7fd05052cbb2d23520790c425a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47692982"
---
# <a name="microsoft-access-data-types"></a>Типы данных Microsoft Access
Ниже приведены типы данных Microsoft Access, типы данных, используемые для создания таблиц и типов данных ODBC SQL.  
  
|Тип данных Microsoft Access|Тип данных (CREATETABLE)|Тип данных ODBC SQL|  
|--------------------------------|-------------------------------|------------------------|  
|BIGBINARY [1]|LONGBINARY|SQL_LONGVARBINARY|  
|BINARY|BINARY|SQL_BINARY|  
|BIT|BIT|SQL_BIT|  
|СЧЕТЧИК|СЧЕТЧИК|SQL_INTEGER|  
|CURRENCY|CURRENCY|SQL_NUMERIC|  
|ДАТЫ И ВРЕМЕНИ|DATETIME|SQL_TIMESTAMP|  
|GUID|GUID|SQL_GUID|  
|ДЛИННОЕ ДВОИЧНОЕ|LONGBINARY|SQL_LONGVARBINARY|  
|ДЛИННЫЙ ТЕКСТ|LONGTEXT|SQL_WLONGVARCHAR SQL_LONGVARCHAR [2] [3]|  
|MEMO|LONGTEXT|SQL_WLONGVARCHAR SQL_LONGVARCHAR [2] [3]|  
|НОМЕР (FieldSize = один)|ЕДИНЫЙ|SQL_REAL|  
|НОМЕР (FieldSize = DOUBLE)|DOUBLE|SQL_DOUBLE|  
|НОМЕР (FieldSize = БАЙТ)|БАЙТ БЕЗ ЗНАКА|SQL_TINYINT|  
|НОМЕР (FieldSize = INTEGER)|КОРОТКИЙ|SQL_SMALLINT|  
|НОМЕР (FieldSize = ДЛИННОЕ целое число)|LONG|SQL_INTEGER|  
|NUMERIC|NUMERIC|SQL_NUMERIC|  
|OLE|LONGBINARY|SQL_LONGVARBINARY|  
|TEXT|VARCHAR|SQL_WVARCHAR SQL_VARCHAR [1] [2]|  
ARBINARY|VARBINARY|SQL_VARBINARY|  
  
 [1] доступ 4.0 приложения. Максимальная длина 4 000 байт. Поведение, аналогичное LONGBINARY.  
  
 [2] только приложения ANSI.  
  
 [3] Юникода и 4.0 доступа только приложения.  
  
> [!NOTE]  
>  **SQLGetTypeInfo** возвращает типы данных ODBC. Он не будет возвращать все типы данных Microsoft Access, если более чем один тип Microsoft Access сопоставляется один и тот же тип данных ODBC SQL. Все преобразования в приложении D *Справочник по программированию ODBC* поддерживаются для типов данных SQL, перечисленные в предыдущей таблице.  
  
 Ниже приведены ограничения на типы данных Microsoft Access.  
  
|Тип данных|Описание|  
|---------------|-----------------|  
|BINARY, VARBINARY и VARCHAR|Создание столбца BINARY, VARBINARY или VARCHAR нулевое или неизвестной длины на самом деле возвращает 510-байтовый столбец.|  
|BYTE|Несмотря на то, что поле номер доступа к Microsoft с основании итогового, равный BYTE без знака, отрицательным числом могут быть вставлены в поле при использовании драйвера Microsoft Access.|  
|CHAR, VARCHAR и LONGVARCHAR|Символ строковый литерал может содержать любой символ ANSI (десятичное число от 1 до 255). Используйте две стоящие рядом одинарные кавычки ("") для представления одинарной кавычки (').<br /><br /> Процедуры должны использоваться для передачи символьных данных при использовании всех специальных символов в символьный столбец тип данных.|  
|DATE|Значения даты должен быть с разделителями в соответствии с канонический формат ODBC или разделителем даты и времени («#»). В противном случае Microsoft Access будет рассматривать значение как арифметического выражения и не вызовут предупреждение или ошибку.<br /><br /> Например, даты, «5 марта 1996 г.» должно быть представлено как {d ' 1996-03-05 "} или #03/05/1996 #; в противном случае — если только отправляется 03/05/1993 г., Microsoft Access оценит это как 3, деления на 5, деленное на 1996 г. Это значение округляет до целого числа 0, а поскольку нулевого дня сопоставляет 1899-12-31, это дата, используемая.<br /><br /> Знак вертикальной черты (&#124;) не может использоваться в значение даты, даже если они заключены обратно в кавычки.|  
|GUID|Тип данных ограничивается Microsoft Access 4.0.|  
|NUMERIC|Тип данных ограничивается Microsoft Access 4.0.|  
  
 Дополнительные ограничения на типы данных можно найти в [ограничения типов данных](../../odbc/microsoft/data-type-limitations.md).
