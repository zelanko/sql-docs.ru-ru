---
description: Типы данных полей Visual FoxPro
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 65410f16367af8764e8572c58e53831f3f7b9cda
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88449056"
---
# <a name="visual-foxpro-field-data-types"></a>Типы данных полей Visual FoxPro
В следующей таблице перечислены значения аргумента *FieldType* в инструкции ALTER table и CREATE TABLE и указано, требуются ли аргументы *нфиелдвидс* и *нпреЦисион* .  
  
|*FieldType*|*нфиелдвидс*|*нпреЦисион*|Описание|  
|-----------------|-------------------|------------------|-----------------|  
|B|-|d|Double|  
|C|Нет|-|Символьное поле ширины *n*|  
|D|-|-|Дата|  
|F|Нет|d|Плавающее числовое поле Width *n* с *d* десятичными разрядами|  
|G|-|-|Общие сведения|  
|I|-|-|Целое число|  
|L|-|-|Логический|  
|M|-|-|Memo|  
|Нет|Нет|d|Числовое поле ширины *n* с *d* десятичными разрядами|  
|T|-|-|Дата и время|  
|Да|-|-|Валюта|
