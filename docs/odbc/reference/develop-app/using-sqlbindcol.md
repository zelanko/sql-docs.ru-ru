---
title: С помощью S'LBindCol Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- result sets [ODBC], binding columns
- binding columns [ODBC]
- SQLBindCol function [ODBC], using
ms.assetid: 17277ab3-33ad-44d3-a81c-a26b5e338512
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: da49ad4db80b93d02534a0c4ecacdc2621c9cf8d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81294634"
---
# <a name="using-sqlbindcol"></a>Использование SQLBindCol
Приложение связывает столбцы, позвонив по **s'LBindCol**. Эта функция связывает один столбец за один раз. С его помощью приложение определяет следующее:  
  
-   Номер столбца. Колонка 0 — колонка закладок; этот столбец не включен в некоторые наборы результатов. Все остальные столбцы пронумероированы, начиная с числа 1. Это ошибка, связывающая столбец с более высоким числом, чем столбцы в наборе результатов; эта ошибка не может быть обнаружена до тех пор, пока не будет создан набор результатов, поэтому он будет возвращен **S'LFetch,** а не **S'LBindCol.**  
  
-   Тип данных C, адрес и длина байт переменной, привязанной к столбцу. Это ошибка, чтобы указать тип данных C, к которому тип данных S'L не может быть преобразован; эта ошибка не может быть обнаружена до тех пор, пока не будет создан набор результатов, поэтому она будет возвращена **S'LFetch,** а не **S'LBindCol.** Список поддерживаемых конверсий [можно](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md) узнать в приложении D: Типы данных. Для получения информации о [Data Buffer Length](../../../odbc/reference/develop-app/data-buffer-length.md)длине байта см.  
  
-   Адрес буфера длины/индикатора. Буфер длины/индикатора не является обязательным. Он используется для возврата длины байт двоичных или символов данных или возврата SQL_NULL_DATA, если данные являются NULL. Для получения дополнительной [информации см.](../../../odbc/reference/develop-app/using-length-and-indicator-values.md)  
  
 При вызове **S'LBindCol** драйвер связывает эту информацию с заявлением. При извлечении каждой строки данных она использует информацию для размещения данных для каждого столбца в переменных связанного приложения.  
  
 Например, следующий код связывает переменные с столбцыsales SalesPerson и CustID. Данные для столбцов будут возвращены в *SalesPerson* и *CustID*. Поскольку *SalesPerson* является буфером символов, приложение определяет его длину байта (11), чтобы водитель мог определить, следует ли усеивать данные. Длина байта возвращенного заголовка, или же она NULL, будет возвращена в *SalesPersonLenInd*.  
  
 Поскольку *CustID* является равной переменной и имеет фиксированную длину, нет необходимости указывать его длину байта; водитель предполагает, что это размер (S'LUINTEGER **)**. **sizeof(** Длина байт возвращенных данных идентификатора клиента, или же это NULL, будет возвращена в *CustIDInd*. Обратите внимание, что приложение заинтересовано только в том, является ли зарплата NULL, потому что длина байт всегда **sizeof**(S'LUINTEGER **)**.  
  
```  
SQLCHAR       SalesPerson[11];  
SQLUINTEGER   CustID;  
SQLINTEGER    SalesPersonLenOrInd, CustIDInd;  
SQLRETURN     rc;  
SQLHSTMT      hstmt;  
  
// Bind SalesPerson to the SalesPerson column and CustID to the   
// CustID column.  
SQLBindCol(hstmt, 1, SQL_C_CHAR, SalesPerson, sizeof(SalesPerson),  
            &SalesPersonLenOrInd);  
SQLBindCol(hstmt, 2, SQL_C_ULONG, &CustID, 0, &CustIDInd);  
  
// Execute a statement to get the sales person/customer of all orders.  
SQLExecDirect(hstmt, "SELECT SalesPerson, CustID FROM Orders ORDER BY SalesPerson",  
               SQL_NTS);  
  
// Fetch and print the data. Print "NULL" if the data is NULL. Code to   
// check if rc equals SQL_ERROR or SQL_SUCCESS_WITH_INFO not shown.  
while ((rc = SQLFetch(hstmt)) != SQL_NO_DATA) {  
   if (SalesPersonLenOrInd == SQL_NULL_DATA)   
            printf("NULL                     ");  
   else   
            printf("%10s   ", SalesPerson);  
   if (CustIDInd == SQL_NULL_DATA)   
         printf("NULL\n");  
   else   
            printf("%d\n", CustID);  
}  
  
// Close the cursor.  
SQLCloseCursor(hstmt);  
```  
  
 Следующий код выполняет заявление **SELECT,** ввеченное пользователем, и печатает каждую строку данных в наборе результатов. Поскольку приложение не может предсказать форму набора результатов, созданного заявлением **SELECT,** оно не может связывать жестко закодированные переменные с набором результатов, как в предыдущем примере. Вместо этого приложение выделяет буфер, вмещающие данные, и буфер длины/индикатора для каждого столбца в этой строке. Для каждого столбца он вычисляет смещение до начала памяти для столбца и регулирует это смещение таким образом, чтобы буферы данных и длины/индикатора для столбца начинались на границах выравнивания. Затем он связывает память, начиная с смещения с столбцом. С точки зрения драйвера, адрес этой памяти неотличим от адреса переменной, связанной в предыдущем примере. Для получения дополнительной информации о выравнивании [см.](../../../odbc/reference/develop-app/alignment.md)  
  
