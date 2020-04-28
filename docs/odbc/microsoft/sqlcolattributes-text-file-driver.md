---
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
ms.openlocfilehash: 3eafe02ba76dcaa6078abee862d743deb4765bdd
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81307925"
---
# <a name="sqlcolattributes-text-file-driver"></a>SQLColAttributes (драйвер для текстовых файлов)
> [!NOTE]  
>  В этом разделе содержатся сведения, относящиеся к драйверам текстовых файлов. Общие сведения об этой функции см. в соответствующем разделе [справочника по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Атрибут|Комментарии|  
|---------------|--------------|  
|SQL_COLUMN_DISPLAY_SIZE|Для данных LONGVARBINARY SQL_COLUMN_DISPLAY_SIZE — это максимальная длина столбца, а не максимальная длина столбца, равная 2.|  
|SQL_OWNER_NAME|В этом столбце возвращается пустая строка (""), так как имя владельца не поддерживается.|  
|SQL_QUALIFIER_NAME|Возвращается путь к каталогу.|  
|SQL_COLUMN_SEARCHABLE|Столбцы LONGVARBINARY и LONGVARCHAR выводятся как SQL_UNSEARCHABLE.<br /><br /> Двоичные и символьные типы данных с фиксированной длиной и переменной длиной поддерживают поиск, даже если LONGVARBINARY и LONGVARCHAR не являются.|
