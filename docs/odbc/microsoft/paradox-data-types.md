---
description: Типы данных Paradox
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 44494e9945a84f978449b6bab02bd967e40d9a20
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88340460"
---
# <a name="paradox-data-types"></a>Типы данных Paradox
Драйвер ODBC Paradox сопоставляет типы данных Paradox с типами данных ODBC SQL. В следующей таблице перечислены все типы данных Paradox и показаны типы данных ODBC SQL, с которыми они сопоставлены.  
  
|Тип данных Paradox|Тип данных ODBC|  
|-----------------------|--------------------|  
|ЗНАКОВ|SQL_VARCHAR|  
|АВТОУВЕЛИЧЕНИЕ [1]|SQL_INTEGER|  
|BCD [1]|SQL_DOUBLE|  
|БАЙТ [1]|SQL_BINARY|  
|DATE|SQL_DATE|  
|ИЗОБРАЖЕНИЕ [2]|SQL_LONGVARBINARY|  
|ЛОГИЧЕСКОЕ [1]|SQL_BIT|  
|ДЛИННЫЙ [1]|SQL_INTEGER|  
|МЕМО [2]|SQL_LONGVARCHAR|  
|ДЕНЬГИ [1]|SQL_DOUBLE|  
|NUMBER|SQL_DOUBLE|  
|SHORT|SQL_SMALLINT|  
|ВРЕМЯ [1]|SQL_TIMESTAMP|  
|МЕТКА ВРЕМЕНИ [1]|SQL_TIMESTAMP|  
  
 [1] допустимо только для Paradox версии 5. *x*.  
  
 [2] допускается только для Paradox версии 4. *x* и 5. *x*.  
  
> [!NOTE]  
>  **SQLGetTypeInfo** возвращает типы данных ODBC SQL. Все преобразования в приложении D *Справочника программиста ODBC* поддерживаются для типов данных ODBC SQL, перечисленных ранее в этом разделе.  
  
 В следующей таблице приведены ограничения для типов данных Paradox.  
  
|Тип данных|Описание|  
|---------------|-----------------|  
|ЗНАКОВ|Создание БУКВЕНно-цифрового столбца нулевой или неуказанной длины фактически возвращает 255-байтовый столбец.|  
|BYTES|Если вставить значение NULL в двоичный столбец с драйвером Paradox5, он изменится на 0.|  
|LONG|Максимальное отрицательное значение, поддерживаемое драйвером Paradox для типа данных Long 5. значение *x* не равно-2 ^ 31 (-2147483648), так как оно должно быть сопоставлено с типом данных ODBC SQL_INTEGER. Максимальное отрицательное значение, поддерживаемое для Long, фактически равно-2 ^ 31 + 1 (-2147483647).|  
|timestamp|Когда драйвер Paradox вставляет значение в столбец TIMESTAMP, затем извлекается из столбца, полученное значение может отличаться от вставленного значения на 1 секунду из-за округления.|  
  
 Дополнительные ограничения для типов данных можно найти в [ограничениях типа данных](../../odbc/microsoft/data-type-limitations.md).
