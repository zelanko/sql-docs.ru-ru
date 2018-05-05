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
ms.topic: conceptual
helpviewer_keywords:
- ODBC desktop database drivers [ODBC], data types
- data types [ODBC], desktop database drivers
- desktop database drivers [ODBC], data types
ms.assetid: 81c4eab7-1f6b-47a0-b940-89d6c6a14dae
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e42d037592d444b21d4eb8a24879667dd12f5409
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
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
