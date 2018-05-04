---
title: Типы данных полей Visual FoxPro | Документы Microsoft
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
- field data types [ODBC]
- Visual FoxPro ODBC driver [ODBC], data types
ms.assetid: 50b733dc-679a-4b10-bc5d-98bb474dead2
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cf6df134c5a4ad54e574e42e57d7a68e10b4e077
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
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
