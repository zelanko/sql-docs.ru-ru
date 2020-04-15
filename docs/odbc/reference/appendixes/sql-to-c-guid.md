---
title: 'СЗЛ в C: GUID Документы Майкрософт'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- converting data from SQL to C types [ODBC], GUID
- data conversions from SQL to C types [ODBC], guid
- GUID data type [ODBC]
ms.assetid: cf56c684-c261-4b89-994a-db14ab2241d6
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f0f247bc4cb411d535050d7c78e0ea42cc144b0e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81296464"
---
# <a name="sql-to-c-guid"></a>Преобразование данных из SQL в C: GUID
Идентификатор для типа данных GUID ODBC S'L:  
  
 SQL_GUID  
  
 В следующей таблице показаны типы данных ODBC C, в которые могут быть преобразованы данные GUID S'L. Для объяснения столбцов и терминов в [Converting Data from SQL to C Data Types](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md)таблице см.  
  
|Идентификатор типа C|Тест|**TargetValuePtr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR|*BufferLength* > характер байт длина|Данные|36|Недоступно|  
||*БуферНая длина* < 37|Не определено.|Не определено.|22003|  
|SQL_C_WCHAR|*BufferLength* > длина персонажа|Данные|36|Недоступно|  
||*БуферНая длина* < 37|Не определено.|Не определено.|22003|  
|SQL_C_BINARY|Длина байт \< = данных *BufferLength*|Данные|Длина данных в байтах|Недоступно|  
||Длина данных байт > *BufferLength*|Не определено.|Не определено.|22003|  
|SQL_C_GUID|Нет|Данные|16.00|Недоступно|  
  
 Значение *BufferLength* игнорируется для этого преобразования. Драйвер предполагает, что размер*TargetValuePtr* — это размер типа данных C.  
  
 Это размер соответствующего типа данных C.
