---
title: 'СЗЛ в C: Бит Документы Майкрософт'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- converting data from SQL to c types [ODBC], bit
- bit data type [ODBC]
- data conversions from SQL to C types [ODBC], bit
ms.assetid: 0eeaab8b-ad82-4a36-b464-9a1211d5f72c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 57688f34c504b221f77c1b66792bf9ee9398df27
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81296754"
---
# <a name="sql-to-c-bit"></a>Преобразование данных из SQL в C: битовые данные
Идентификатор для типа данных от бита ODBC S'L:  
  
 SQL_BIT  
  
 В следующей таблице показаны типы данных ODBC C, в которые могут быть преобразованы данные бита S'L. Для объяснения столбцов и терминов в [Converting Data from SQL to C Data Types](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md)таблице см.  
  
|Идентификатор типа C|Тест|**TargetValuePtr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR<br /><br /> SQL_C_WCHAR|*БуферНая длина* > 1<br /><br /> *<бафференедокдлина* No 1|Данные<br /><br /> Не определено.|1<br /><br /> Не определено.|Недоступно<br /><br /> 22003|  
|SQL_C_STINYINT<br /><br /> SQL_C_UTINYINT<br /><br /> SQL_C_TINYINT<br /><br /> SQL_C_SBIGINT<br /><br /> SQL_C_UBIGINT<br /><br /> SQL_C_SSHORT<br /><br /> SQL_C_USHORT<br /><br /> SQL_C_SHORT<br /><br /> SQL_C_SLONG<br /><br /> SQL_C_ULONG<br /><br /> SQL_C_LONG<br /><br /> SQL_C_FLOAT<br /><br /> SQL_C_DOUBLE<br /><br /> SQL_C_NUMERIC|Нет|Данные|Размер типа данных C|Недоступно|  
|SQL_C_BIT|Нет|Данные|1 b|Недоступно|  
|SQL_C_BINARY|*>бафференедокдлина* No 1<br /><br /> *БуферНая длина* < 1|Данные<br /><br /> Не определено.|1<br /><br /> Не определено.|Недоступно<br /><br /> 22003|  
  
 Значение *BufferLength* игнорируется для этого преобразования. Драйвер предполагает, что размер*TargetValuePtr* — это размер типа данных C.  
  
 Это размер соответствующего типа данных C.  
  
 При преобразовании данных бита S'L в данные символа C возможные значения являются "0" и "1".
