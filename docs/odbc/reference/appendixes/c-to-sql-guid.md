---
title: 'C в SQL: ИДЕНТИФИКАТОР GUID | Документация Майкрософт'
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
manager: craigg
ms.openlocfilehash: af0ed8307652ccf45e7fbfffb6c00355c8a8b004
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63159354"
---
# <a name="c-to-sql-guid"></a>C в SQL: GUID
Идентификатор для типа данных GUID ODBC C является:  
  
 SQL_C_GUID  
  
 Следующая таблица показывает ODBC SQL типы данных, к которым GUID C данные могут преобразовываться. Описание столбцов и условия в таблице, см. в разделе [преобразование данных из C в типы данных SQL](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md).  
  
|Идентификатор типа SQL|Тест|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR|Длина столбца в байтах > = 36|н/д|  
|SQL_VARCHAR|Столбец байтов длиной < 36|22001|  
|SQL_LONGVARCHAR|Значение данных не является допустимым идентификатором GUID|22018|  
|SQL_WCHAR|Длина столбца символ > = 36|н/д|  
|SQL_WVARCHAR|Длина < 36 символов столбца|22001|  
|SQL_WLONGVARCHAR|Значение данных не является допустимым идентификатором GUID|22018|  
|SQL_GUID|Нет [a]|н/д|  
  
 [a] все шестнадцатеричных значений могут использоваться в качестве идентификатора GUID.  
  
 Драйвер не учитывает значение длины и индикатора, при преобразовании данных из типа данных GUID C и предполагает, что размер буфера данных размер типа данных GUID C. Значение длины и индикатора, переданное в *StrLen_or_Ind* аргумента в **SQLPutData** и в указанный буфер с *StrLen_or_IndPtr* аргумента в **SQLBindParameter**. Буфер данных указывается с помощью *DataPtr* аргумента в **SQLPutData** и *ParameterValuePtr* аргумента в **SQLBindParameter**.
