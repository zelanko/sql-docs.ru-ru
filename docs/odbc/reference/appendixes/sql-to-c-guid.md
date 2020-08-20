---
description: 'Преобразование данных из SQL в C: GUID'
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3a0285850372d78bbe0a24c8707e14e4f5672fb4
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88456505"
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
|SQL_C_BINARY|Длина BufferLength данных в байтах \< =  *BufferLength*|Данные|Длина данных в байтах|Недоступно|  
||Длина байта данных > *BufferLength*|Не определено|Не определено|22003|  
|SQL_C_GUID|Нет [a]|Данные|16 [b]|Недоступно|  
  
 [a] значение *BufferLength* игнорируется для этого преобразования. Драйвер предполагает, что размер **таржетвалуептр* — это размер типа данных C.  
  
 [b] это размер соответствующего типа данных C.
