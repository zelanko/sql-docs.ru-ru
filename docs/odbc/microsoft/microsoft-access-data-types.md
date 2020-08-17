---
description: Типы данных Microsoft Access
title: Типы данных Microsoft Access | Документация Майкрософт
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
ms.openlocfilehash: 24428c436e9e60c8ca5e42288b217f2c576cbd0d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88340770"
---
# <a name="microsoft-access-data-types"></a>Типы данных Microsoft Access
В следующей таблице показаны типы данных Microsoft Access, типы данных, используемые для создания таблиц, и типы данных ODBC SQL.  
  
|Тип данных Microsoft Access|Тип данных (CREATETABLE)|Тип данных ODBC SQL|  
|--------------------------------|-------------------------------|------------------------|  
|БИГБИНАРИ [1]|лонгбинари|SQL_LONGVARBINARY|  
|BINARY|BINARY|SQL_BINARY|  
|BIT|BIT|SQL_BIT|  
|ПОДПИСАН|ПОДПИСАН|SQL_INTEGER|  
|CURRENCY|ДЕНЕЖНАЯ ЕДИНИЦА|SQL_NUMERIC|  
|ДАТА И ВРЕМЯ|DATETIME|SQL_TIMESTAMP|  
|Код GUID|Код GUID|SQL_GUID|  
|ДЛИННЫЙ ДВОИЧНЫЙ ФАЙЛ|лонгбинари|SQL_LONGVARBINARY|  
|ДЛИННЫЙ ТЕКСТ|LONGTEXT|SQL_LONGVARCHAR [2] SQL_WLONGVARCHAR [3]|  
|ПОЛУЧЕНА|LONGTEXT|SQL_LONGVARCHAR [2] SQL_WLONGVARCHAR [3]|  
|ЧИСЛО (FieldSize = SINGLE)|ОДИН|SQL_REAL|  
|ЧИСЛО (FieldSize = DOUBLE)|DOUBLE|SQL_DOUBLE|  
|ЧИСЛО (FieldSize = BYTE)|БАЙТ БЕЗ ЗНАКА|SQL_TINYINT|  
|ЧИСЛО (FieldSize = INTEGER)|SHORT|SQL_SMALLINT|  
|ЧИСЛО (FieldSize = ДЛИННое ЦЕЛОе)|LONG|SQL_INTEGER|  
|NUMERIC|NUMERIC|SQL_NUMERIC|  
|OLE|лонгбинари|SQL_LONGVARBINARY|  
|TEXT|VARCHAR|SQL_VARCHAR [1] SQL_WVARCHAR [2]|  
|VARBINARY|VARBINARY|SQL_VARBINARY|  
  
 [1] доступ только к приложениям 4,0. Максимальная длина 4000 байт. Поведение аналогично ЛОНГБИНАРИ.  
  
 [2] только приложения ANSI.  
  
 [3] Unicode и доступ только к приложениям 4,0.  
  
> [!NOTE]  
>  **SQLGetTypeInfo** возвращает типы данных ODBC. Все типы данных Microsoft Access не возвращаются, если к одному и тому же типу данных ODBC SQL сопоставлено несколько типов Microsoft Access. Все преобразования в приложении D *Справочника программиста ODBC* поддерживаются для типов данных SQL, перечисленных в предыдущей таблице.  
  
 В следующей таблице приведены ограничения для типов данных Microsoft Access.  
  
|Тип данных|Описание|  
|---------------|-----------------|  
|BINARY, VARBINARY и VARCHAR|Создание столбца BINARY, VARBINARY или VARCHAR, который имеет нулевую или неуказанную длину, фактически возвращает 510-байтовый столбец.|  
|BYTE|Несмотря на то, что поле номера Microsoft Access с размером FieldSize, равным BYTE, не подписано, при использовании драйвера Microsoft Access в поле можно вставить отрицательное число.|  
|CHAR, LONGVARCHAR и VARCHAR|Символьная строка символов может содержать любой символ ANSI (1-255 десятичное число). Для представления одной одинарной кавычки (') используйте две последовательные одинарные кавычки (' ').<br /><br /> Процедуры должны использоваться для передачи символьных данных при использовании любого специального символа в столбце символьного типа данных.|  
|DATE|Значения даты должны быть либо ограничены в соответствии с каноническим форматом даты ODBC, либо разделяться разделителем даты и времени ("#"). В противном случае Microsoft Access будет рассматривать значение как арифметическое выражение и не будет вызывать предупреждение или ошибку.<br /><br /> Например, Дата "5 марта 1996" должна быть представлена в виде {d ' 1996-03-05 '} или #03/05/1996 #; в противном случае, если будет отправлено только 03/05/1993, Microsoft Access вычислит это значение 3 на 5 деленное на 1996. Это значение округляется до целого числа 0, а нулевой день сопоставляется с 1899-12-31, то есть используется дата.<br /><br /> Символ вертикальной черты (&#124;) нельзя использовать в значении даты, даже если он заключен в обратные кавычки.|  
|Код GUID|Тип данных ограничен Microsoft Access 4,0.|  
|NUMERIC|Тип данных ограничен Microsoft Access 4,0.|  
  
 Дополнительные ограничения для типов данных можно найти в [ограничениях типа данных](../../odbc/microsoft/data-type-limitations.md).
