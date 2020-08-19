---
description: Использование SQLBindCol
title: Использование SQLBindCol | Документация Майкрософт
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
ms.openlocfilehash: f68aa647f600709dd1a4b989cdab8153775f0aaa
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88421448"
---
# <a name="using-sqlbindcol"></a>Использование SQLBindCol
Приложение привязывает столбцы путем вызова **SQLBindCol**. Эта функция привязывает один столбец за раз. В нем в приложении указано следующее:  
  
-   Номер столбца. Столбец 0 является столбцом закладки; Этот столбец не включен в некоторые результирующие наборы. Все остальные столбцы нумеруются, начиная с номера 1. Не удается привязать столбец с большим числом столбцов, чем в результирующем наборе. эту ошибку невозможно обнаружить до тех пор, пока результирующий набор не будет создан, поэтому он возвращается функцией **SQLFetch**, а не **SQLBindCol**.  
  
-   Тип данных C, адрес и длина байта переменной, привязанной к столбцу. Указание типа данных C, к которому не удается преобразовать тип данных SQL столбца, является ошибкой. Эта ошибка может быть не обнаружена до тех пор, пока результирующий набор не будет создан, поэтому он возвращается функцией **SQLFetch**, а не **SQLBindCol**. Список поддерживаемых преобразований см. в разделе [Преобразование данных из SQL в типы данных C](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md) в приложении г: типы данных. Дополнительные сведения о длине байт см. в разделе [Длина буфера данных](../../../odbc/reference/develop-app/data-buffer-length.md).  
  
-   Адрес буфера длины или индикатора. Буфер длины и индикатора необязателен. Он используется для возврата байтовой длины двоичных или символьных данных или возврата SQL_NULL_DATA, если данные имеют значение NULL. Дополнительные сведения см. [в разделе Использование значений длины и индикатора](../../../odbc/reference/develop-app/using-length-and-indicator-values.md).  
  
 При вызове **SQLBindCol** драйвер связывает эти сведения с инструкцией. При выборке каждой строки данных она использует эти сведения для размещения данных для каждого столбца в привязанных переменных приложения.  
  
 Например, следующий код привязывает переменные к столбцам SalesPerson и CustID. Данные для столбцов будут возвращены в *SalesPerson* и *CustID*. Поскольку *Продавец* является символьным буфером, приложение указывает его длину в байтах (11), чтобы драйвер мог определить, следует ли усекать данные. Длина байта возвращаемого заголовка или значение NULL, будет возвращено в *салесперсонленоринд*.  
  
 Поскольку *CustID* является целочисленной переменной и имеет фиксированную длину, нет необходимости указывать ее длину в байтах. драйвер предполагает, что он имеет значение **sizeof (** SQLUINTEGER **)**. Длина байта возвращенных данных идентификатора клиента или значение NULL будет возвращено в *кустидинд*. Обратите внимание, что приложение заинтересовано только в том случае, если оклад имеет значение NULL, поскольку длина байта всегда равна **sizeof (** SQLUINTEGER **)**.  
  
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
  
 Следующий код выполняет инструкцию **SELECT** , указанную пользователем, и выводит каждую строку данных в результирующем наборе. Поскольку приложение не может предсказать форму результирующего набора, созданного инструкцией **SELECT** , она не может привязывать жестко запрограммированные переменные к результирующему набору, как в предыдущем примере. Вместо этого приложение выделяет буфер, содержащий данные, и буфер длины и индикатора для каждого столбца в этой строке. Для каждого столбца вычисляется смещение до начала памяти для столбца и корректирует это смещение таким образом, чтобы данные и буферы показателей и длины для столбца начинались с границ выравнивания. Затем он связывает память, начиная с смещения со столбцом. С точки зрения драйвера адрес этой памяти не различается по адресу переменной, привязанной в предыдущем примере. Дополнительные сведения о выравнивании см. в разделе [Выравнивание](../../../odbc/reference/develop-app/alignment.md).  
  
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
