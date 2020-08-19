---
description: SQLStatistics (драйвер для Access)
title: SQLStatistics (драйвер для Access) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Access driver [ODBC], SQLStatistics
- SQLStatistics function [ODBC], Access Driver
ms.assetid: 6117ac77-1020-4f0c-8eed-e671c34c1f21
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 67ea4e7f2553d85837c1ece30327f24298d94c97
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88421588"
---
# <a name="sqlstatistics-access-driver"></a>SQLStatistics (драйвер для Access)
> [!NOTE]  
>  В этом разделе содержатся сведения, относящиеся к драйверу. Общие сведения об этой функции см. в соответствующем разделе [справочника по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Столбец|Комментарии|  
|------------|--------------|  
|TABLE_QUALIFIER|Путь к файлу базы данных возвращается для Microsoft Access.<br /><br /> Сопоставление шаблонов не поддерживается в аргументе *сзтаблекуалифиер* .|  
|TABLE_OWNER|В этом столбце возвращается значение NULL, так как имя владельца не поддерживается.|  
|TABLE_NAME|Имя таблицы, не разделяются.<br /><br /> Сопоставление шаблонов не поддерживается в аргументе *сзтабленаме* .|  
|INDEX_QUALIFIER|Всегда возвращается значение NULL.|  
|INDEX_NAME|Зависит от индекса.|  
|TYPE|Для типа будет возвращено только SQL_TABLE_STAT или SQL_INDEX_OTHER.|  
|SEQ_IN_INDEX|Зависит от индекса.|  
|COLUMN_NAME|Зависит от индекса.|  
|COLLATION|Зависит от индекса.|  
|CARDINALITY|Возвращается только для Microsoft Access.|  
|PAGES|Всегда возвращается значение NULL.|  
  
 Фильтрация основана на уникальности (аргумент *фуникуе* ). Параметр *факкураци* игнорируется.
