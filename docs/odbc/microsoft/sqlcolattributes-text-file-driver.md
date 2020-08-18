---
description: SQLColAttributes (драйвер для текстовых файлов)
title: SQLColAttributes (драйвер для текстовых файлов) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- text file driver [ODBC], SQLColAttributes
- SQLColAttribute function [ODBC], Text File Driver
ms.assetid: 132fd1c0-1921-4a7d-910e-aedf1bff5453
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ee659f984f75b3ede7fc09e698e58b427158f9fc
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88412210"
---
# <a name="sqlcolattributes-text-file-driver"></a>SQLColAttributes (драйвер для текстовых файлов)
> [!NOTE]  
>  В этом разделе содержатся сведения, относящиеся к драйверам текстовых файлов. Общие сведения об этой функции см. в соответствующем разделе [справочника по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|attribute|Комментарии|  
|---------------|--------------|  
|SQL_COLUMN_DISPLAY_SIZE|Для данных LONGVARBINARY SQL_COLUMN_DISPLAY_SIZE — это максимальная длина столбца, а не максимальная длина столбца, равная 2.|  
|SQL_OWNER_NAME|В этом столбце возвращается пустая строка (""), так как имя владельца не поддерживается.|  
|SQL_QUALIFIER_NAME|Возвращается путь к каталогу.|  
|SQL_COLUMN_SEARCHABLE|Столбцы LONGVARBINARY и LONGVARCHAR выводятся как SQL_UNSEARCHABLE.<br /><br /> Двоичные и символьные типы данных с фиксированной длиной и переменной длиной поддерживают поиск, даже если LONGVARBINARY и LONGVARCHAR не являются.|
