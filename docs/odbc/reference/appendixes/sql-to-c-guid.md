---
title: 'SQL в C: ИДЕНТИФИКАТОР GUID | Документация Майкрософт'
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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68056874"
---
# <a name="sql-to-c-guid"></a>SQL в C: GUID
Идентификатор для типа данных GUID ODBC SQL представляет собой:  
  
 SQL_GUID  
  
 Следующая таблица показывает ODBC C типы данных, к которым GUID SQL данные могут преобразовываться. Описание столбцов и условия в таблице, см. в разделе [преобразование данных из SQL в типы данных C](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).  
  
|Идентификатор типа C|Тест|**TargetValuePtr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR|*BufferLength* > байт символов|Data|36|Н/Д|  
||*BufferLength* < 37|Не определено.|Не определено.|22003|  
|SQL_C_WCHAR|*BufferLength* > Длина символьной|Data|36|Н/Д|  
||*BufferLength* < 37|Не определено.|Не определено.|22003|  
|SQL_C_BINARY|Байтовая длина данных \< =  *BufferLength*|Data|Длина данных в байтах|Н/Д|  
||Длину данных в байтах > *BufferLength*|Не определено.|Не определено.|22003|  
|SQL_C_GUID|Нет [a]|Data|16 [b]|Н/Д|  
  
 [a] значение *BufferLength* игнорируется для этого преобразования. Драйвер предполагает, что размер **TargetValuePtr* — это размер типа данных C.  
  
 [b] это размер соответствующего типа данных C.
