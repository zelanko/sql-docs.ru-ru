---
title: SQLColAttributes (драйвер для Access) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLColAttribute function [ODBC], Access Driver
- Access driver [ODBC], SQLColAttributes
ms.assetid: adb6f81d-e8c7-4748-9b1d-f7a053788bbc
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0c78229da8a577670ba31ae82c679bfefbef4f80
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67903979"
---
# <a name="sqlcolattributes-access-driver"></a>SQLColAttributes (драйвер для Access)
> [!NOTE]  
>  В этом разделе сведения конкретного драйвера доступа. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|attribute|Комментарии|  
|---------------|--------------|  
|SQL_COLUMN_DISPLAY_SIZE|Для данных LONGVARBINARY SQL_COLUMN_DISPLAY_SIZE составляет максимальную длину столбца, не Максимальная длина столбца времени 2.|  
|SQL_OWNER_NAME|Пустая строка ("») возвращается в этом столбце, так как имя владельца не поддерживается.|  
|SQL_QUALIFIER_NAME|Возвращает путь к файлу базы данных.|  
|SQL_COLUMN_SEARCHABLE|LONGVARBINARY и LONGVARCHAR столбцы помечаются как SQL_UNSEARCHABLE.<br /><br /> Двоичный файл фиксированной и переменной длины и символьные типы данных доступны для поиска, несмотря на то, что LONGVARBINARY и LONGVARCHAR не.|  
  
> [!NOTE]  
>  Вышесказанное не полный список атрибутов, возвращенный методом **SQLColAttributes**.
