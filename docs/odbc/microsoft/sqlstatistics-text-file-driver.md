---
title: SQLStatistics (драйвер для текстовых файлов) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- text file driver [ODBC], SQLStatistics
- SQLStatistics function [ODBC], Text File Driver
ms.assetid: 311afc01-d656-425f-be43-4a8e7cbc9a97
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 783b036d37e63d33f9aa89cad4eb3bb4bfb2d30a
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62686974"
---
# <a name="sqlstatistics-text-file-driver"></a>SQLStatistics (драйвер для текстовых файлов)
> [!NOTE]  
>  В этом разделе сведения конкретного драйвера текстовый файл. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Столбец|Комментарии|  
|------------|--------------|  
|TABLE_QUALIFIER|Путь к каталогу.<br /><br /> Сопоставление шаблонов не поддерживается в *szTableQualifier* аргумент.|  
|TABLE_OWNER|В этом столбце возвращается значение NULL, так как имя владельца не поддерживается.|  
|TABLE_NAME|Имя неразделенный таблицы.<br /><br /> Сопоставление шаблонов не поддерживается в *szTableName* аргумент.|  
|INDEX_QUALIFIER|Всегда возвращается значение NULL.|  
|INDEX_NAME|Зависящих от индекса.|  
|TYPE|Для ТИПА будет возвращаться только SQL_TABLE_STAT или SQL_INDEX_OTHER.|  
|SEQ_IN_INDEX|Зависящих от индекса.|  
|COLUMN_NAME|Зависящих от индекса.|  
|COLLATION|Зависящих от индекса.|  
|PAGES|Всегда возвращается значение NULL.|  
  
 Фильтрация основана на уникальность ( *fUnique* аргумент). *FAccuracy* параметр учитывается.
