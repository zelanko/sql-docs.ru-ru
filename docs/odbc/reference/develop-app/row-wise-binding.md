---
title: Привязка на уровне строки | Документы Microsoft
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
ms.topic: conceptual
helpviewer_keywords:
- row-wise binding [ODBC]
- result sets [ODBC], binding columns
- binding columns [ODBC]
ms.assetid: 4f622cf4-0603-47a1-a48b-944c4ef46364
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 61839fe1cad32bc9daf0acdc1bb43a2d793bf5b1
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="row-wise-binding"></a>Привязка на уровне строки
Если используется привязка на уровне строки, приложение определяет структуру, содержащую один или два, или в некоторых случаях трех элементов для каждого столбца, для которого требуется возвращаемых данных. Первый элемент содержит значение данных, а второй элемент содержит буфер длины/индикатора. Индикаторы и значения длины могут храниться в отдельных буферов, задав поля дескриптора SQL_DESC_INDICATOR_PTR и SQL_DESC_OCTET_LENGTH_PTR в разные значения; Если это сделать, эта структура содержит третьего элемента. Затем приложение выделяет массив эти структуры, который содержит число элементов, как строк в наборе строк.  
  
 Приложение объявляет размер структуры драйвера с атрибутом SQL_ATTR_ROW_BIND_TYPE инструкции и связывает адрес каждого элемента в первом элементе массива. Таким образом драйвер может вычислить адрес данных для конкретной строки и столбца в виде  
  
```  
Address = Bound Address + ((Row Number - 1) * Structure Size)  
```  
  
 где строки пронумерованы от 1 до размера набора строк. (Один вычитается из номер строки, так как в языке C индексации массива начинается с нуля.) Ниже показано, как на уровне строки работает привязки. Как правило в структуре включаются только те столбцы, которые будут действовать. Структура может содержать поля, не связанными с последующим набора столбцов. Столбцы могут размещаться в структуре в любом порядке, но отображаются в последовательном порядке для ясности.  
  
 ![Отображает строку&#45;статистику привязки](../../../odbc/reference/develop-app/media/pr22.gif "pr22")  
  
 Например следующий код создает структуру элементов, в которой возвращаются данные для столбцов OrderID, менеджер по продажам и состояния и длины/индикаторы столбцов менеджеров по продажам и состояние. Он выделяет 10 из этих структур и связывает их со столбцами OrderID, менеджер по продажам и состояние.  
  
```  
#define ROW_ARRAY_SIZE 10  
  
// Define the ORDERINFO struct and allocate an array of 10 structs.  
typedef struct {  
   SQLUINTEGER   OrderID;  
   SQLINTEGER    OrderIDInd;  
   SQLCHAR       SalesPerson[11];  
   SQLINTEGER    SalesPersonLenOrInd;  
   SQLCHAR       Status[7];  
   SQLINTEGER    StatusLenOrInd;  
} ORDERINFO;  
ORDERINFO OrderInfoArray[ROW_ARRAY_SIZE];  
  
SQLULEN    NumRowsFetched;  
SQLUSMALLINT   RowStatusArray[ROW_ARRAY_SIZE], i;  
SQLRETURN      rc;  
SQLHSTMT       hstmt;  
  
// Specify the size of the structure with the SQL_ATTR_ROW_BIND_TYPE  
// statement attribute. This also declares that row-wise binding will  
// be used. Declare the rowset size with the SQL_ATTR_ROW_ARRAY_SIZE  
// statement attribute. Set the SQL_ATTR_ROW_STATUS_PTR statement  
// attribute to point to the row status array. Set the  
// SQL_ATTR_ROWS_FETCHED_PTR statement attribute to point to  
// NumRowsFetched.  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_BIND_TYPE, sizeof(ORDERINFO), 0);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_ARRAY_SIZE, ROW_ARRAY_SIZE, 0);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_STATUS_PTR, RowStatusArray, 0);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROWS_FETCHED_PTR, &NumRowsFetched, 0);  
  
// Bind elements of the first structure in the array to the OrderID,  
// SalesPerson, and Status columns.  
SQLBindCol(hstmt, 1, SQL_C_ULONG, &OrderInfoArray[0].OrderID, 0, &OrderInfoArray[0].OrderIDInd);  
SQLBindCol(hstmt, 2, SQL_C_CHAR, OrderInfoArray[0].SalesPerson,  
            sizeof(OrderInfoArray[0].SalesPerson),  
            &OrderInfoArray[0].SalesPersonLenOrInd);  
SQLBindCol(hstmt, 3, SQL_C_CHAR, OrderInfoArray[0].Status,  
            sizeof(OrderInfoArray[0].Status), &OrderInfoArray[0].StatusLenOrInd);  
  
// Execute a statement to retrieve rows from the Orders table.  
SQLExecDirect(hstmt, "SELECT OrderID, SalesPerson, Status FROM Orders", SQL_NTS);  
  
// Fetch up to the rowset size number of rows at a time. Print the actual  
// number of rows fetched; this number is returned in NumRowsFetched.  
// Check the row status array to print only those rows successfully  
// fetched. Code to check if rc equals SQL_SUCCESS_WITH_INFO or  
// SQL_ERRORnot shown.  
while ((rc = SQLFetchScroll(hstmt,SQL_FETCH_NEXT,0)) != SQL_NO_DATA) {  
   for (i = 0; i < NumRowsFetched; i++) {  
      if (RowStatusArray[i] == SQL_ROW_SUCCESS|| RowStatusArray[i] ==   
         SQL_ROW_SUCCESS_WITH_INFO) {  
         if (OrderInfoArray[i].OrderIDInd == SQL_NULL_DATA)  
            printf(" NULL      ");  
         else  
            printf("%d\t", OrderInfoArray[i].OrderID);  
         if (OrderInfoArray[i].SalesPersonLenOrInd == SQL_NULL_DATA)  
            printf(" NULL      ");  
         else  
            printf("%s\t", OrderInfoArray[i].SalesPerson);  
         if (OrderInfoArray[i].StatusLenOrInd == SQL_NULL_DATA)  
            printf(" NULL\n");  
         else  
            printf("%s\n", OrderInfoArray[i].Status);  
      }  
   }  
}  
  
// Close the cursor.  
SQLCloseCursor(hstmt);  
```
