---
title: 'C в SQL: Метка времени | Документация Майкрософт'
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: aa75299f4d8e8f15293064d0bf3fb3979fe382d1
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68037706"
---
# <a name="c-to-sql-timestamp"></a>C в SQL: Отметка времени
Идентификатор для типа данных ODBC C timestamp является:  
  
 SQL_C_TYPE_TIMESTAMP  
  
 Следующая таблица показывает ODBC SQL типы данных, к которым могут преобразовываться данных C отметки времени. Описание столбцов и условия в таблице, см. в разделе [преобразование данных из C в типы данных SQL](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md).  
  
|Идентификатор типа SQL|Тест|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR<br /><br /> SQL_VARCHAR<br /><br /> SQL_LONGVARCHAR|Длина столбца в байтах > = байтов символов<br /><br /> 19 < = длина в байтах столбца < символов байт<br /><br /> Столбец байтов длиной < 19<br /><br /> Значение данных не допустимую метку времени|Н/Д<br /><br /> 22001<br /><br /> 22001<br /><br /> 22008|  
|SQL_WCHAR<br /><br /> SQL_WVARCHAR<br /><br /> SQL_WLONGVARCHAR|Длина столбца символ > = символьную длину данных<br /><br /> 19 < = длина столбца символ < символ длину данных<br /><br /> Столбец символов длиной < 19<br /><br /> Значение данных не допустимую метку времени|Н/Д<br /><br /> 22001<br /><br /> 22001<br /><br /> 22008|  
|SQL_TYPE_DATE|Поля времени равны нулю<br /><br /> Поля времени отличны от нуля<br /><br /> Значение данных не содержит допустимую дату|Н/Д<br /><br /> 22008<br /><br /> 22007|  
|SQL_TYPE_TIME|Поля долей секунд равны нулю [a]<br /><br /> Поля долей секунды, ненулевое значение [a]<br /><br /> Значение данных не содержит допустимое время|Н/Д<br /><br /> 22008<br /><br /> 22007|  
|SQL_TYPE_TIMESTAMP|Поля долей секунд не усекаются.<br /><br /> Поля доли секунды усекаются<br /><br /> Значение данных не допустимую метку времени|Н/Д<br /><br /> 22008<br /><br /> 22007|  
  
 [a] Дата полей структуры, метка времени учитываются.  
  
 Сведения о том, какие значения являются допустимыми в структуре SQL_C_TIMESTAMP, см. в разделе [типы данных C](../../../odbc/reference/appendixes/c-data-types.md)ранее в этом приложении.  
  
 При преобразовании в символьные данные SQL данных отметки времени C полученные данные символ находится в "*гггг*-*мм*-*дд* *hh*:*мм*:*ss*[.*f...* ]» формат.  
  
 Драйвер не учитывает значение длины и индикатора, при преобразовании данных из типа данных timestamp C и предполагается, что размер буфера данных размер типа данных timestamp C. Значение длины и индикатора, переданное в *StrLen_or_Ind* аргумента в **SQLPutData** и в указанный буфер с *StrLen_or_IndPtr* аргумента в **SQLBindParameter**. Буфер данных указывается с помощью *DataPtr* аргумента в **SQLPutData** и *ParameterValuePtr* аргумента в **SQLBindParameter**.
