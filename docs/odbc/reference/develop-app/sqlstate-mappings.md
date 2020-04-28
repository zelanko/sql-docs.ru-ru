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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ec58c0e41869529bbba5fd31ad534976923a990d
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299744"
---
# <a name="sqlstate-mappings"></a>Сопоставления SQLSTATE
В этом разделе обсуждаются значения SQLSTATE для ODBC *2. x* и ODBC *3. x*. Дополнительные сведения о значениях SQLSTATE ODBC *3. x* см. в [приложении A: коды ошибок ODBC](../../../odbc/reference/appendixes/appendix-a-odbc-error-codes.md).  
  
 В ODBC *3. x*хикскскс SQLSTATE возвращаются вместо S1xxx, а 42Sxx SQLSTATE возвращается вместо S00XX. Это было сделано для согласования с открытыми стандартами групп и ISO. Во многих случаях сопоставление не является "один к одному", так как стандарты переопределяют интерпретацию нескольких SQLSTATE.  
  
 При обновлении приложения ODBC *2. x* до приложения ODBC *3. x* приложение должно быть изменено на ожидание ODBC *3. x* SQLSTATE вместо ODBC *2. x* SQLSTATE. В следующей таблице перечислены SQLSTATE ODBC *3. x* , с которыми сопоставлены все ODBC *2. x* SQLSTATE.  
  
 Если для атрибута среды SQL_ATTR_ODBC_VERSION задано значение SQL_OV_ODBC2, драйвер будет публиковать ODBC *2. x* SQLSTATE вместо ODBC *3. x* SQLSTATE при вызове **SQLGetDiagField** или **SQLGetDiagRec** . Определенное сопоставление можно определить, отметив ODBC *2. x* SQLSTATE в столбце 1 следующей таблицы, которая соответствует ODBC *3. x* SQLSTATE в столбце 2.  
  
|ODBC *2. x* SQLSTATE|ODBC *3. x* SQLSTATE|Комментарии|  
|-------------------------|-------------------------|--------------|  
|01S03|01001||  
|01S04|01001||  
|22003|HY019||  
|22008|22007||  
|22005|22018||  
|24 000|07005||  
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
|S1002|07009|ODBC *2. x* SQLSTATE S1002 сопоставляется с ODBC *3. x* SQLSTATE 07009, если базовая функция — **SQLBindCol**, **SQLColAttribute**, **SQLExtendedFetch**, **SQLFetch**, **SQLFetchScroll**или **SQLGetData**.|  
|S1003|HY003||  
|S1004|HY004||  
|S1008|HY008||  
|S1009|HY009|Возвращается для недопустимого использования пустого указателя.|  
|S1009|HY024|Возвращено для недопустимого значения атрибута.|  
|S1009|HY092|Возвращается для обновления или удаления данных путем вызова функции **SQLSetPos**, добавления, обновления или удаления данных с помощью вызова **SQLBulkOperations**, если параллелизм доступен только для чтения.|  
|S1010|HY007 HY010|Значение SQLSTATE S1010 сопоставляется с SQLSTATE HY007, когда **SQLDescribeCol** вызывается до вызова **SQLPrepare**, **SQLExecDirect**или функции каталога для *статеменсандле*. В противном случае S1010 SQLSTATE сопоставляется с SQLSTATE HY010.|  
|S1011|HY011||  
|S1012|HY012||  
|S1090|HY090||  
|S1091|HY091||  
|S1092|HY092||  
|S1093|07009|ODBC *3. x* SQLSTATE 07009 СОПОСТАВЛЕН с ODBC *2. x* SQLSTATE S1093, если базовая функция — **SQLBindParameter** или **SQLDescribeParam**.|  
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
>  ODBC *3. x* SQLSTATE 07008 СОПОСТАВЛЕН с ODBC *2. x* SQLSTATE S1000.
