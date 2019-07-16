---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0575c7ef7e380b1157640f9927e41192838c1ac0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68091602"
---
# <a name="updating-rows-in-the-rowset-with-sqlsetpos"></a>Обновление строк в наборе строк с помощью SQLSetPos
Операции обновления из **SQLSetPos** позволяет обновить один или несколько выбранных строк таблицы, используя данные в буферах приложения для каждого привязанного столбца (если значение в буфер длины/индикатора не SQL_COLUMN_IGNORE) источника данных. Столбцы, которые не связаны не обновляется.  
  
 Обновление строк с **SQLSetPos**, приложение выполняет следующие:  
  
1.  Помещает новые значения данных в буферах набора строк. Сведения о том, как для отправления объемных данных с помощью **SQLSetPos**, см. в разделе [длинных данных и функции SQLSetPos и SQLBulkOperations](../../../odbc/reference/develop-app/long-data-and-sqlsetpos-and-sqlbulkoperations.md).  
  
2.  Задает значение в буфер длины/индикатора каждого столбца, при необходимости. Это байтовая длина данных или SQL_NTS для столбцов, привязанных к буферам строк байтовая длина данных для столбцов, привязанных к двоичных буферах и SQL_NULL_DATA для всех столбцов будет присвоено значение NULL.  
  
3.  Задает значение в буфер длины/индикатора значений этих столбцов, которые не должны быть обновлены для SQL_COLUMN_IGNORE. Несмотря на то, что приложение может пропустить этот шаг и повторно отправить существующих данных, этот способ малоэффективен и привести к отправке значений в источнике данных, были усечены при чтении.  
  
4.  Вызовы **SQLSetPos** с *операции* присвоено SQL_UPDATE и *RowNumber* задайте количество строк, чтобы обновить. Если *RowNumber* равно 0, обновляются все строки в наборе строк.  
  
 После **SQLSetPos** возвращает, обновленная строка имеет значение текущей строки.  
  
 При обновлении все строки набора строк (*RowNumber* равно 0), приложение может отключить обновление некоторых строк, задав соответствующие элементы массива операций строк (на него указывает SQL_ATTR_ROW_OPERATION_PTR атрибут инструкции) для SQL_ROW_IGNORE. Размер и количество элементов в массив статусов строк (на него указывает атрибут инструкции значения SQL_ATTR_ROW_STATUS_PTR) соответствует массива операций строк. Чтобы обновить только строки в результирующем наборе, которые были успешно получен и не были удалены из набора строк, приложение использует массив статусов строк из функции, которые были получены ранее набора строк как массива операций строк для **SQLSetPos**.  
  
 Для каждой строки, которая отправляется к источнику данных, как обновление буферы приложения должны иметь допустимую строку данных. Если буферы приложения заполняются выборкой, а массив состояния строк была сохранена, значения каждой из этих позиций строк не должно быть значение SQL_ROW_DELETED, SQL_ROW_ERROR или SQL_ROW_NOROW.  
  
 Например следующий код позволяет пользователю прокрутить содержимое таблицы клиентов и обновления, удаления или добавления новых строк. Она помещает новые данные в буферах строк перед вызовом **SQLSetPos** для обновления или добавления новых строк. Дополнительная строка выделяется в конце буферы строк для хранения новых строк; Это предотвращает перезапись при помещении данных для новой строки в буферы существующих данных.  
  
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
