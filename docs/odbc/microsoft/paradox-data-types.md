---
title: Типы данных Paradox | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8e2f3b1e63578af7c0b42f00113fbb9e87cb8003
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47628512"
---
# <a name="paradox-data-types"></a>Типы данных Paradox
Драйвер ODBC для Paradox сопоставляет типы данных Paradox типов данных ODBC SQL. В следующей таблице перечислены все типы данных Paradox и показано ODBC SQL, типы данных, которые они сопоставляются.  
  
|Тип данных Paradox|Тип данных ODBC|  
|-----------------------|--------------------|  
|БУКВЕННО-ЦИФРОВОЙ|SQL_VARCHAR|  
|АВТОУВЕЛИЧЕНИЕ [1]|SQL_INTEGER|  
|BCD [1]|SQL_DOUBLE|  
|БАЙТЫ [1]|SQL_BINARY|  
|DATE|SQL_DATE|  
|ИЗОБРАЖЕНИЯ [2]|SQL_LONGVARBINARY|  
|ЛОГИЧЕСКИЙ [1]|SQL_BIT|  
|ДОЛГО [1]|SQL_INTEGER|  
|MEMO [2]|SQL_LONGVARCHAR|  
|MONEY [1]|SQL_DOUBLE|  
|NUMBER|SQL_DOUBLE|  
|КОРОТКИЙ|SQL_SMALLINT|  
|ВРЕМЯ [1]|SQL_TIMESTAMP|  
|МЕТКА ВРЕМЕНИ [1]|SQL_TIMESTAMP|  
  
 [1] допустимо только для Paradox версии 5. *x*.  
  
 [2] допустимо только для Paradox версии 4. *x* и 5. *x*.  
  
> [!NOTE]  
>  **SQLGetTypeInfo** возвращает типы данных ODBC SQL. Все преобразования в приложении D *Справочник по программированию ODBC* поддерживаются для типов данных ODBC SQL, перечисленных ранее в этом разделе.  
  
 Ниже приведены ограничения на типы данных Paradox.  
  
|Тип данных|Описание|  
|---------------|-----------------|  
|БУКВЕННО-ЦИФРОВОЙ|Создание столбца буквенно-ЦИФРОВЫЕ нулевой или неизвестной длины на самом деле возвращает 255-байтовый столбец.|  
|BYTES|Если вставить значение NULL в двоичный столбец с помощью драйвера Paradox5, он изменяется на 0.|  
|LONG|Максимальное значение отрицательное, поддерживаемый драйвер для Paradox для типа данных Long в Paradox 5. *x* не -2 ^ 31 (-2147483648), как было бы с момента Long сопоставляется данных ODBC, введите SQL_INTEGER. Максимальное значение отрицательное, поддерживаемое для длительных — фактически -2 ^ 31 + 1 (-2147483647).|  
|timestamp|Когда значения вставляются в столбец отметки времени драйвер для Paradox, то затем извлекается из столбца, извлеченное значение может отличаться от вставленное значение по мере 1 секунды из-за округления.|  
  
 Дополнительные ограничения на типы данных можно найти в [ограничения типов данных](../../odbc/microsoft/data-type-limitations.md).
