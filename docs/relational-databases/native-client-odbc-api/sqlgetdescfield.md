---
title: СЗЛГетДескФилд Документы Майкрософт
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLGetDescField function
ms.assetid: 3e59a37a-28ee-4c91-8968-7fe3b966739d
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 341a9fe5c5919093853b0c62c7148515380a0551
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299584"
---
# <a name="sqlgetdescfield"></a>SQLGetDescField
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Драйвер [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC предоставляет поля дескриптора драйвера для дескриптора реализации (IRD) только для дескриптора строки реализации. В IRD [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поля дескриптора ссылаются через атрибуты столбца для драйверов. Для получения информации о полном списке доступных [SQLColAttribute](../../relational-databases/native-client-odbc-api/sqlcolattribute.md)полей дескриптора драйвера, см.  
  
 Поля дескриптора, содержащие строки идентификатора столбца, часто являются строками нулевой длины. Все специфические для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] значения поля дескриптора доступны только для чтения.  
  
 Например, атрибуты, полученные с помощью S'LColAttribute, полей дескриптора, которые сообщают о атрибутах уровня строки (например, SQL_CA_SS_COMPUTE_ID) регистрируются для всех столбцов в наборе результатов.  
  
## <a name="sqlgetdescfield-and-table-valued-parameters"></a>Функция SQLGetDescField и возвращающие табличные значения параметры  
 Для получения значений расширенных атрибутов параметров и столовых столбцов можно использовать значение для расширенных атрибутов параметров, ценных на таблицу. Для получения дополнительной информации о параметрах, ценных на стол, с [&#41;&#40;м. ](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)  
  
## <a name="sqlgetdescfield-support-for-enhanced-date-and-time-features"></a>Поддержка функции SQLGetDescField для усовершенствованных функций даты-времени  
 Для получения информации о полях дескриптора, доступных с новыми типами даты/времени, [см.](../../relational-databases/native-client-odbc-date-time/metadata-parameter-and-result.md)  
  
 Для получения дополнительной информации см [&#41;&#40;. ](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md)  
  
 Начиная [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]с , S'LGetDescField может вернуть **SQL_C_SS_TIME2** (для типов **времени)** или **SQL_C_SS_TIMESTAMPOFFSET** (для **timetimeoffset)** вместо **SQL_C_BINARY,** если ваше приложение использует ODBC 3.8.  
  
## <a name="sqlgetdescfield-support-for-large-clr-udts"></a>Поддержка функции SQLGetDescField для больших определяемых пользователем типов данных CLR  
 **S'LGetDescField** поддерживает большие типы, определяемые пользователями CLR (UDT). Для получения дополнительной информации смотрите [большие типы, определяемые пользователями CLR, &#40;&#41;ODBC. ](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md)  
  
## <a name="sqlgetdescfield-support-for-sparse-columns"></a>Поддержка функции SQLGetDescField Support для разреженных столбцов  
 Для запроса нового поля IRD можно использовать SQL_CA_SS_IS_COLUMN_SET, чтобы определить, является ли столбец **column_set** столбец.  
  
 Для получения дополнительной информации см. [Sparse колонки поддержка &#40;ODBC&#41;](../../relational-databases/native-client/odbc/sparse-columns-support-odbc.md).  
  
## <a name="example"></a>Пример  
  
```  
typedef struct tagCOMPUTEBYLIST  
    {  
    SQLSMALLINT nBys;  
    SQLSMALLINT aByList[1];  
    } COMPUTEBYLIST;  
typedef COMPUTEBYLIST* PCOMPUTEBYLIST;   
  
SQLHDESC    hIRD;   
SQLINTEGER  cbIRD;   
SQLINTEGER  nSet = 0;   
  
// . . .  
// Execute a statement that contains a COMPUTE clause,  
//  then get the descriptor handle of the IRD and  
//  get some IRD values.  
  
SQLGetStmtAttr(g_hStmt, SQL_ATTR_IMP_ROW_DESC,  
    (SQLPOINTER) &hIRD, sizeof(SQLHDESC), &cbIRD);  
  
// For statement-wide column attributes, any  
//  descriptor record will do. You know that 1 exists,  
//  so use it.  
SQLGetDescField(hIRD, 1, SQL_CA_SS_NUM_COMPUTES,  
    (SQLPOINTER) &nComputes, SQL_IS_INTEGER, &cbIRD);  
  
if (nSet == 0)  
    {  
    SQLINTEGER      nOrderID;  
  
    printf_s("Normal result set.\n");  
  
    for (nCol = 0; nCol < nCols; nCol++)  
        {  
        SQLGetDescField(hIRD, nCol+1,  
            SQL_CA_SS_COLUMN_ORDER,  
            (SQLPOINTER) &nOrderID, SQL_IS_INTEGER,  
            &cbIRD);  
  
        if (nOrderID != 0)  
            {  
            printf_s("Col in ORDER BY, pos: %ld",  
                nOrderID);  
            }  
            printf_s("\n");  
        }  
  
    printf_s("\n");  
    }  
else  
    {  
    PCOMPUTEBYLIST  pByList;  
    SQLSMALLINT     nBy;  
    SQLINTEGER      nColID;  
  
    printf_s("Computed result set number: %lu\n",  
        nSet);  
  
    SQLGetDescField(hIRD, 1, SQL_CA_SS_COMPUTE_BYLIST,  
        (SQLPOINTER) &pByList, SQL_IS_INTEGER,  
        &cbIRD);  
  
    if (pByList != NULL)  
        {  
        printf_s("Clause ordered by columns: ");  
        for (nBy = 0; nBy < pByList->nBys; )  
            {  
            printf_s("%u", pByList->aByList[nBy]);  
            nBy++;  
  
            if (nBy == pByList->nBys)  
                {  
                printf_s("\n");  
                }  
            else  
                {  
                printf_s(", ");  
                }  
            }  
        }  
    else  
        {  
        printf_s("Compute clause set not ordered.\n");  
        }  
  
    for (nCol = 0; nCol < nCols; nCol++)  
        {  
        SQLGetDescField(hIRD, nCol+1,  
            SQL_CA_SS_COLUMN_ID, (SQLPOINTER) &nColID,  
            SQL_IS_INTEGER, &cbIRD);  
        printf_s("ColumnID: %lu, nColID);  
        }  
    printf_s("\n");  
    }  
  
if (SQLMoreResults(g_hStmt) == SQL_SUCCESS)  
    {  
    // Determine the result set indicator.  
    SQLGetDescField(hIRD, 1, SQL_CA_SS_COMPUTE_ID,  
        (SQLPOINTER) &nSet, SQL_IS_INTEGER, &cbIRD);  
    }  
```  
  
## <a name="see-also"></a>См. также:  
 [Функция S'LGetDescfield](https://go.microsoft.com/fwlink/?LinkId=59351)   
 [ODBC API Implementation Details](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
