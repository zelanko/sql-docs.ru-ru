---
title: 'SQL в C: битовые | Документация Майкрософт'
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
manager: craigg
ms.openlocfilehash: f7ff0bd2988460596623eb47ded276392dc3d443
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47767592"
---
# <a name="sql-to-c-bit"></a>Преобразование данных из SQL в C: битовые данные
Идентификатор для типа данных bit ODBC SQL — это:  
  
 SQL_BIT  
  
 Следующая таблица показывает ODBC C типы данных, к которым можно преобразовать bit data системы SQL. Описание столбцов и условия в таблице, см. в разделе [преобразование данных из SQL в типы данных C](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).  
  
|Идентификатор типа C|Тест|**TargetValuePtr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR<br /><br /> SQL_C_WCHAR|*BufferLength* > 1<br /><br /> *BufferLength* < = 1|Данные <br /><br /> Не определено.|1<br /><br /> Не определено.|н/д<br /><br /> 22003|  
|SQL_C_STINYINT<br /><br /> SQL_C_UTINYINT<br /><br /> SQL_C_TINYINT<br /><br /> SQL_C_SBIGINT<br /><br /> SQL_C_UBIGINT<br /><br /> SQL_C_SSHORT<br /><br /> SQL_C_USHORT<br /><br /> SQL_C_SHORT<br /><br /> SQL_C_SLONG<br /><br /> SQL_C_ULONG<br /><br /> SQL_C_LONG<br /><br /> SQL_C_FLOAT<br /><br /> SQL_C_DOUBLE<br /><br /> SQL_C_NUMERIC|Нет [a]|Данные |Размер типа данных C|н/д|  
|SQL_C_BIT|Нет [a]|Данные |1 [b]|н/д|  
|SQL_C_BINARY|*BufferLength* > = 1<br /><br /> *BufferLength* < 1|Данные <br /><br /> Не определено.|1<br /><br /> Не определено.|н/д<br /><br /> 22003|  
  
 [a] значение *BufferLength* игнорируется для этого преобразования. Драйвер предполагает, что размер **TargetValuePtr* — это размер типа данных C.  
  
 [b] это размер соответствующего типа данных C.  
  
 При преобразовании в символьный C bit data системы SQL возможными значениями являются «0» и «1».
