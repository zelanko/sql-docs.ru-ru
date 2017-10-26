---
title: "SQL битом C: | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- converting data from SQL to c types [ODBC], bit
- bit data type [ODBC]
- data conversions from SQL to C types [ODBC], bit
ms.assetid: 0eeaab8b-ad82-4a36-b464-9a1211d5f72c
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 5432e5f4a47dde5b3ad64059a8f2eb1de9ba1691
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="sql-to-c-bit"></a>SQL битом C:
Идентификатор для типа данных bit ODBC SQL является:  
  
 SQL_BIT  
  
 Следующая таблица показывает ODBC C типы данных, к которым может быть преобразован бит данных SQL. Объяснение столбцы и условия в таблице см. в разделе [преобразование данных из SQL в типы данных C](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).  
  
|Идентификатор типа C|Тест|**TargetValuePtr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR<br /><br /> SQL_C_WCHAR|*BufferLength* > 1<br /><br /> *BufferLength* < = 1|data<br /><br /> Не определено.|1<br /><br /> Не определено.|н/д<br /><br /> 22003|  
|SQL_C_STINYINT<br /><br /> SQL_C_UTINYINT<br /><br /> SQL_C_TINYINT<br /><br /> SQL_C_SBIGINT<br /><br /> SQL_C_UBIGINT<br /><br /> SQL_C_SSHORT<br /><br /> SQL_C_USHORT<br /><br /> SQL_C_SHORT<br /><br /> SQL_C_SLONG<br /><br /> SQL_C_ULONG<br /><br /> SQL_C_LONG<br /><br /> SQL_C_FLOAT<br /><br /> SQL_C_DOUBLE<br /><br /> SQL_C_NUMERIC|Нет []|data|Размер типа данных C|н/д|  
|SQL_C_BIT|Нет []|data|1 [b]|н/д|  
|SQL_C_BINARY|*BufferLength* > = 1<br /><br /> *BufferLength* < 1|data<br /><br /> Не определено.|1<br /><br /> Не определено.|н/д<br /><br /> 22003|  
  
 [] значение *BufferLength* учитывается для этого преобразования. Драйвер предполагает, что размер **TargetValuePtr* — это размер типа данных C.  
  
 [b] это размер соответствующие типы данных C.  
  
 При преобразовании в символьный C бит данных SQL возможными значениями являются «0» и «1».

