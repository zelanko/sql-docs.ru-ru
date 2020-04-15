---
title: S'LColAttributes (Драйвер текстовых файлов) Документы Майкрософт
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307925"
---
# <a name="sqlcolattributes-text-file-driver"></a>SQLColAttributes (драйвер для текстовых файлов)
> [!NOTE]  
>  Эта тема предоставляет информацию о драйверах, специфийных для драйверов текста. Для получения общей информации об этой [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md)функции, см.  
  
|Атрибут|Комментарии|  
|---------------|--------------|  
|SQL_COLUMN_DISPLAY_SIZE|Для данных LONGVARBINARY SQL_COLUMN_DISPLAY_SIZE является максимальной длиной столбца, а не максимальной длиной столбца раз 2.|  
|SQL_OWNER_NAME|В этой колонке возвращается пустая строка ("") из-за неподдерживается имя владельца.|  
|SQL_QUALIFIER_NAME|Возвращается путь к каталогу.|  
|SQL_COLUMN_SEARCHABLE|Как сообщается, SQL_UNSEARCHABLE столбцов LONGVARBINARY и LONGVARCHAR.<br /><br /> Типы бинарных и типы данных с фиксированной длиной и переменной длиной можно найти, несмотря на то, что LONGVARBINARY и LONGVARCHAR не являются.|
