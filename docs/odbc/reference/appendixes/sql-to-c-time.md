---
title: 'СЗЛ в C: Время Документы Майкрософт'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- converting data from SQL to C types [ODBC], time
- time data type [ODBC]
- data conversions from SQL to C types [ODBC], time
ms.assetid: 6dc59973-7bb5-40f1-87c8-5bf68b3bf2ee
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ebd146abf650861099a40bf91b2641df768b343d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81296384"
---
# <a name="sql-to-c-time"></a>Преобразование данных из SQL в C: время
Идентификатор времени типа данных ODBC S'L:  
  
 SQL_TYPE_TIME  
  
 В следующей таблице показаны типы данных ODBC C, к которым могут быть преобразованы данные S'L. Для объяснения столбцов и терминов в [Converting Data from SQL to C Data Types](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md)таблице см.  
  
|Идентификатор типа C|Тест|**TargetValuePtr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR|*BufferLength* > характер байт длина<br /><br /> *9* <= *БуферНая длина* <- длина байт-персонажа<br /><br /> *Буферная длина* < 9|Данные<br /><br /> Truncated данные<br /><br /> Не определено.|Длина данных в байтах<br /><br /> Длина данных в байтах<br /><br /> Не определено.|Недоступно<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_WCHAR|*BufferLength* > длина персонажа<br /><br /> *9* <= *Буферная длина* <- длина персонажа<br /><br /> *Буферная длина* < 9|Данные<br /><br /> Truncated данные<br /><br /> Не определено.|Длина данных в символах<br /><br /> Длина данных в символах<br /><br /> Не определено.|Недоступно<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_BINARY|Длина данных байт <- *BufferLength*<br /><br /> Длина данных байт > *BufferLength*|Данные<br /><br /> Не определено.|Длина данных в байтах<br /><br /> Не определено.|Недоступно<br /><br /> 22003|  
|SQL_C_TYPE_TIME|Ни один из них|Данные|6-е время|Недоступно|  
|SQL_C_TYPE_TIMESTAMP|Ни один из них|Данные|16 лет|Недоступно|  
  
 Дробные секунды времени усечены.  
  
 Значение *BufferLength* игнорируется для этого преобразования. Драйвер предполагает, что размер*TargetValuePtr* — это размер типа данных C.  
  
 Поля даты структуры метки времени устанавливаются к текущей дате, а дробное секундное поле структуры метки времени устанавливается до нуля.  
  
 Это размер соответствующего типа данных C.  
  
 Когда данные S'L преобразуются в данные символа C, полученная строка находится в формате «*hh*:*mm*:*ss».* Этот формат не зависит от настройки windows® страны.
