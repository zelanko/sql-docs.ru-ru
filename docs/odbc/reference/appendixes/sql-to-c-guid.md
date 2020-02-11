---
title: 'С SQL на C: GUID | Документация Майкрософт'
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1a2ed3cffcb196cb09841df3b54fbfab53e22477
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68056874"
---
# <a name="sql-to-c-guid"></a>Преобразование данных из SQL в C: GUID
Идентификатором для типа данных ODBC SQL является:  
  
 SQL_GUID  
  
 В следующей таблице показаны типы данных ODBC C, к которым могут быть преобразованы данные SQL в GUID. Описание столбцов и терминов в таблице см. в разделе [Преобразование данных из SQL в типы данных C](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).  
  
|Идентификатор типа C|Тест|**таржетвалуептр*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR|*BufferLength* длина байта > символов|Данные|36|Недоступно|  
||*BufferLength* < 37|Не определено|Не определено|22003|  
|SQL_C_WCHAR|Длина *BufferLength* > символов|Данные|36|Недоступно|  
||*BufferLength* < 37|Не определено|Не определено|22003|  
|SQL_C_BINARY|Длина \< =  *BufferLength* данных в байтах|Данные|Длина данных в байтах|Недоступно|  
||Длина байта данных > *BufferLength*|Не определено|Не определено|22003|  
|SQL_C_GUID|Нет [a]|Данные|16 [b]|Недоступно|  
  
 [a] значение *BufferLength* игнорируется для этого преобразования. Драйвер предполагает, что размер **таржетвалуептр* — это размер типа данных C.  
  
 [b] это размер соответствующего типа данных C.
