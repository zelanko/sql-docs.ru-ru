---
title: 'СЗЛ в C: Дата Документы Майкрософт'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- converting data from SQL to C types [ODBC], date
- date data type [ODBC]
- data conversions from SQL to C types [ODBC], date
ms.assetid: 703c7960-9cf4-4d7a-9920-53b29c184f97
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fe9656c0c02c0ff5a10029525da3d38280530cc3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81296534"
---
# <a name="sql-to-c-date"></a>Преобразование данных из SQL в C: даты
Идентификатор омичи даты типа данных ODBC S'L:  
  
 SQL_TYPE_DATE  
  
 В следующей таблице показаны типы данных ODBC C, к которым могут быть преобразованы данные с s'L. Для объяснения столбцов и терминов в [Converting Data from SQL to C Data Types](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md)таблице см.  
  
|Идентификатор типа C|Тест|**TargetValuePtr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR|*BufferLength* > характер байт длина<br /><br /> 11 <- *<буферной <* - длина байт-персонажа<br /><br /> *БуферНая длина* < 11|Данные<br /><br /> Truncated данные<br /><br /> Не определено.|10<br /><br /> Длина данных в байтах<br /><br /> Не определено.|Недоступно<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_WCHAR|*BufferLength* > длина персонажа<br /><br /> 11 <- *<буферной <* - длина персонажа<br /><br /> *БуферНая длина* < 11|Данные<br /><br /> Truncated данные<br /><br /> Не определено.|10<br /><br /> Длина данных в символах<br /><br /> Не определено.|Недоступно<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_BINARY|Длина данных байт <- *BufferLength*<br /><br /> Длина данных байт > *BufferLength*|Данные<br /><br /> Не определено.|Длина данных в байтах<br /><br /> Не определено.|Недоступно<br /><br /> 22003|  
|SQL_C_TYPE_DATE|Нет|Данные|6 кв. м.|Недоступно|  
|SQL_C_TYPE_TIMESTAMP|Нет|Данные|16.00|Недоступно|  
  
 Значение *BufferLength* игнорируется для этого преобразования. Драйвер предполагает, что размер*TargetValuePtr* — это размер типа данных C.  
  
 Поля времени структуры метки времени сведены к нулю.  
  
 Это размер соответствующего типа данных C.  
  
 При преобразовании данных о дате S'L в данные символа C получена строка в формате *«yyyy*-*mm*-*dd».* Этот формат не зависит от настройки windows® страны.
