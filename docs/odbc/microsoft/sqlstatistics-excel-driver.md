---
description: SQLStatistics (драйвер для Excel)
title: SQLStatistics (драйвер для Excel) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Excel driver [ODBC], SQLStatistics
- SQLStatistics function [ODBC], Excel Driver
ms.assetid: 02506664-8dcc-4bd0-a8bb-d49fcbdd5722
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d6482de71907962fe9734f2167072a56a045a271
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88421578"
---
# <a name="sqlstatistics-excel-driver"></a>SQLStatistics (драйвер для Excel)
> [!NOTE]  
>  В этом разделе приводятся сведения, относящиеся к драйверу Excel. Общие сведения об этой функции см. в соответствующем разделе [справочника по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Столбец|Комментарии|  
|------------|--------------|  
|TABLE_QUALIFIER|Путь к каталогу.<br /><br /> Сопоставление шаблонов не поддерживается в аргументе *сзтаблекуалифиер* .|  
|TABLE_OWNER|Значение NULL возвращается в этом столбце, так как имя владельца не поддерживается.|  
|TABLE_NAME|Имя таблицы, не разделяются.<br /><br /> Сопоставление шаблонов не поддерживается в аргументе *сзтабленаме* .|  
|INDEX_QUALIFIER|Всегда возвращается значение NULL.|  
|INDEX_NAME|Зависит от индекса.|  
|TYPE|Для типа будет возвращено только SQL_TABLE_STAT или SQL_INDEX_OTHER.|  
|SEQ_IN_INDEX|Зависит от индекса.|  
|COLUMN_NAME|Зависит от индекса.|  
|COLLATION|Зависит от индекса.|  
|PAGES|Всегда возвращается значение NULL.|  
  
 Фильтрация основана на уникальности (аргумент *фуникуе* ). Параметр *факкураци* игнорируется.
