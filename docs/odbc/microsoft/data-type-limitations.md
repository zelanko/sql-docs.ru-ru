---
title: Ограничения типа данных | Документация Майкрософт
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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68096465"
---
# <a name="data-type-limitations"></a>Ограничения типов данных
Драйверы для баз данных Microsoft ODBC Desktop накладывает следующие ограничения на типы данных:  
  
|Тип данных|Описание|  
|---------------|-----------------|  
|Все типы данных|Ошибки преобразования типа может привести к столбцу, равным NULL.|  
|BINARY|Создание двоичный столбец нулевой длины на самом деле возвращает 255-байтовые двоичный столбец.|  
|DATE|Тип данных DATE невозможно привести к другому типу данных (или сам) с помощью функции CONVERT.|  
|DECIMAL (точное числовое)|Не поддерживается.|  
|Типы данных с плавающей запятой|Количество десятичных разрядов в число с плавающей запятой могут быть ограничены числовой формат, задайте в разделе региональных стандартов в панели управления Windows.|  
|NUMERIC|Поддерживает максимальную точность и масштаб 28.|  
|timestamp|Тип данных TIMESTAMP невозможно привести к самой функцией CONVERT.|  
|TINYINT|TINYINT значения всегда равны без знака.|  
|Строки с нулевой длиной|При использовании dBASE, Microsoft Excel, Paradox или Textdriver вставки строки нулевой длины в столбец фактически вставляет значение NULL вместо него.|
