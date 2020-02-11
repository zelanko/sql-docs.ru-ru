---
title: SQLStatistics (драйвер для dBASE) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLStatistics function [ODBC], dBASE Driver
- DBase driver [ODBC], SQLStatistics
ms.assetid: 631cec1b-66b7-4103-b9a7-ffd81da3c442
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b3ccd07ad517b52a18dc25ddb3cb3882bd2eb61e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68037824"
---
# <a name="sqlstatistics-dbase-driver"></a>SQLStatistics (драйвер для dBASE)
> [!NOTE]  
>  В этом разделе приводятся сведения, относящиеся к драйверу dBASE. Общие сведения об этой функции см. в соответствующем разделе [справочника по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
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
