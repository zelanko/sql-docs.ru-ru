---
title: 'C в SQL: бит | Документы Microsoft'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- converting data from c to SQL types [ODBC], bit
- bit data type [ODBC]
- data conversions from C to SQL types [ODBC], bit
ms.assetid: 267c9fa9-599e-4ee6-b51b-0cae43f09183
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a6fc0008d18b5ee758ad6edcbd32246664efacd8
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="c-to-sql-bit"></a>C в SQL: бит
Идентификатор для типа данных bit ODBC C —:  
  
 SQL_C_BIT  
  
 В следующей таблице показаны ODBC SQL типы данных, к которым может быть преобразован бит данных C. Объяснение столбцы и условия в таблице см. в разделе [преобразование данных из C в типы данных SQL](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md).  
  
|Идентификатор типа SQL|Тест|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR SQL_VARCHAR<br /><br /> SQL_LONGVARCHAR<br /><br /> SQL_WCHAR SQL_WVARCHAR<br /><br /> SQL_WLONGVARCHAR|Нет|н/д|  
|SQL_DECIMAL SQL_NUMERIC<br /><br /> SQL_TINYINT SQL_SMALLINT<br /><br /> SQL_INTEGER SQL_BIGINT<br /><br /> SQL_REAL SQL_FLOAT<br /><br /> SQL_DOUBLE|Нет|н/д|  
|SQL_BIT|Нет|н/д|  
  
 Драйвер не учитывает значение длины/индикатора при преобразовании данных из типа данных bit C и предполагает, что размер типа данных bit C размер буфера данных. Переданное значение длины/индикатора *StrLen_or_Ind* аргумент в **SQLPutData** и в указанный буфер с *StrLen_or_IndPtr* аргумент в **SQLBindParameter**. Буфер данных задается с помощью *DataPtr* аргумент в **SQLPutData** и *ParameterValuePtr* аргумент в **SQLBindParameter**.
