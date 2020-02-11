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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5863935ddf595409d48be79dc646c0994ddeb0b8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68019322"
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
