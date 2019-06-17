---
title: 'C в SQL: Время | Документация Майкрософт'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data conversions from C to SQL types [ODBC], time
- time data type [ODBC]
- converting data from c to SQL types [ODBC], time
ms.assetid: a8da43c9-d9a5-45e5-bd9a-1dd633db2ee0
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7ea11803847505698ea42d13727b6177f3a24bda
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63316528"
---
# <a name="c-to-sql-time"></a>C в SQL: Time
Идентификатор для типа данных ODBC C времени является:  
  
 SQL_C_TYPE_TIME  
  
 Следующая таблица показывает ODBC SQL типы данных, к которым времени C данные могут преобразовываться. Описание столбцов и условия в таблице, см. в разделе [преобразование данных из C в типы данных SQL](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md).  
  
|Идентификатор типа SQL|Тест|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR<br /><br /> SQL_VARCHAR<br /><br /> SQL_LONGVARCHAR|Длина столбца в байтах > = 8<br /><br /> Столбец байтов длиной < 8<br /><br /> Значение данных не является допустимым временем|н/д<br /><br /> 22001<br /><br /> 22008|  
|SQL_WCHAR<br /><br /> SQL_WVARCHAR<br /><br /> SQL_WLONGVARCHAR|Длина столбца символ > = 8<br /><br /> Столбец символов длиной < 8<br /><br /> Значение данных не является допустимым временем|н/д<br /><br /> 22001<br /><br /> 22008|  
|SQL_TYPE_TIME|Значение является действительным значением времени<br /><br /> Значение данных не является допустимым временем|н/д<br /><br /> 22007|  
|SQL_TYPE_TIMESTAMP|Значение является действительным значением времени [a]<br /><br /> Значение данных не является допустимым временем|н/д<br /><br /> 22007|  
  
 [a] дату часть штампа времени имеет значение текущей даты и доли секунды, часть штампа времени, равным нулю.  
  
 Сведения о том, какие значения являются допустимыми в структуре SQL_C_TYPE_TIME, см. в разделе [типы данных C](../../../odbc/reference/appendixes/c-data-types.md)ранее в этом приложении.  
  
 При данных времени C преобразуется в символьные данные SQL, результирующий символьных данных находится в "*hh*:*мм*:*ss*" формат.  
  
 Драйвер не учитывает значение длины и индикатора, при преобразовании данных с момента тип данных C и предполагается, что размер буфера данных размер типа данных времени C. Значение длины и индикатора, переданное в *StrLen_or_Ind* аргумента в **SQLPutData** и в указанный буфер с *StrLen_or_IndPtr* аргумента в **SQLBindParameter**. Буфер данных указывается с помощью *DataPtr* аргумента в **SQLPutData** и *ParameterValuePtr* аргумента в **SQLBindParameter**.
