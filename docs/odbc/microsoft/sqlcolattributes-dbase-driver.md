---
title: SQLColAttributes (драйвер для dBASE) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLColAttribute function [ODBC], dBASE Driver
- DBase driver [ODBC], SQLColAttributes
ms.assetid: ed44de2b-0b01-4dce-a340-f5eb3aac30b7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 56d6a7cb3c2c071191a956c6aaf11479810698f8
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62666518"
---
# <a name="sqlcolattributes-dbase-driver"></a>SQLColAttributes (драйвер для dBASE)
> [!NOTE]  
>  В этом разделе сведения для dBASE специфические для драйвера. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|attribute|Комментарии|  
|---------------|--------------|  
|SQL_COLUMN_DISPLAY_SIZE|Для данных LONGVARBINARY SQL_COLUMN_DISPLAY_SIZE составляет максимальную длину столбца, не Максимальная длина столбца времени 2.|  
|SQL_OWNER_NAME|Пустая строка ("») возвращается в этом столбце, так как имя владельца не поддерживается.|  
|SQL_QUALIFIER_NAME|Возвращает путь к каталогу.|  
|SQL_COLUMN_SEARCHABLE|LONGVARBINARY и LONGVARCHAR столбцы помечаются как SQL_UNSEARCHABLE.<br /><br /> Двоичный файл фиксированной и переменной длины и символьные типы данных доступны для поиска, несмотря на то, что LONGVARBINARY и LONGVARCHAR не.|  
  
> [!NOTE]  
>  Вышесказанное не полный список атрибутов, возвращенный методом **SQLColAttributes**.
