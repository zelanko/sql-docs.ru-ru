---
title: 'C в SQL: Дата | Документация Майкрософт'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- date data type [ODBC]
- converting data from c to SQL types [ODBC], date
- data conversions from C to SQL types [ODBC], date
ms.assetid: bea087d3-911f-418b-b483-d2b5b334da19
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8edb075be1bf64dad8f4ef18924a6396b7c64e80
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63294370"
---
# <a name="c-to-sql-date"></a>C в SQL: Дата
Идентификатор для типа данных ODBC C дата является:  
  
 SQL_C_TYPE_DATE  
  
 Следующая таблица показывает ODBC SQL типы данных, к которым можно преобразовать даты данных C. Описание столбцов и условия в таблице, см. в разделе [преобразование данных из C в типы данных SQL](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md).  
  
|Идентификатор типа SQL|Тест|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR<br /><br /> SQL_VARCHAR<br /><br /> SQL_LONGVARCHAR|Длина столбца в байтах > = 10<br /><br /> Столбец байтов длиной < 10<br /><br /> Значение данных не является допустимой датой|н/д<br /><br /> 22001<br /><br /> 22008|  
|SQL_WCHAR<br /><br /> SQL_WVARCHAR<br /><br /> SQL_WLONGVARCHAR|Длина столбца символ > = 10<br /><br /> Столбец символов длиной < 10<br /><br /> Значение данных не является допустимой датой|н/д<br /><br /> 22001<br /><br /> 22008|  
|SQL_TYPE_DATE|Значение данных представляет собой допустимую дату<br /><br /> Значение данных не является допустимой датой|н/д<br /><br /> 22007|  
|SQL_TYPE_TIMESTAMP|Значение данных представляет собой допустимую дату [a]<br /><br /> Значение данных не является допустимой датой|н/д<br /><br /> 22007|  
  
 [a] части времени отметки времени, равным нулю.  
  
 Сведения о том, какие значения являются допустимыми в структуре SQL_C_TYPE_DATE, см. в разделе [типы данных C](../../../odbc/reference/appendixes/c-data-types.md)ранее в этом приложении.  
  
 При даты C данные преобразуются в символьные данные SQL, результирующий символьных данных находится в "*гггг*-*мм*-*дд*" формат.  
  
 Драйвер не учитывает значение длины и индикатора, при преобразовании данных из типа данных даты C и предполагается, что размер буфера данных размер типа данных date C. Значение длины и индикатора, переданное в *StrLen_or_Ind* аргумента в **SQLPutData** и в указанный буфер с *StrLen_or_IndPtr* аргумента в **SQLBindParameter**. Буфер данных указывается с помощью *DataPtr* аргумента в **SQLPutData** и *ParameterValuePtr* аргумента в **SQLBindParameter**.
