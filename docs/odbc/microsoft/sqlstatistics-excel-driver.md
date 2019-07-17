---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1c36d68f42b9b7f76310c453d704c6815ee6de22
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68132467"
---
# <a name="sqlstatistics-excel-driver"></a>SQLStatistics (драйвер для Excel)
> [!NOTE]  
>  В этом разделе сведения конкретного драйвера Excel. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
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
