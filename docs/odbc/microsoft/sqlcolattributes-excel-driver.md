---
title: "SQLColAttributes (драйвер Excel) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Excel driver [ODBC], SQLColAttributes
- SQLColAttribute function [ODBC], Excel Driver
ms.assetid: 7c4833e3-ff0c-4313-9ab8-21379ceab656
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5410a36a2c53c410126191e73740f6e2f4aa0cfd
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="sqlcolattributes-excel-driver"></a>SQLColAttributes (драйвер Excel)
> [!NOTE]  
>  В этом разделе сведения драйвера Excel. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Attribute|Комментарии|  
|---------------|--------------|  
|SQL_COLUMN_DISPLAY_SIZE|Для данных LONGVARBINARY SQL_COLUMN_DISPLAY_SIZE является максимальная длина столбца, не Максимальная длина столбца время 2.|  
|SQL_OWNER_NAME|Пустая строка ("») возвращается в этом столбце, так как имя владельца не поддерживается.|  
|SQL_QUALIFIER_NAME|Путь к каталогу, возвращается.|  
|SQL_COLUMN_SEARCHABLE|LONGVARBINARY и LONGVARCHAR столбцы помечаются как SQL_UNSEARCHABLE.<br /><br /> Binary фиксированной и переменной длины и символьные типы данных с возможностью поиска, даже если LONGVARBINARY и LONGVARCHAR не.|  
  
> [!NOTE]  
>  Это не полный список атрибутов, возвращенный методом **SQLColAttributes**.
