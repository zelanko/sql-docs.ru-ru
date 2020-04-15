---
title: S'LСтатистика (водитель dBASE) Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: deec1d7cff9ea1d0f8560b3c9b866cad79e69a25
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299354"
---
# <a name="sqlstatistics-dbase-driver"></a>SQLStatistics (драйвер для dBASE)
> [!NOTE]  
>  Эта тема содержит информацию о драйверах dBASE. Для получения общей информации об этой [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md)функции, см.  
  
|Столбец|Комментарии|  
|------------|--------------|  
|TABLE_QUALIFIER|Путь к каталогу.<br /><br /> Сопоставление шаблонов не поддерживается в аргументе *szTableQualifier.*|  
|TABLE_OWNER|NULL возвращается в этой колонке, поскольку имя владельца не поддерживается.|  
|TABLE_NAME|Неразграниченное название таблицы.<br /><br /> Сопоставление шаблонов не поддерживается в аргументе *szTableName.*|  
|INDEX_QUALIFIER|NULL всегда возвращается.|  
|INDEX_NAME|Индекс-зависимый.|  
|TYPE|Для TYPE будет возвращена только SQL_TABLE_STAT или SQL_INDEX_OTHER.|  
|SEQ_IN_INDEX|Индекс-зависимый.|  
|COLUMN_NAME|Индекс-зависимый.|  
|COLLATION|Индекс-зависимый.|  
|PAGES|NULL всегда возвращается.|  
  
 Фильтрация основана на уникальности (аргумент *fUnique).* Параметр *fAccuracy* игнорируется.
