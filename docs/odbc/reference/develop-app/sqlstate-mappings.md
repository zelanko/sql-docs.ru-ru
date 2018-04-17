---
title: Сопоставления SQLSTATE | Документы Microsoft
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
- compatibility [ODBC], SQLSTATE
- backward compatibility [ODBC], SQLSTATE
- SQLSTATE [ODBC]
ms.assetid: 6e6cabcf-a204-40eb-b77d-8a0c4a5e8524
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 402d5b6c01142334ed38a73b96da9f0eb635f1c3
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sqlstate-mappings"></a>Сопоставления SQLSTATE
В этом разделе рассматриваются значениях SQLSTATE для ODBC 2. *x* и ODBC 3. *x*. Дополнительные сведения о ODBC 3. *x* значения SQLSTATE. в разделе [коды ошибок ODBC приложение A:](../../../odbc/reference/appendixes/appendix-a-odbc-error-codes.md).  
  
 В ODBC 3. *x*HYxxx SQLSTATE возвращаются вместо S1xxx и 42Sxx SQLSTATE возвращаются вместо S00XX. Это было сделано в соответствии со стандартами Open Group и ISO. Во многих случаях сопоставление не один к одному, поскольку стандарты переопределен Интерпретация несколько SQLSTATE.  
  
 Когда ODBC 2. *x* обновить приложение ODBC 3. *x* приложения, приложение должно измениться ожидать ODBC 3. *x* SQLSTATE, а не ODBC 2. *x* SQLSTATE. В следующей таблице перечислены функции ODBC 3. *x* SQLSTATE, каждый ODBC 2. *x* сопоставляется SQLSTATE.  
  
 Если SQL_OV_ODBC2 имеет значение атрибута среды SQL_ATTR_ODBC_VERSION, драйвер отправляет ODBC 2. *x* SQLSTATE, а не ODBC 3. *x* SQLSTATE при **SQLGetDiagField** или **SQLGetDiagRec** вызывается. Можно определить конкретного сопоставления, отмечая ODBC 2*.x* SQLSTATE в столбец 1 следующей таблицы, которая соответствует ODBC 3. *x* SQLSTATE в столбце 2.  
  
|ODBC 2. *x* SQLSTATE|ODBC 3. *x* SQLSTATE|Комментарии|  
|-------------------------|-------------------------|--------------|  
|01S03|01001||  
|01S04|01001||  
|22003|HY019||  
|22008|22007||  
|22005|22018||  
|24000|07005||  
|37000|42000||  
|70100|HY018||  
|S0001|42S01||  
|S0002|42S02||  
|S0011|42S11||  
|S0012|42S12||  
|S0021|42S21||  
|S0022|42S22||  
|S0023|42S23||  
|S1000|HY000||  
|S1001|HY001||  
|S1002|07009|ODBC 2. *x* SQLSTATE S1002 сопоставляется ODBC 3. *x* SQLSTATE 07009, если базовая функция **SQLBindCol**, **SQLColAttribute**, **SQLExtendedFetch**, **SQLFetch** , **SQLFetchScroll**, или **SQLGetData**.|  
|S1003|HY003 И СООБЩЕНИЕМ||  
|S1004|HY004||  
|S1008|HY008||  
|S1009|HY009|Вернуть для недопустимое использование пустого указателя.|  
|S1009|HY024|Вернуть для недопустимым значением атрибута.|  
|S1009|HY092|Возвращается для обновления или удаления данных с помощью вызова **SQLSetPos**, или добавление, обновление или удаление данных с помощью вызова **SQLBulkOperations**, при одновременной работы пользователей доступен только для чтения.|  
|S1010|HY007 HY010|SQLSTATE S1010 сопоставляется SQLSTATE HY007 при **SQLDescribeCol** вызывается до вызова метода **SQLPrepare**, **SQLExecDirect**, или функции каталога для *StatementHandle*. В противном случае SQLSTATE S1010 сопоставляется с параметром SQLSTATE HY010.|  
|S1011|HY011||  
|S1012|HY012||  
|S1090|HY090||  
|S1091|HY091||  
|S1092|HY092||  
|S1093|07009|ODBC 3. *x* SQLSTATE 07009 сопоставляется ODBC 2. *x* S1093 SQLSTATE, если базовая функция **SQLBindParameter** или **SQLDescribeParam**.|  
|S1096|HY096||  
|S1097|HY097||  
|S1098|HY098||  
|S1099|HY099||  
|S1100|HY100||  
|S1101|HY101||  
|S1103|HY103||  
|S1104|HY104||  
|S1105|HY105||  
|S1106|HY106||  
|S1107|HY107||  
|S1108|HY108||  
|S1109|HY109||  
|S1110|HY110||  
|S1111|HY111||  
|S1C00|HYC00||  
|S1T00|HYT00||  
  
> [!NOTE]  
>  ODBC 3. *x* SQLSTATE 07008 сопоставляется ODBC 2. *x* SQLSTATE S1000.
