---
title: Сопоставления SQLSTATE | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- compatibility [ODBC], SQLSTATE
- backward compatibility [ODBC], SQLSTATE
- SQLSTATE [ODBC]
ms.assetid: 6e6cabcf-a204-40eb-b77d-8a0c4a5e8524
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 89be9c958cb848384a67e7eaf74cfecc72f07c35
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63148884"
---
# <a name="sqlstate-mappings"></a>Сопоставления SQLSTATE
В этом разделе рассматриваются значениях SQLSTATE для ODBC 2. *x* и ODBC 3. *x*. Дополнительные сведения о ODBC 3. *x* значения SQLSTATE, см. в разделе [приложении a. Коды ошибок ODBC](../../../odbc/reference/appendixes/appendix-a-odbc-error-codes.md).  
  
 В ODBC 3. *x*HYxxx SQLSTATE возвращаются вместо S1xxx и SQLSTATE 42Sxx возвращаются вместо S00XX. Это было сделано в соответствии со стандартами Open Group и ISO. Во многих случаях сопоставление не один к одному, так как стандарты переопределен интерпретацию несколько SQLSTATE.  
  
 Когда ODBC 2. *x* обновлении приложения до ODBC 3. *x* приложение, приложение должно изменить ожидать ODBC 3. *x* SQLSTATE, а не ODBC 2. *x* SQLSTATE. В следующей таблице перечислены ODBC 3. *x* SQLSTATE, каждый ODBC 2. *x* сопоставляется с кодом SQLSTATE.  
  
 Если атрибуту окружения SQL_ATTR_ODBC_VERSION присвоено SQL_OV_ODBC2, драйвер учитывает ODBC 2. *x* SQLSTATE, а не ODBC 3. *x* SQLSTATE при **SQLGetDiagField** или **SQLGetDiagRec** вызывается. Конкретного сопоставления можно определить с помощью отметить ODBC 2 *.x* SQLSTATE, в столбце 1 в следующей таблице, соответствующий ODBC 3. *x* SQLSTATE в столбце 2.  
  
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
|S1002|07009|ODBC 2. *x* SQLSTATE S1002 сопоставляется с ODBC 3. *x* SQLSTATE 07009 при базовой функции **SQLBindCol**, **SQLColAttribute**, **SQLExtendedFetch**, **SQLFetch** , **SQLFetchScroll**, или **SQLGetData**.|  
|S1003|HY003||  
|S1004|HY004||  
|S1008|HY008||  
|S1009|HY009|Возвращается для недопустимое использование пустого указателя.|  
|S1009|HY024|Возвращается для недопустимым значением атрибута.|  
|S1009|HY092|Возвращается для обновления или удаления данных с помощью вызова **SQLSetPos**, или добавление, обновление или удаление данных с помощью вызова **SQLBulkOperations**, когда уровень параллелизма только для чтения.|  
|S1010|HY007 HY010|SQLSTATE S1010 сопоставляется с кодом SQLSTATE HY007 при **SQLDescribeCol** вызывается до вызова метода **SQLPrepare**, **SQLExecDirect**, или функции каталога для *StatementHandle*. В противном случае SQLSTATE S1010 сопоставляется с параметром SQLSTATE HY010.|  
|S1011|HY011||  
|S1012|HY012||  
|S1090|HY090||  
|S1091|HY091||  
|S1092|HY092||  
|S1093|07009|ODBC 3. *x* SQLSTATE 07009 сопоставляется с ODBC 2. *x* S1093 SQLSTATE, если функция базового **SQLBindParameter** или **SQLDescribeParam**.|  
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
>  ODBC 3. *x* SQLSTATE 07008 сопоставляется с ODBC 2. *x* SQLSTATE S1000.
