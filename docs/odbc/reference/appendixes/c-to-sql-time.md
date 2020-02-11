---
title: 'C на SQL: время | Документация Майкрософт'
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
ms.openlocfilehash: c4a3734ff8d9f0cb120e1d33433ee3a301bb59ae
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68019301"
---
# <a name="c-to-sql-time"></a>Преобразование из C в SQL: время
Идентификатор для типа данных time ODBC C:  
  
 SQL_C_TYPE_TIME  
  
 В следующей таблице показаны типы данных ODBC SQL, к которым могут быть преобразованы данные времени C. Описание столбцов и терминов в таблице см. в разделе [Преобразование данных из C в типы данных SQL](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md).  
  
|Идентификатор типа SQL|Тест|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR<br /><br /> SQL_VARCHAR<br /><br /> SQL_LONGVARCHAR|Длина байта столбца >= 8<br /><br /> Длина байта столбца < 8<br /><br /> Значение данных не является допустимым временем|Недоступно<br /><br /> 22001<br /><br /> 22008|  
|SQL_WCHAR<br /><br /> SQL_WVARCHAR<br /><br /> SQL_WLONGVARCHAR|Длина символа столбца >= 8<br /><br /> Длина символа столбца < 8<br /><br /> Значение данных не является допустимым временем|Недоступно<br /><br /> 22001<br /><br /> 22008|  
|SQL_TYPE_TIME|Значение данных является допустимым временем<br /><br /> Значение данных не является допустимым временем|Недоступно<br /><br /> 22007|  
|SQL_TYPE_TIMESTAMP|Значение данных является допустимым временем [a]<br /><br /> Значение данных не является допустимым временем|Недоступно<br /><br /> 22007|  
  
 [a] для даты в метке времени задана текущая дата, а часть метки времени в долях секунды имеет значение 0.  
  
 Сведения о том, какие значения допустимы в структуре SQL_C_TYPE_TIME, см. в разделе [типы данных C](../../../odbc/reference/appendixes/c-data-types.md)ранее в этом приложении.  
  
 Когда данные времени C преобразуются в символьные данные SQL, полученные символьные данные имеют формат "*чч*:*мм*:*СС*".  
  
 Драйвер игнорирует значение длины или индикатора при преобразовании данных из типа данных C и предполагает, что размер буфера данных равен размеру типа данных C. Значение length/индикатора передается в аргументе *StrLen_Or_Ind* в **SQLPutData** и в буфере, указанном аргументом *StrLen_or_IndPtr* в **SQLBindParameter**. Буфер данных указывается с помощью аргумента *датаптр* в **SQLPutData** и аргумента *параметервалуептр* в **SQLBindParameter**.
