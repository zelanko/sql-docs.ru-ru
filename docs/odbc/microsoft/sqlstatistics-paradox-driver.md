---
title: S'LСтатистика (Парадокс Драйвер) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Paradox driver [ODBC], SQLStatistics
- SQLStatistics function [ODBC], Paradox Driver
ms.assetid: 886cab83-d599-4fbc-9c88-e8cb833aac4b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5e9782eb22e4176a57aab7bdd3823982575a0d55
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299324"
---
# <a name="sqlstatistics-paradox-driver"></a>SQLStatistics (драйвер для Paradox)
> [!NOTE]  
>  Эта тема содержит информацию о драйверах парадокса. Для получения общей информации об этой [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md)функции, см.  
  
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
