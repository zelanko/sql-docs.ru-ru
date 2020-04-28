---
title: 'C в SQL: GUID | Документация Майкрософт'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- converting data from c to SQL types [ODBC], guid
- data conversions from C to SQL types [ODBC], guid
- GUID data type [ODBC]
ms.assetid: 9168b0b6-a828-4fef-b8cd-bdf439776f23
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b3b559499273e885e23da10d9093a0ce9ff92393
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81306625"
---
# <a name="c-to-sql-guid"></a>Преобразование из C в SQL: GUID
Идентификатор для типа данных ODBC C:  
  
 SQL_C_GUID  
  
 В следующей таблице показаны типы данных ODBC SQL, к которым могут быть преобразованы данные GUID C. Описание столбцов и терминов в таблице см. в разделе [Преобразование данных из C в типы данных SQL](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md).  
  
|Идентификатор типа SQL|Тест|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR|Длина байта столбца >= 36|Недоступно|  
|SQL_VARCHAR|Длина байта столбца < 36|22001|  
|SQL_LONGVARCHAR|Значение данных не является допустимым идентификатором GUID|22018|  
|SQL_WCHAR|Длина символа столбца >= 36|Недоступно|  
|SQL_WVARCHAR|Длина символов столбца < 36|22001|  
|SQL_WLONGVARCHAR|Значение данных не является допустимым идентификатором GUID|22018|  
|SQL_GUID|Нет [a]|Недоступно|  
  
 [a] все шестнадцатеричные значения допустимы в виде идентификатора GUID.  
  
 Драйвер игнорирует значение длины или индикатора при преобразовании данных из типа данных GUID C и предполагает, что размер буфера данных равен размеру типа данных GUID C. Значение length/индикатора передается в аргументе *StrLen_Or_Ind* в **SQLPutData** и в буфере, указанном аргументом *StrLen_or_IndPtr* в **SQLBindParameter**. Буфер данных указывается с помощью аргумента *датаптр* в **SQLPutData** и аргумента *параметервалуептр* в **SQLBindParameter**.
