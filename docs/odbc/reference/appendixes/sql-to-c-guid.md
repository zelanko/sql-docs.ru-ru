---
title: 'SQL в C: GUID | Документы Microsoft'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- converting data from SQL to C types [ODBC], GUID
- data conversions from SQL to C types [ODBC], guid
- GUID data type [ODBC]
ms.assetid: cf56c684-c261-4b89-994a-db14ab2241d6
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bff530732652d76d04ec6c0088b4563f38ea5877
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sql-to-c-guid"></a>SQL в C: GUID
Идентификатор для типа данных GUID ODBC SQL является:  
  
 SQL_GUID  
  
 Следующая таблица показывает ODBC C типы данных, к которым может быть преобразован GUID SQL данных. Объяснение столбцы и условия в таблице см. в разделе [преобразование данных из SQL в типы данных C](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).  
  
|Идентификатор типа C|Тест|**TargetValuePtr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR|*BufferLength* > байт символов|Данные |36|н/д|  
||*BufferLength* < 37|Не определено.|Не определено.|22003|  
|SQL_C_WCHAR|*BufferLength* > Длина символьной|Данные |36|н/д|  
||*BufferLength* < 37|Не определено.|Не определено.|22003|  
|SQL_C_BINARY|Байтовая длина данных \< =  *BufferLength*|Данные |Длина данных в байтах|н/д|  
||Байтовая длина данных > *BufferLength*|Не определено.|Не определено.|22003|  
|SQL_C_GUID|Нет []|Данные |16 [b]|н/д|  
  
 [] значение *BufferLength* учитывается для этого преобразования. Драйвер предполагает, что размер **TargetValuePtr* — это размер типа данных C.  
  
 [b] это размер соответствующие типы данных C.
