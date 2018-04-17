---
title: Типы данных Paradox | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ODBC desktop database drivers [ODBC], Paradox driver
- desktop database drivers [ODBC], Paradox driver
- Paradox data types [ODBC]
- Jet-based ODBC drivers [ODBC], Paradox driver
- data types [ODBC], Paradox driver
- Paradox driver [ODBC], data types
ms.assetid: 0c9e5d21-9321-49f8-a055-69459e1c9c85
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: cee6fd6f7b13b10a59047964ba0d344ba13b8381
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="paradox-data-types"></a>Типы данных Paradox
Драйвера ODBC Paradox Paradox типы данных сопоставляются с типами данных ODBC SQL. В следующей таблице перечислены все типы данных Paradox и показаны типы данных, которые они сопоставляются с ODBC SQL.  
  
|Тип данных Paradox|Тип данных ODBC|  
|-----------------------|--------------------|  
|БУКВЕННО-ЦИФРОВОЙ|SQL_VARCHAR|  
|АВТОУВЕЛИЧЕНИЕ [1]|SQL_INTEGER|  
|BCD [1]|SQL_DOUBLE|  
|БАЙТЫ [1]|SQL_BINARY|  
|DATE|SQL_DATE|  
|ИЗОБРАЖЕНИЯ [2]|SQL_LONGVARBINARY|  
|ЛОГИЧЕСКИЙ [1]|SQL_BIT|  
|LONG [1]|SQL_INTEGER|  
|MEMO [2]|SQL_LONGVARCHAR|  
|MONEY [1]|SQL_DOUBLE|  
|NUMBER|SQL_DOUBLE|  
|КОРОТКИЙ|SQL_SMALLINT|  
|ВРЕМЯ [1]|SQL_TIMESTAMP|  
|ОТМЕТКА ВРЕМЕНИ [1]|SQL_TIMESTAMP|  
  
 [1] допустимо только для Paradox версии 5. *x*.  
  
 [2] допустимо только для Paradox версии 4. *x* и 5. *x*.  
  
> [!NOTE]  
>  **SQLGetTypeInfo** возвращает типы данных ODBC SQL. Все преобразования в приложении D *справочнике программиста ODBC* поддерживается для типов данных ODBC SQL, перечисленных ранее в этом разделе.  
  
 Ниже приведены ограничения на типы данных Paradox.  
  
|Тип данных|Описание|  
|---------------|-----------------|  
|БУКВЕННО-ЦИФРОВОЙ|Создание буквенно-ЦИФРОВЫХ столбца равно нулю или неизвестной длины фактически возвращает столбец 255 байт.|  
|BYTES|При вставке значения NULL в двоичного столбца с помощью драйвера Paradox5 он меняется на 0.|  
|LONG|Максимальное значение отрицательное, поддерживаются драйвером Paradox для типа данных Long в Paradox 5. *x* не -2 ^ 31 (-2147483648), как она должна быть, так как Long сопоставляется данных ODBC, введите SQL_INTEGER. Максимальное значение отрицательное, поддерживаемое для длительных является фактически -2 ^ 31 + 1 (-2147483647).|  
|TIMESTAMP|Если значение вставляемых в столбец отметки времени драйвером Paradox, то впоследствии, полученных из столбца, возвращенного значения могут отличаться от вставленное значение по мере 1 секунды из-за округления.|  
  
 Дополнительные ограничения на типы данных можно найти в [ограничения типа данных](../../odbc/microsoft/data-type-limitations.md).
