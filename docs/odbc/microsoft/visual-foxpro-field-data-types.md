---
title: Типы данных полей Visual FoxPro | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- field data types [ODBC]
- Visual FoxPro ODBC driver [ODBC], data types
ms.assetid: 50b733dc-679a-4b10-bc5d-98bb474dead2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 07aa06eae9f1e75a047bdd302754d884790436e1
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47806133"
---
# <a name="visual-foxpro-field-data-types"></a>Типы данных полей Visual FoxPro
В следующей таблице перечислены значения для *FieldType* аргумент в инструкции ALTER TABLE и CREATE TABLE и указывает ли *nFieldWidth* и *nPrecision* аргументы Обязательно.  
  
|*FieldType*|*NFieldWidth*|*nPrecision*|Описание|  
|-----------------|-------------------|------------------|-----------------|  
|B|-|d|Double|  
|C|Нет|-|Символ поле шириной *n*|  
|D|-|-|Дата|  
|Ж|Нет|d|С плавающей запятой числовое поле шириной *n* с *d* десятичных разрядов|  
|Ж|-|-|Общие|  
|I|-|-|Целочисленный|  
|L|-|-|Логические|  
|M|-|-|MEMO|  
|Нет|Нет|d|Числовое поле шириной *n* с *d* десятичных разрядов|  
|T|-|-|DateTime|  
|Да|-|-|CURRENCY|
