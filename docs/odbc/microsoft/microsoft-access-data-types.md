---
title: Типы данных доступа Майкрософт Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2019
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 024fb65b6fdc81ae0a8e007d1cee150c6a35b91c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307733"
---
# <a name="microsoft-access-data-types"></a>Типы данных Microsoft Access
В следующей таблице показаны типы данных Microsoft Access, типы данных, используемые для создания таблиц, и типы данных ODBC S'L.  
  
|Тип данных Microsoft Access|Тип данных (CREATETABLE)|Тип данных ODBC S'L|  
|--------------------------------|-------------------------------|------------------------|  
|БИГБИНАРНЫЙ|ЛОНГБИНАРНЫЙ|SQL_LONGVARBINARY|  
|BINARY|BINARY|SQL_BINARY|  
|BIT|BIT|SQL_BIT|  
|Счетчик|Счетчик|SQL_INTEGER|  
|CURRENCY|CURRENCY|SQL_NUMERIC|  
|ДАТА/ВРЕМЯ|DATETIME|SQL_TIMESTAMP|  
|GUID|GUID|SQL_GUID|  
|ДЛИННЫЕ ДВОИЧНЫЕ|ЛОНГБИНАРНЫЙ|SQL_LONGVARBINARY|  
|ДЛИННЫЙ ТЕКСТ|ЛОНГТЕКСТ|SQL_LONGVARCHAR SQL_WLONGVARCHAR|  
|Памятка|ЛОНГТЕКСТ|SQL_LONGVARCHAR SQL_WLONGVARCHAR|  
|NUMBER (FieldSize- SINGLE)|Одного|SQL_REAL|  
|NUMBER (FieldSize- DOUBLE)|DOUBLE|SQL_DOUBLE|  
|NUMBER (FieldSize BYTE)|НЕПОДПИСАННЫЙ БАЙТ|SQL_TINYINT|  
|NUMBER (FieldSize- INTEger)|SHORT|SQL_SMALLINT|  
|NUMBER (FieldSize - LONG INTEger)|LONG|SQL_INTEGER|  
|NUMERIC|NUMERIC|SQL_NUMERIC|  
|OLE|ЛОНГБИНАРНЫЙ|SQL_LONGVARBINARY|  
|TEXT|VARCHAR|SQL_VARCHAR SQL_WVARCHAR|  
|VARBINARY|VARBINARY|SQL_VARBINARY|  
  
 Доступ только 4.0 приложений. Максимальная длина 4000 байтов. Поведение похожее на LONGBINARY.  
  
 AnSI только приложения.  
  
 Только приложения Unicode и Access 4.0.  
  
> [!NOTE]  
>  **S'LGetTypeInfo** возвращает типы данных ODBC. Он не вернет все типы данных Microsoft Access, если более одного типа доступа Майкрософт отображается в тот же тип данных ODBC S'L. Все преобразования в приложении D *Справочника программиста ODBC* поддерживаются для типов данных S'L, перечисленных в предыдущей таблице.  
  
 В следующей таблице отображается ограничения на типы данных Microsoft Access.  
  
|Тип данных|Описание|  
|---------------|-----------------|  
|БИНАР, ВАРБИНАИНА и ВАРЧАР|Создание столбца BINARY, VARBINARY или VARCHAR нулевой или неустановленной длины фактически возвращает столбец 510 байт.|  
|BYTE|Несмотря на то, что поле Microsoft Access NUMBER с полем, равным BYTE, не подписано, отрицательное число может быть вставлено в поле при использовании драйвера Microsoft Access.|  
|ЧАРР, ЛОНГВАРАР и ВАРЧАР|Строка символа буквально может содержать любой символ ANSI (1-255 десятичных знаков). Используйте две последовательные одиночные кавычки ('') для представления одной отметки цитаты (').<br /><br /> Процедуры следует использовать для передачи данных символов при использовании какого-либо специального символа в столбце типа данных символов.|  
|DATE|Значения дат должны быть либо разграничены в соответствии с каноническим форматом даты ODBC, либо разграничены делимитедом времени даты («я»). В противном случае Microsoft Access будет рассматривать значение как арифметическое выражение и не будет вызывать предупреждение или ошибку.<br /><br /> Например, дата "5 марта 1996 года" должна быть представлена как "d 'd 'd 'd 'd 'd 'd 'd 'd 'd 'd 'd 'd 'd 'd 'd 'd 'd 'd 'd 'd 'd 'd '1996-03-05') или #03/05/1996"; в противном случае, если только 03/05/1993 представлен, Microsoft Access будет оценивать это как 3 разделены на 5 разделены на 1996 год. Это значение округляет до integer 0, и с карты нулевого дня до 1899-12-31, это дата используется.<br /><br /> Символ трубы (&#124;) не может быть использован в значении даты, даже если он заключен в задние кавычки.|  
|GUID|Тип данных ограничен Microsoft Access 4.0.|  
|NUMERIC|Тип данных ограничен Microsoft Access 4.0.|  
  
 Дополнительные ограничения на типы данных можно найти в [ограничениях типа данных.](../../odbc/microsoft/data-type-limitations.md)
