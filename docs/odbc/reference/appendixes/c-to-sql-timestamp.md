---
description: 'Преобразование из C в SQL: отметки времени'
title: 'C в SQL: timestamp | Документация Майкрософт'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data conversions from C to SQL types [ODBC], timestamp
- timestamp data type [ODBC]
- converting data from c to SQL types [ODBC], timestamp
ms.assetid: 0e08bfff-68f9-4648-9558-09b57fea08ad
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e51d82e8acd59c8b4e6f5a8385720b0bd38eba4c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88449036"
---
# <a name="c-to-sql-timestamp"></a>Преобразование из C в SQL: отметки времени
Идентификатором для типа данных ODBC C timestamp является:  
  
 SQL_C_TYPE_TIMESTAMP  
  
 В следующей таблице показаны типы данных ODBC SQL, к которым могут быть преобразованы данные timestamp C. Описание столбцов и терминов в таблице см. в разделе [Преобразование данных из C в типы данных SQL](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md).  
  
|Идентификатор типа SQL|Тест|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR<br /><br /> SQL_VARCHAR<br /><br /> SQL_LONGVARCHAR|Длина байта столбца >= Длина байтового символа<br /><br /> 19 <= длина байта столбца < длина байтовой кодировки<br /><br /> Длина байта столбца < 19<br /><br /> Значение данных не является допустимой меткой времени|Недоступно<br /><br /> 22001<br /><br /> 22001<br /><br /> 22008|  
|SQL_WCHAR<br /><br /> SQL_WVARCHAR<br /><br /> SQL_WLONGVARCHAR|Длина символа столбца >= символьная длина данных<br /><br /> 19 <= длина символов столбца < длина данных<br /><br /> Длина символа столбца < 19<br /><br /> Значение данных не является допустимой меткой времени|Недоступно<br /><br /> 22001<br /><br /> 22001<br /><br /> 22008|  
|SQL_TYPE_DATE|Поля времени равны нулю<br /><br /> Поля времени не равны нулю<br /><br /> Значение данных не содержит допустимой даты|Недоступно<br /><br /> 22008<br /><br /> 22007|  
|SQL_TYPE_TIME|Поля долей секунды равны нулю [a]<br /><br /> Поля долей секунды не равны нулю [a]<br /><br /> Значение данных не содержит допустимое время|Недоступно<br /><br /> 22008<br /><br /> 22007|  
|SQL_TYPE_TIMESTAMP|Поля долей секунды не усекаются<br /><br /> Поля долей секунды усекаются<br /><br /> Значение данных не является допустимой меткой времени|Недоступно<br /><br /> 22008<br /><br /> 22007|  
  
 [a] поля даты структуры отметок времени игнорируются.  
  
 Сведения о том, какие значения допустимы в структуре SQL_C_TIMESTAMP, см. в разделе [типы данных C](../../../odbc/reference/appendixes/c-data-types.md)ранее в этом приложении.  
  
 Когда данные timestamp C преобразуются в символьные данные SQL, полученные символьные данные находятся в формате "*гггг* - *мм* - *дд* *чч*:*мм*:*СС*[.* f...*] " формат.  
  
 Драйвер игнорирует значение длины или индикатора при преобразовании данных из типа данных timestamp C и предполагает, что размер буфера данных равен размеру типа данных timestamp C. Значение length/индикатора передается в аргументе *StrLen_Or_Ind* в **SQLPutData** и в буфере, указанном аргументом *StrLen_or_IndPtr* в **SQLBindParameter**. Буфер данных указывается с помощью аргумента *датаптр* в **SQLPutData** и аргумента *параметервалуептр* в **SQLBindParameter**.
