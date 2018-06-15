---
title: 'C в SQL: GUID | Документы Microsoft'
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
- converting data from c to SQL types [ODBC], guid
- data conversions from C to SQL types [ODBC], guid
- GUID data type [ODBC]
ms.assetid: 9168b0b6-a828-4fef-b8cd-bdf439776f23
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fc27c02bdd31cf2e18f6bfbb14e48666760a29a6
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32905559"
---
# <a name="c-to-sql-guid"></a>C в SQL: GUID
Идентификатор для типа данных GUID ODBC C является:  
  
 SQL_C_GUID  
  
 Следующая таблица показывает ODBC SQL типы данных, к которым может быть преобразован данных GUID C. Объяснение столбцы и условия в таблице см. в разделе [преобразование данных из C в типы данных SQL](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md).  
  
|Идентификатор типа SQL|Тест|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR|Длина столбца в байтах > = 36|н/д|  
|SQL_VARCHAR|Столбец байтов длина < 36|22001|  
|SQL_LONGVARCHAR|Значение данных не является допустимым идентификатором GUID|22018|  
|SQL_WCHAR|Длина столбца символ > = 36|н/д|  
|SQL_WVARCHAR|Длина < 36 символов столбца|22001|  
|SQL_WLONGVARCHAR|Значение данных не является допустимым идентификатором GUID|22018|  
|SQL_GUID|Нет []|н/д|  
  
 [] все шестнадцатеричных значений могут использоваться в качестве идентификатора GUID.  
  
 Драйвер не учитывает значение длины/индикатора при преобразовании данных из типа данных GUID C и предполагает, что размер буфера данных размер типа данных GUID C. Переданное значение длины/индикатора *StrLen_or_Ind* аргумент в **SQLPutData** и в указанный буфер с *StrLen_or_IndPtr* аргумент в **SQLBindParameter**. Буфер данных задается с помощью *DataPtr* аргумент в **SQLPutData** и *ParameterValuePtr* аргумент в **SQLBindParameter**.
