---
title: Обновление строк в Строке с помощью S'LSetPos (ru) Документы Майкрософт
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
ms.openlocfilehash: 4851d4ba741379fc188b2b88c895a378ef3bb80d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298974"
---
# <a name="updating-rows-in-the-rowset-with-sqlsetpos"></a>Обновление строк в наборе строк с помощью SQLSetPos
Операция обновления **S'LSetPos** делает обновление источника данных одним или более выбранными строками таблицы, используя данные в буферах приложения для каждого связанного столбца (если значение в буфере длины/индикатора не является SQL_COLUMN_IGNORE). Столбцы, которые не связаны, не будут обновляться.  
  
 Для обновления строк с **помощью S'LSetPos**приложение выполняет следующее:  
  
1.  Размещает новые значения данных в буферах рядового набора. Для получения информации о том, как отправлять [Long Data and SQLSetPos and SQLBulkOperations](../../../odbc/reference/develop-app/long-data-and-sqlsetpos-and-sqlbulkoperations.md)длинные данные с **помощью S'LSetPos,** см.  
  
2.  Устанавливает значение в буфере длины/индикатора каждого столбца по мере необходимости. Это длина данных или SQL_NTS для столбцов, привязанных к строке буферов, длина байт данных для столбцов, привязанных к бинарным буферам, и SQL_NULL_DATA для любых столбцов, которые будут установлены на NULL.  
  
3.  Устанавливает значение в буфере длины/индикатора тех столбцов, которые не должны обновляться до SQL_COLUMN_IGNORE. Хотя приложение может пропустить этот шаг и отправить существующие данные, это неэффективно и рискует отправить значения в источник данных, которые были усечены при чтении.  
  
4.  Вызовы **S'LSetPos** с *операцией,* установленной для SQL_UPDATE и *RowNumber,* устанавливается на номер строки для обновления. Если *RowNumber* равен 0, все строки в наборе строк обновляются.  
  
 После возвращения **S'LSetPos** текущая строка устанавливается в обновленную строку.  
  
 При обновлении всех строк строк строки *(RowNumber* равен 0), приложение может отключить обновление определенных строк, установив соответствующие элементы массива операции строки (на который указывает атрибут SQL_ATTR_ROW_OPERATION_PTR оператора) на SQL_ROW_IGNORE. Массив операции строки соответствует по размеру и количеству элементов массиву состояния строки (указывается на SQL_ATTR_ROW_STATUS_PTR атрибута оператора). Для обновления только тех строк в наборе результатов, которые были успешно извлечены и не были удалены из набора строк, приложение использует массив состояния строкизм из функции, которая принесла строку в качестве массива работы строки в **S'LSetPos.**  
  
 Для каждой строки, отправленной в источник данных в качестве обновления, буферы приложения должны иметь действительные данные строки. Если буферы приложения были заполнены путем извлечения и если массив состояния строки был сохранен, его значения в каждой из этих строк не должны быть SQL_ROW_DELETED, SQL_ROW_ERROR или SQL_ROW_NOROW.  
  
 Например, следующий код позволяет пользователю прокручивать таблицу Клиентов и обновлять, удалять или добавлять новые строки. Он помещает новые данные в буферы строк, прежде чем вызывать **S'LSetPos** для обновления или добавления новых строк. Дополнительная строка выделяется в конце буферов строки для удержания новых строк; это предотвращает перезаписание существующих данных при размещении данных для новой строки в буферах.  
  
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
