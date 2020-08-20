---
description: Обновление строк в наборе строк с помощью SQLSetPos
title: Обновление строк в наборе строк с помощью SQLSetPos | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- updating data [ODBC], SQLSetPos
- data updates [ODBC], SQLSetPos
- SQLSetPos function [ODBC], updating rows
ms.assetid: d83a8c2a-5aa8-4f19-947c-79a817167ee1
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d1b1b50007a03ee1973d92acafbe8f2be1022f52
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88471219"
---
# <a name="updating-rows-in-the-rowset-with-sqlsetpos"></a>Обновление строк в наборе строк с помощью SQLSetPos
Операция обновления функции **SQLSetPos** позволяет источнику данных обновлять одну или несколько строк таблицы, используя данные в буферах приложений для каждого привязанного столбца (если значение в буфере длины или индикатора не SQL_COLUMN_IGNORE). Столбцы, которые не привязаны, не будут обновлены.  
  
 Для обновления строк с помощью функции **SQLSetPos**приложение выполняет следующие действия:  
  
1.  Помещает новые значения данных в буферы набора строк. Сведения о том, как отправить длинные данные с помощью функции **SQLSetPos**, см. в разделе [Long Data, SQLSetPos и SQLBulkOperations](../../../odbc/reference/develop-app/long-data-and-sqlsetpos-and-sqlbulkoperations.md).  
  
2.  При необходимости устанавливает значение в буфере длины и индикатора для каждого столбца. Это длина байта данных или SQL_NTS для столбцов, привязанных к буферам строк, длина байтов данных для столбцов, привязанных к двоичным буферам, и SQL_NULL_DATA для всех столбцов, для которых задано значение NULL.  
  
3.  Задает значение в буфере длины или индикатора для столбцов, которые не обновляются до SQL_COLUMN_IGNORE. Несмотря на то, что приложение может пропустить этот шаг и повторно отправить существующие данные, это неэффективно и риски отправляют значения в источник данных, который был усечен при чтении.  
  
4.  Вызывает функцию **SQLSetPos** с набором *операций* SQL_UPDATE, а функция *RowNumber* задает номер обновляемой строки. Если параметр *RowNumber* имеет значение 0, то обновляются все строки в наборе строк.  
  
 После возврата функции **SQLSetPos** текущей строке присваивается обновленная строка.  
  
 При обновлении всех строк набора строк (*RowNumber* равен 0) приложение может отключить обновление определенных строк, задав соответствующие элементы массива операций строк (на который указывает атрибут инструкции SQL_ATTR_ROW_OPERATION_PTR) для SQL_ROW_IGNORE. Массив операций строк соответствует размеру и числу элементов в массиве состояния строки (на который указывает атрибут инструкции SQL_ATTR_ROW_STATUS_PTR). Чтобы обновить только те строки результирующего набора, которые были успешно получены и не были удалены из набора строк, приложение использует массив состояния строк из функции, которая извлекает набор **строк в качестве**развернутого массива операций строк.  
  
 Для каждой строки, которая отправляется в источник данных как обновление, буферы приложения должны иметь допустимые данные строк. Если буферы приложения были заполнены путем выборки и если массив состояния строки был сохранен, то его значения в каждой из этих положений строки не должны быть SQL_ROW_DELETED, SQL_ROW_ERROR или SQL_ROW_NOROW.  
  
 Например, следующий код позволяет пользователю прокручивать таблицу Customers, обновлять, удалять или добавлять новые строки. Он помещает новые данные в буферы набора строк перед вызовом функции **SQLSetPos** для обновления или добавления новых строк. В конце буферов набора строк выделяются дополнительные строки для хранения новых строк. Это предотвращает перезапись существующих данных при помещении данных для новой строки в буферы.  
  
