---
title: SQLStatistics (драйвер Paradox) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Paradox driver [ODBC], SQLStatistics
- SQLStatistics function [ODBC], Paradox Driver
ms.assetid: 886cab83-d599-4fbc-9c88-e8cb833aac4b
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 18e323ff059fdeb70fcadd256728de8050eea56a
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32903295"
---
# <a name="sqlstatistics-paradox-driver"></a>SQLStatistics (драйвер Paradox)
> [!NOTE]  
>  В этом разделе сведения драйвера Paradox. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Столбец|Комментарии|  
|------------|--------------|  
|TABLE_QUALIFIER|Путь к каталогу.<br /><br /> Соответствие шаблону не поддерживается в *szTableQualifier* аргумент.|  
|TABLE_OWNER|В этом столбце возвращается значение NULL, так как имя владельца не поддерживается.|  
|TABLE_NAME|Имя таблицы без разделителей.<br /><br /> Соответствие шаблону не поддерживается в *szTableName* аргумент.|  
|INDEX_QUALIFIER|Всегда возвращается значение NULL.|  
|INDEX_NAME|Зависящих от индекса.|  
|TYPE|Для ТИПА будет возвращаться только SQL_TABLE_STAT или SQL_INDEX_OTHER.|  
|SEQ_IN_INDEX|Зависящих от индекса.|  
|COLUMN_NAME|Зависящих от индекса.|  
|COLLATION|Зависящих от индекса.|  
|PAGES|Всегда возвращается значение NULL.|  
  
 Фильтрация основана на уникальность ( *fUnique* аргумент). *FAccuracy* параметр учитывается.
