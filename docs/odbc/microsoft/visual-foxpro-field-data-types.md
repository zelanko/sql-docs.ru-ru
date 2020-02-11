---
title: Типы данных поля Visual FoxPro | Документация Майкрософт
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
ms.openlocfilehash: 217058bf328677bf375d346ae7201c6eb81efa4e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68087938"
---
# <a name="visual-foxpro-field-data-types"></a>Типы данных полей Visual FoxPro
В следующей таблице перечислены значения аргумента *FieldType* в инструкции ALTER table и CREATE TABLE и указано, требуются ли аргументы *нфиелдвидс* и *нпреЦисион* .  
  
|*FieldType*|*нфиелдвидс*|*нпреЦисион*|Description|  
|-----------------|-------------------|------------------|-----------------|  
|B|-|d|Double|  
|C|Нет|-|Символьное поле ширины *n*|  
|D|-|-|Дата|  
|F|Нет|d|Плавающее числовое поле Width *n* с *d* десятичными разрядами|  
|G.|-|-|Общие сведения|  
|I|-|-|Целое число|  
|L|-|-|Логические|  
|M|-|-|Получена|  
|Нет|Нет|d|Числовое поле ширины *n* с *d* десятичными разрядами|  
|T|-|-|DateTime|  
|Да|-|-|Валюта|
