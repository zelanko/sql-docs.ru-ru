---
title: "Ограничения типа данных | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC desktop database drivers [ODBC], data types
- data types [ODBC], desktop database drivers
- desktop database drivers [ODBC], data types
ms.assetid: 81c4eab7-1f6b-47a0-b940-89d6c6a14dae
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 558789a4f435e9fc54176b1423d71369f6b4cc22
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="data-type-limitations"></a>Ограничения типа данных
Драйверы Microsoft ODBC системной базы данных наложить следующие ограничения на типы данных.  
  
|Тип данных|Description|  
|---------------|-----------------|  
|Все типы данных|Ошибки преобразования типа может привести к столбцу, равным NULL.|  
|BINARY|Создание ДВОИЧНОГО столбца нулевой длины фактически возвращает ДВОИЧНЫМ столбцом 255 байт.|  
|DATE|Тип данных DATE невозможно привести к другому типу данных (или сам) с помощью функции CONVERT.|  
|DECIMAL (точное числовое)|Не поддерживается.|  
|Типы данных с плавающей запятой|Число десятичных разрядов, в число с плавающей запятой может быть ограничена числовой формат, в разделе региональных стандартов в панели управления Windows.|  
|NUMERIC|Поддерживает максимальную точность и масштаб 28.|  
|timestamp|Тип данных TIMESTAMP невозможно привести к самой функцией CONVERT.|  
|TINYINT|TINYINT значения всегда равны число без знака.|  
|Строки с нулевой длиной|При использовании dBASE, Microsoft Excel, Paradox или Textdriver вставки строки нулевой длины в столбец фактически вставляет значение NULL вместо него.|
