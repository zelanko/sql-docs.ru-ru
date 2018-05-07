---
title: Типы данных полей Visual FoxPro | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- field data types [ODBC]
- Visual FoxPro ODBC driver [ODBC], data types
ms.assetid: 50b733dc-679a-4b10-bc5d-98bb474dead2
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c2bb370e2e27d2c058b93bbe25024b33947994d3
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="visual-foxpro-field-data-types"></a>Типы данных полей Visual FoxPro
В следующей таблице перечислены значения для *FieldType* аргумент в инструкции ALTER TABLE и CREATE TABLE и указывает, является ли *nFieldWidth* и *nPrecision* аргументы Обязательно.  
  
|*FieldType*|*NFieldWidth*|*nPrecision*|Описание|  
|-----------------|-------------------|------------------|-----------------|  
|B|-|d|Double|  
|C|Нет|-|Символ поле шириной *n*|  
|D|-|-|Дата|  
|Ж|Нет|d|С плавающей запятой числовое поле шириной *n* с *d* десятичных разрядов|  
|Ж|-|-|Общие сведения|  
|I|-|-|Целочисленный|  
|L|-|-|Логические|  
|M|-|-|MEMO|  
|Нет|Нет|d|Числовое поле шириной *n* с *d* десятичных разрядов|  
|T|-|-|DateTime|  
|Да|-|-|Измерение валют|
