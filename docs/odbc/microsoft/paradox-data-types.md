---
title: Типы данных парадокса (ru) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC desktop database drivers [ODBC], Paradox driver
- desktop database drivers [ODBC], Paradox driver
- Paradox data types [ODBC]
- Jet-based ODBC drivers [ODBC], Paradox driver
- data types [ODBC], Paradox driver
- Paradox driver [ODBC], data types
ms.assetid: 0c9e5d21-9321-49f8-a055-69459e1c9c85
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a85cf643a6d22b9b2fce15984539d74dc43c62ab
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81290934"
---
# <a name="paradox-data-types"></a>Типы данных Paradox
Драйвер ODBC Paradox отображает типы данных Paradox к типам данных ODBC S'L. В следующей таблице перечислены все типы данных Paradox и показаны типы данных ODBC S'L, к которые они отображаются.  
  
|Тип данных парадокса|Тип данных ODBC|  
|-----------------------|--------------------|  
|Буквы|SQL_VARCHAR|  
|АУТОИНКРЕМЕНТ|SQL_INTEGER|  
|БХД)|SQL_DOUBLE|  
|БАЙТС|SQL_BINARY|  
|DATE|SQL_DATE|  
|ИЗОБРАЖЕНИЕ|SQL_LONGVARBINARY|  
|ЛОГИЧНО|SQL_BIT|  
|ДОЛГОЕ ВРЕМЯ|SQL_INTEGER|  
|ПАМЯТКА|SQL_LONGVARCHAR|  
|ДЕНЬГИ|SQL_DOUBLE|  
|NUMBER|SQL_DOUBLE|  
|SHORT|SQL_SMALLINT|  
|ВРЕМЯ|SQL_TIMESTAMP|  
|TIMESTAMP|SQL_TIMESTAMP|  
  
 Действительно только для версий Paradox 5. *x*.  
  
 Действительно только для версий Парадокса 4. *x* и 5. *x*.  
  
> [!NOTE]  
>  **SLGetTypeInfo** возвращает типы данных ODBC S'L. Все преобразования в приложении D *Справочника программиста ODBC* поддерживаются для типов данных ODBC S'L, перечисленных ранее в этой теме.  
  
 В следующей таблице показаны ограничения по типам данных Paradox.  
  
|Тип данных|Описание|  
|---------------|-----------------|  
|Буквы|Создание столбца ALPHANUMERIC нулевой или неопределенной длины фактически возвращает столбец 255 байт.|  
|BYTES|Если вы вставите NULL в двоичную колонку с драйвером Paradox5, он будет изменен на 0.|  
|LONG|Максимальное отрицательное значение, поддерживаемое драйвером Paradox для типа Длинных данных в Paradox 5. *x* не является -2'31 (-2147483648), как это должно быть, так как Длинные карты типа данных ODBC SQL_INTEGER. Максимальное отрицательное значение, поддерживаемое для Long, на самом деле составляет -2'31 и 1 (-2147483647).|  
|timestamp|Когда значение вставляется в столбец TIMESTAMP драйвером Paradox, затем последующее извлечение из столбца, извлеченное значение может отличаться от вставленного значения на целых 1 секунду из-за округления.|  
  
 Дополнительные ограничения на типы данных можно найти в [ограничениях типа данных.](../../odbc/microsoft/data-type-limitations.md)
