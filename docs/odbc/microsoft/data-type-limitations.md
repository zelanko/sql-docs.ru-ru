---
title: Ограничения типов данных | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC desktop database drivers [ODBC], data types
- data types [ODBC], desktop database drivers
- desktop database drivers [ODBC], data types
ms.assetid: 81c4eab7-1f6b-47a0-b940-89d6c6a14dae
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 64d16a9181c475427677371d1e6e180570225b7a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68096465"
---
# <a name="data-type-limitations"></a>Ограничения типов данных
Драйверы баз данных Microsoft ODBC для настольных систем накладывают следующие ограничения на типы данных:  
  
|Тип данных|Description|  
|---------------|-----------------|  
|Все типы данных|Ошибки преобразования типов могут привести к тому, что в затронутом столбце будет установлено значение NULL.|  
|BINARY|Создание ДВОИЧного столбца нулевой длины фактически возвращает 255-байтный ДВОИЧный столбец.|  
|DATE|Тип данных DATE не может быть преобразован в другой тип данных (или сам) функцией CONVERT.|  
|ДЕСЯТИЧное число (точное число)|Не поддерживается.|  
|Типы данных с плавающей запятой|Число десятичных разрядов в числе чисел с плавающей запятой может быть ограничено числом, заданным в разделе Международная на панели управления Windows.|  
|NUMERIC|Поддерживает максимальную точность и масштаб 28.|  
|TIMESTAMP|Тип данных TIMESTAMP не может быть преобразован функцией CONVERT.|  
|TINYINT|Значения TINYINT всегда беззнаковые.|  
|Строки нулевой длины|При использовании dBASE, Microsoft Excel, Paradox или Текстдривер Вставка строки нулевой длины в столбец фактически вставляет значение NULL.|
