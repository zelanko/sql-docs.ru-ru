---
title: 'C в SQL: метка времени | Документы Microsoft'
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
- data conversions from C to SQL types [ODBC], timestamp
- timestamp data type [ODBC]
- converting data from c to SQL types [ODBC], timestamp
ms.assetid: 0e08bfff-68f9-4648-9558-09b57fea08ad
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bc9202f97100e2b6eb69776d7864c8bafbed20d8
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="c-to-sql-timestamp"></a>C в SQL: отметка времени
Идентификатор для типа данных ODBC C timestamp является:  
  
 SQL_C_TYPE_TIMESTAMP  
  
 Следующая таблица показывает ODBC SQL типы данных, к которым может быть преобразован данных C отметки времени. Объяснение столбцы и условия в таблице см. в разделе [преобразование данных из C в типы данных SQL](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md).  
  
|Идентификатор типа SQL|Тест|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR<br /><br /> SQL_VARCHAR<br /><br /> SQL_LONGVARCHAR|Длина столбца в байтах > = байт символов<br /><br /> 19 < = длина столбца в байтах < символов длина в байтах<br /><br /> Столбец байтов длина < 19<br /><br /> Значение данных не является допустимым отметки времени|н/д<br /><br /> 22001<br /><br /> 22001<br /><br /> 22008|  
|SQL_WCHAR<br /><br /> SQL_WVARCHAR<br /><br /> SQL_WLONGVARCHAR|Длина столбца символ > = длина символов в данных<br /><br /> 19 < = длина столбца символ < длина данных<br /><br /> Длина < 19 символов столбца<br /><br /> Значение данных не является допустимым отметки времени|н/д<br /><br /> 22001<br /><br /> 22001<br /><br /> 22008|  
|SQL_TYPE_DATE|Поля времени равны нулю<br /><br /> Ненулевое значение поля времени<br /><br /> Значение данных не содержит допустимой датой|н/д<br /><br /> 22008<br /><br /> 22007|  
|SQL_TYPE_TIME|Поля долей секунды равны нулю []<br /><br /> Поля долей секунды, ненулевое значение, [a]<br /><br /> Значение данных не содержит допустимое время|н/д<br /><br /> 22008<br /><br /> 22007|  
|SQL_TYPE_TIMESTAMP|Поля долей секунд не усекаются.<br /><br /> Поля долей секунды усекаются<br /><br /> Значение данных не является допустимым отметки времени|н/д<br /><br /> 22008<br /><br /> 22007|  
  
 [a] Дата поля структуры отметки времени учитываются.  
  
 Сведения о какие значения являются допустимыми в структуре SQL_C_TIMESTAMP см. в разделе [типы данных C](../../../odbc/reference/appendixes/c-data-types.md)ранее в этом приложении.  
  
 При преобразовании данных C отметки времени в символьные данные SQL, результирующий символьных данных находится в «*гггг*-*мм*-*дд* *hh*:*мм*:*ss*[.*f...*]» формата.  
  
 Драйвер не учитывает значение длины/индикатора при преобразовании данных из типа данных timestamp C и предполагает, что размер типа данных timestamp C размер буфера данных. Переданное значение длины/индикатора *StrLen_or_Ind* аргумент в **SQLPutData** и в указанный буфер с *StrLen_or_IndPtr* аргумент в **SQLBindParameter**. Буфер данных задается с помощью *DataPtr* аргумент в **SQLPutData** и *ParameterValuePtr* аргумент в **SQLBindParameter**.