```  
// This application allocates a buffer at run time. For each column, this   
// buffer contains memory for the column's data and length/indicator.   
// For example:  
//      column 1         column 2      column 3      column 4  
// <------------><---------------><-----><------------>  
//      db1   li1   db2   li2   db3   li3   db4   li4  
//      |      |      |      |      |      |      |         |  
//      _____V_____V________V_______V___V___V______V_____V_  
// |__________|__|_____________|__|___|__|__________|__|  
//  
// dbn = data buffer for column n  
// lin = length/indicator buffer for column n  
  
// Define a macro to increase the size of a buffer so that it is a   
// multiple of the alignment size. Thus, if a buffer starts on an   
// alignment boundary, it will end just before the next alignment   
// boundary. In this example, an alignment size of 4 is used because   
// this is the size of the largest data type used in the application's   
// buffer--the size of an SDWORD and of the largest default C data type   
// are both 4. If a larger data type (such as _int64) was used, it would   
// be necessary to align for that size.  
#define ALIGNSIZE 4  
#define ALIGNBUF(Length) Length % ALIGNSIZE ? \  
                  Length + ALIGNSIZE - (Length % ALIGNSIZE) : Length  
  
SQLCHAR        SelectStmt[100];  
SQLSMALLINT    NumCols, *CTypeArray, i;  
SQLINTEGER *   ColLenArray, *OffsetArray, SQLType, *DataPtr;  
SQLRETURN      rc;   
SQLHSTMT       hstmt;  
  
// Get a SELECT statement from the user and execute it.  
GetSelectStmt(SelectStmt, 100);  
SQLExecDirect(hstmt, SelectStmt, SQL_NTS);  
  
// Determine the number of result set columns. Allocate arrays to hold   
// the C type, byte length, and buffer offset to the data.  
SQLNumResultCols(hstmt, &NumCols);  
CTypeArray = (SQLSMALLINT *) malloc(NumCols * sizeof(SQLSMALLINT));  
ColLenArray = (SQLINTEGER *) malloc(NumCols * sizeof(SQLINTEGER));  
OffsetArray = (SQLINTEGER *) malloc(NumCols * sizeof(SQLINTEGER));  
  
OffsetArray[0] = 0;  
for (i = 0; i < NumCols; i++) {  
   // Determine the column's SQL type. GetDefaultCType contains a switch   
   // statement that returns the default C type for each SQL type.  
   SQLColAttribute(hstmt, ((SQLUSMALLINT) i) + 1, SQL_DESC_TYPE, NULL, 0, NULL, (SQLPOINTER) &SQLType);  
   CTypeArray[i] = GetDefaultCType(SQLType);  
  
   // Determine the column's byte length. Calculate the offset in the   
   // buffer to the data as the offset to the previous column, plus the   
   // byte length of the previous column, plus the byte length of the   
   // previous column's length/indicator buffer. Note that the byte   
   // length of the column and the length/indicator buffer are increased   
   // so that, assuming they start on an alignment boundary, they will  
   // end on the byte before the next alignment boundary. Although this   
   // might leave some holes in the buffer, it is a relatively   
   // inexpensive way to guarantee alignment.  
   SQLColAttribute(hstmt, ((SQLUSMALLINT) i)+1, SQL_DESC_OCTET_LENGTH, NULL, 0, NULL, &ColLenArray[i]);  
   ColLenArray[i] = ALIGNBUF(ColLenArray[i]);  
   if (i)  
      OffsetArray[i] = OffsetArray[i-1]+ColLenArray[i-1]+ALIGNBUF(sizeof(SQLINTEGER));  
}  
  
// Allocate the data buffer. The size of the buffer is equal to the   
// offset to the data buffer for the final column, plus the byte length   
// of the data buffer and length/indicator buffer for the last column.  
void *DataPtr = malloc(OffsetArray[NumCols - 1] +  
               ColLenArray[NumCols - 1] + ALIGNBUF(sizeof(SQLINTEGER)));  
  
// For each column, bind the address in the buffer at the start of the   
// memory allocated for that column's data and the address at the start   
// of the memory allocated for that column's length/indicator buffer.  
for (i = 0; i < NumCols; i++)  
   SQLBindCol(hstmt,  
            ((SQLUSMALLINT) i) + 1,  
            CTypeArray[i],  
            (SQLPOINTER)((SQLCHAR *)DataPtr + OffsetArray[i]),  
            ColLenArray[i],  
            (SQLINTEGER *)((SQLCHAR *)DataPtr + OffsetArray[i] + ColLenArray[i]));  
  
// Retrieve and print each row. PrintData accepts a pointer to the data,   
// its C type, and its byte length/indicator. It contains a switch   
// statement that casts and prints the data according to its type. Code   
// to check if rc equals SQL_ERROR or SQL_SUCCESS_WITH_INFO not shown.  
while ((rc = SQLFetch(hstmt)) != SQL_NO_DATA) {  
   for (i = 0; i < NumCols; i++) {  
      PrintData((SQLCHAR *)DataPtr[OffsetArray[i]], CTypeArray[i],  
               (SQLINTEGER *)((SQLCHAR *)DataPtr[OffsetArray[i] + ColLenArray[i]]));  
   }  
}  
  
// Close the cursor.  
SQLCloseCursor(hstmt);  
```
