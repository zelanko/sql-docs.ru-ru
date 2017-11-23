---
title: "С помощью SQLBindCol | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- result sets [ODBC], binding columns
- binding columns [ODBC]
- SQLBindCol function [ODBC], using
ms.assetid: 17277ab3-33ad-44d3-a81c-a26b5e338512
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6e0cc3b7bde32302ed16a20a8b1c0ccbc985584a
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="using-sqlbindcol"></a>С помощью SQLBindCol
Приложение выполняет привязку столбцов путем вызова **SQLBindCol**. Эта функция привязывает один столбец за раз. С его помощью приложение указывает следующее:  
  
-   Номер столбца. 0 является столбец закладки; Этот столбец не включен в несколько результирующих наборов. Все остальные столбцы нумеруются, начиная с номера 1. Это ошибка, чтобы привязать столбец большим номером, чем число столбцов в результирующем наборе; Эта ошибка не удается обнаружить, пока не будет создан результирующий набор, поэтому он возвращается в виде **SQLFetch**, а не **SQLBindCol**.  
  
-   C тип, адрес и байтов длина данных переменной, привязанное к столбцу. Это ошибка, чтобы указать тип данных C, к которому не удается преобразовать тип данных SQL столбца; Эта ошибка может быть незамечен пока создан результирующий набор, он возвращается в виде **SQLFetch**, а не **SQLBindCol**. Список поддерживаемых преобразований см. в разделе [преобразование данных из SQL в типы данных C](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md) в типах данных приложение D:. Сведения о байтовая длина разделе [длина буфера данных](../../../odbc/reference/develop-app/data-buffer-length.md).  
  
-   Адрес буфера длины и индикатора. Буфер длины/индикатора является необязательным. Он используется для возврата числа двоичных или символьных данных или возвращаемого значения SQL_NULL_DATA байт, если данные имеют значение NULL. Дополнительные сведения см. в разделе [использование значения длины/индикатора](../../../odbc/reference/develop-app/using-length-and-indicator-values.md).  
  
 Когда **SQLBindCol** является именем, драйвер связывает эти сведения с помощью инструкции. Когда извлекается каждой строки данных, он использует данные для перемещения данных для каждого столбца в связанные переменные приложений.  
  
 Например следующий код связывает столбцы «менеджер по продажам» и «CustID переменных. Будут возвращены данные для столбцов в *менеджеров по продажам* и *CustID*. Поскольку *менеджеров по продажам* является буфером символов приложение задает его длина в байтах (11), чтобы драйвер мог определить, следует ли усекать данные. Байтовая длина полученного заголовка или является ли NULL, будут возвращены в *SalesPersonLenOrInd*.  
  
 Поскольку *CustID* — целочисленная переменная и фиксированную длину, нет необходимости указывать его длина в байтах; драйвер предполагает это **sizeof (**SQLUINTEGER**)**. Байт, возвращенных клиента идентификатор данных или является ли NULL, будут возвращены в *CustIDInd*. Обратите внимание, что приложение интересует только ли Зарплата имеет значение NULL, так как байтовая длина всегда **sizeof (**SQLUINTEGER**)**.  
  
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
  
 В следующем коде выполняется **ВЫБЕРИТЕ** инструкции, введенные пользователем и выводит каждой строки данных в результирующем наборе. Поскольку приложение не может предсказать форму результата установить созданные **ВЫБЕРИТЕ** инструкции, его невозможно привязать жестко переменные в результирующий набор, как показано в предыдущем примере. Вместо этого приложение выделяет буфер, содержащий данные и буфер длины/индикатора для каждого столбца в этой строке. Для каждого столбца она вычисляет смещение для начала памяти для столбца и корректирует смещения, таким образом, чтобы запустить буферов данных и длины/индикатора для столбца на границы выравнивания. Затем он привязывает памяти, начиная со смещения в столбец. С точки зрения драйвера адрес этой памяти не отличается от адреса переменной, привязанного в предыдущем примере. Дополнительные сведения о выравнивании см. в разделе [выравнивание](../../../odbc/reference/develop-app/alignment.md).  
  
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
