---
title: SQLColAttributes (драйвер для Excel) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Excel driver [ODBC], SQLColAttributes
- SQLColAttribute function [ODBC], Excel Driver
ms.assetid: 7c4833e3-ff0c-4313-9ab8-21379ceab656
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 67ba6df9955a1b138ebb919d410ef7817e1fb48e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62666276"
---
# <a name="sqlcolattributes-excel-driver"></a>SQLColAttributes (драйвер для Excel)
> [!NOTE]  
>  В этом разделе сведения конкретного драйвера Excel. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|attribute|Комментарии|  
|---------------|--------------|  
|SQL_COLUMN_DISPLAY_SIZE|Для данных LONGVARBINARY SQL_COLUMN_DISPLAY_SIZE составляет максимальную длину столбца, не Максимальная длина столбца времени 2.|  
|SQL_OWNER_NAME|Пустая строка ("») возвращается в этом столбце, так как имя владельца не поддерживается.|  
|SQL_QUALIFIER_NAME|Возвращает путь к каталогу.|  
|SQL_COLUMN_SEARCHABLE|LONGVARBINARY и LONGVARCHAR столбцы помечаются как SQL_UNSEARCHABLE.<br /><br /> Двоичный файл фиксированной и переменной длины и символьные типы данных доступны для поиска, несмотря на то, что LONGVARBINARY и LONGVARCHAR не.|  
  
> [!NOTE]  
>  Вышесказанное не полный список атрибутов, возвращенный методом **SQLColAttributes**.
