---
title: 'SQL в C: Бит | Документация Майкрософт'
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8d00a3c26d842b196e20861da6d8ae3e818d4cbe
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68056902"
---
# <a name="sql-to-c-bit"></a>SQL в C: bit
Идентификатор для типа данных bit ODBC SQL — это:  
  
 SQL_BIT  
  
 Следующая таблица показывает ODBC C типы данных, к которым можно преобразовать bit data системы SQL. Описание столбцов и условия в таблице, см. в разделе [преобразование данных из SQL в типы данных C](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).  
  
|Идентификатор типа C|Тест|**TargetValuePtr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR<br /><br /> SQL_C_WCHAR|*BufferLength* > 1<br /><br /> *BufferLength* < = 1|Data<br /><br /> Не определено.|1<br /><br /> Не определено.|Н/Д<br /><br /> 22003|  
|SQL_C_STINYINT<br /><br /> SQL_C_UTINYINT<br /><br /> SQL_C_TINYINT<br /><br /> SQL_C_SBIGINT<br /><br /> SQL_C_UBIGINT<br /><br /> SQL_C_SSHORT<br /><br /> SQL_C_USHORT<br /><br /> SQL_C_SHORT<br /><br /> SQL_C_SLONG<br /><br /> SQL_C_ULONG<br /><br /> SQL_C_LONG<br /><br /> SQL_C_FLOAT<br /><br /> SQL_C_DOUBLE<br /><br /> SQL_C_NUMERIC|Нет [a]|Data|Размер типа данных C|Н/Д|  
|SQL_C_BIT|Нет [a]|Data|1 [b]|Н/Д|  
|SQL_C_BINARY|*BufferLength* > = 1<br /><br /> *BufferLength* < 1|Data<br /><br /> Не определено.|1<br /><br /> Не определено.|Н/Д<br /><br /> 22003|  
  
 [a] значение *BufferLength* игнорируется для этого преобразования. Драйвер предполагает, что размер **TargetValuePtr* — это размер типа данных C.  
  
 [b] это размер соответствующего типа данных C.  
  
 При преобразовании в символьный C bit data системы SQL возможными значениями являются «0» и «1».