```  
#define UPDATE_ROW   100  
#define DELETE_ROW   101  
#define ADD_ROW      102  
  
SQLUINTEGER    CustIDArray[11];  
SQLCHAR        NameArray[11][51], AddressArray[11][51],   
               PhoneArray[11][11];  
SQLINTEGER     CustIDIndArray[11], NameLenOrIndArray[11],   
               AddressLenOrIndArray[11],  
               PhoneLenOrIndArray[11];  
SQLUSMALLINT   RowStatusArray[10], Action, RowNum;  
SQLRETURN      rc;  
SQLHSTMT       hstmt;  
  
// Set the SQL_ATTR_ROW_BIND_TYPE statement attribute to use column-wise   
// binding. Declare the rowset size with the SQL_ATTR_ROW_ARRAY_SIZE   
// statement attribute. Set the SQL_ATTR_ROW_STATUS_PTR statement   
// attribute to point to the row status array.  
SQLSetStmtAttr(hstmt, SQL_ATTR_CURSOR_TYPE, SQL_CURSOR_KEYSET_DRIVEN, 0);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_BIND_TYPE, SQL_BIND_BY_COLUMN, 0);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_ARRAY_SIZE, 10, 0);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_STATUS_PTR, RowStatusArray, 0);  
  
// Bind arrays to the CustID, Name, Address, and Phone columns.  
SQLBindCol(hstmt, 1, SQL_C_ULONG, CustIDArray, 0, CustIDIndArray);  
SQLBindCol(hstmt, 2, SQL_C_CHAR, NameArray, sizeof(NameArray[0]), NameLenOrIndArray);  
SQLBindCol(hstmt, 3, SQL_C_CHAR, AddressArray, sizeof(AddressArray[0]),  
            AddressLenOrIndArray);  
SQLBindCol(hstmt, 4, SQL_C_CHAR, PhoneArray, sizeof(PhoneArray[0]),  
            PhoneLenOrIndArray);  
  
// Execute a statement to retrieve rows from the Customers table.  
SQLExecDirect(hstmt, "SELECT CustID, Name, Address, Phone FROM Customers", SQL_NTS);  
  
// Fetch and display the first 10 rows.  
rc = SQLFetchScroll(hstmt, SQL_FETCH_NEXT, 0);  
DisplayData(CustIDArray, CustIDIndArray, NameArray, NameLenOrIndArray, AddressArray,  
            AddressLenOrIndArray, PhoneArray, PhoneLenOrIndArray, RowStatusArray);  
  
// Call GetAction to get an action and a row number from the user.  
while (GetAction(&Action, &RowNum)) {  
   switch (Action) {  
  
      case SQL_FETCH_NEXT:  
      case SQL_FETCH_PRIOR:  
      case SQL_FETCH_FIRST:  
      case SQL_FETCH_LAST:  
      case SQL_FETCH_ABSOLUTE:  
      case SQL_FETCH_RELATIVE:  
         // Fetch and display the requested data.  
         SQLFetchScroll(hstmt, Action, RowNum);  
         DisplayData(CustIDArray, CustIDIndArray,  
                     NameArray, NameLenOrIndArray,  
                     AddressArray, AddressLenOrIndArray,  
                     PhoneArray, PhoneLenOrIndArray, RowStatusArray);  
         break;  
  
      case UPDATE_ROW:  
         // Place the new data in the rowset buffers and update the   
         // specified row.  
         GetNewData(&CustIDArray[RowNum - 1], &CustIDIndArray[RowNum - 1],  
                  NameArray[RowNum - 1], &NameLenOrIndArray[RowNum - 1],  
                  AddressArray[RowNum - 1], &AddressLenOrIndArray[RowNum - 1],  
                  PhoneArray[RowNum - 1], &PhoneLenOrIndArray[RowNum - 1]);  
         SQLSetPos(hstmt, RowNum, SQL_UPDATE, SQL_LOCK_NO_CHANGE);  
         break;  
  
      case DELETE_ROW:  
         // Delete the specified row.  
         SQLSetPos(hstmt, RowNum, SQL_DELETE, SQL_LOCK_NO_CHANGE);  
         break;  
  
      case ADD_ROW:  
         // Place the new data in the rowset buffers at index 10.   
         // This is an extra element for new rows so rowset data is   
         // not overwritten. Insert the new row. Row 11 corresponds   
         // to index 10.  
         GetNewData(&CustIDArray[10], &CustIDIndArray[10],  
                     NameArray[10], &NameLenOrIndArray[10],  
                     AddressArray[10], &AddressLenOrIndArray[10],  
                     PhoneArray[10], &PhoneLenOrIndArray[10]);  
         SQLSetPos(hstmt, 11, SQL_ADD, SQL_LOCK_NO_CHANGE);  
         break;  
   }  
}  
  
// Close the cursor.  
SQLCloseCursor(hstmt);  
```
