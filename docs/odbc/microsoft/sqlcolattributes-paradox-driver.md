---
title: S'LColAttributes (Парадокс Драйвер) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLColAttribute function [ODBC], Paradox Driver
- Paradox driver [ODBC], SQLColAttributes
ms.assetid: bbeef024-d470-4d28-b61b-26997ef41007
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8a18cfa1a3c22795b16427ef341b215cdadb998b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307935"
---
# <a name="sqlcolattributes-paradox-driver"></a>SQLColAttributes (драйвер для Paradox)
> [!NOTE]  
>  Эта тема содержит информацию о драйверах парадокса. Для получения общей информации об этой [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md)функции, см.  
  
|Атрибут|Комментарии|  
|---------------|--------------|  
|SQL_COLUMN_DISPLAY_SIZE|Для данных LONGVARBINARY SQL_COLUMN_DISPLAY_SIZE является максимальной длиной столбца, а не максимальной длиной столбца раз 2.|  
|SQL_OWNER_NAME|В этой колонке возвращается пустая строка ("") из-за неподдерживается имя владельца.|  
|SQL_QUALIFIER_NAME|Возвращается путь к каталогу.|  
|SQL_COLUMN_SEARCHABLE|Как сообщается, SQL_UNSEARCHABLE столбцов LONGVARBINARY и LONGVARCHAR.<br /><br /> Типы бинарных и типы данных с фиксированной длиной и переменной длиной можно найти, несмотря на то, что LONGVARBINARY и LONGVARCHAR не являются.|  
  
> [!NOTE]  
>  Вышеупомянутое не является полным списком атрибутов, возвращенных **S'LColAttributes.**
