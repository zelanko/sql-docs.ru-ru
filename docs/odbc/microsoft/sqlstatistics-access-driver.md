---
title: S'LСтатистика (Драйвер доступа) Документы Майкрософт
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
ms.openlocfilehash: f75f41bf63cbf224772955effa0f120b5d384111
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299364"
---
# <a name="sqlstatistics-access-driver"></a>SQLStatistics (драйвер для Access)
> [!NOTE]  
>  Эта тема содержит информацию о драйверах доступа. Для получения общей информации об этой [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md)функции, см.  
  
|Столбец|Комментарии|  
|------------|--------------|  
|TABLE_QUALIFIER|Путь к файлу базы данных возвращается для Microsoft Access.<br /><br /> Сопоставление шаблонов не поддерживается в аргументе *szTableQualifier.*|  
|TABLE_OWNER|NULL возвращается в этой колонке, так как имя владельца не поддерживается.|  
|TABLE_NAME|Неразграниченное название таблицы.<br /><br /> Сопоставление шаблонов не поддерживается в аргументе *szTableName.*|  
|INDEX_QUALIFIER|NULL всегда возвращается.|  
|INDEX_NAME|Индекс-зависимый.|  
|TYPE|Для TYPE будет возвращена только SQL_TABLE_STAT или SQL_INDEX_OTHER.|  
|SEQ_IN_INDEX|Индекс-зависимый.|  
|COLUMN_NAME|Индекс-зависимый.|  
|COLLATION|Индекс-зависимый.|  
|CARDINALITY|Возвращается только для Microsoft Access.|  
|PAGES|NULL всегда возвращается.|  
  
 Фильтрация основана на уникальности (аргумент *fUnique).* Параметр *fAccuracy* игнорируется.
