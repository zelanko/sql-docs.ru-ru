---
title: Ограничения типа данных | Документы Microsoft
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
- ODBC desktop database drivers [ODBC], data types
- data types [ODBC], desktop database drivers
- desktop database drivers [ODBC], data types
ms.assetid: 81c4eab7-1f6b-47a0-b940-89d6c6a14dae
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6f7be82a89d81f887baf0ae6ef0fe7cd00e72c27
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="data-type-limitations"></a>Ограничения типа данных
Драйверы Microsoft ODBC системной базы данных наложить следующие ограничения на типы данных.  
  
|Тип данных|Описание|  
|---------------|-----------------|  
|Все типы данных|Ошибки преобразования типа может привести к столбцу, равным NULL.|  
|BINARY|Создание ДВОИЧНОГО столбца нулевой длины фактически возвращает ДВОИЧНЫМ столбцом 255 байт.|  
|DATE|Тип данных DATE невозможно привести к другому типу данных (или сам) с помощью функции CONVERT.|  
|DECIMAL (точное числовое)|Не поддерживается.|  
|Типы данных с плавающей запятой|Число десятичных разрядов, в число с плавающей запятой может быть ограничена числовой формат, в разделе региональных стандартов в панели управления Windows.|  
|NUMERIC|Поддерживает максимальную точность и масштаб 28.|  
|TIMESTAMP|Тип данных TIMESTAMP невозможно привести к самой функцией CONVERT.|  
|TINYINT|TINYINT значения всегда равны число без знака.|  
|Строки с нулевой длиной|При использовании dBASE, Microsoft Excel, Paradox или Textdriver вставки строки нулевой длины в столбец фактически вставляет значение NULL вместо него.|
