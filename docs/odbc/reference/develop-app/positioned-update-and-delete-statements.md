---
title: Позиционированного обновления и инструкций Delete | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- positioned deletes [ODBC]
- data updates [ODBC], positioned update or delete
- positioned updates [ODBC]
- updating data [ODBC], positioned update or delete
ms.assetid: 0eafba50-02c7-46ca-a439-ef3307b935dc
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5b37bdfae5f97a453477768aca39b801c06c0701
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68023293"
---
# <a name="positioned-update-and-delete-statements"></a>Инструкции позиционированного обновления и удаления
Приложения могут обновить или удалить текущую строку в результирующем наборе с позиционированного обновления или инструкция delete. Позиционированного обновления и удаления инструкций поддерживаются некоторые источники данных, но не все из них. Чтобы определить ли располагается источник данных поддерживает операторы обновления и удаления, приложение вызывает **SQLGetInfo** SQL_DYNAMIC_CURSOR_ATTRIBUTES1, SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1, SQL_KEYSET_CURSOR_ Атрибутов1 или SQL_STATIC_CURSOR_ATTRIBUTES1 *InfoType* (в зависимости от типа курсора). Обратите внимание на то, что библиотека курсоров ODBC имитирует позиционированного обновления и удаления.  
  
 Чтобы использовать позиционированного обновления или инструкция delete, приложение должно создать результирующий набор с **ВЫБЕРИТЕ для обновления** инструкции. Используется следующий синтаксис этого оператора:  
  
 **ВЫБЕРИТЕ** [**все** &#124; **DISTINCT**] *список выбора*  
  
 **ИЗ** *таблицы список ссылок*  
  
 [**ГДЕ** *условие поиска*]  
  
 **ДЛЯ обновления из** [*имя_столбца* [ **,** *имя_столбца*]...]  
  
 Затем приложение помещает курсор на строке, чтобы обновить или удалить. Его можно сделать, вызвав **SQLFetchScroll** для извлечения набора строк, содержащий необходимые строки и вызова **SQLSetPos** для позиционирования курсора набора строк в этой строке. Затем приложение выполняет позиционированного обновления или инструкции delete на различные инструкции, а не инструкции, используется результирующий набор. Используется следующий синтаксис этих операторов:  
  
 **ОБНОВЛЕНИЕ** *имя таблицы*  
  
 **ЗАДАЙТЕ** *идентификатор столбца* **=** {*выражение* &#124; **NULL**}  
  
 [ **,** *идентификатор столбца* **=** {*выражение* &#124; **NULL**}]...  
  
 **WHERE CURRENT OF** *имя курсора*  
  
 **УДАЛИТЬ из** *имя таблицы* **WHERE CURRENT OF** *имя курсора*  
  
 Обратите внимание на то, что эти операторы требуют имя курсора. Приложения можно указать имя курсора с **SQLSetCursorName** перед выполнением инструкции, которая создает результат задать или можно оставить источника данных автоматически создают имя курсора, при создании курсора. В последнем случае приложение получает это имя курсора для использования в инструкций позиционированного обновления и удаления, вызывая **SQLGetCursorName**.  
  
 Например следующий код позволяет пользователю прокрутить содержимое таблицы клиентов и удаление записей клиентов или обновить свои адреса и номера телефонов. Он вызывает **SQLSetCursorName** для указания имени курсора, прежде чем он создает результирующий набор, клиентов и использует три дескрипторов инструкций: *hstmtCust* для результирующего набора, *hstmtUpdate* для инструкции позиционированного обновления, и *hstmtDelete* для позиционированные инструкции удаления. Несмотря на то, что код может привязать отдельных переменных с параметрами инструкции позиционированного обновления, обновляет буферы строк и привязывает элементы этих буферов. Это действие оставляет буферы строк, синхронизированы с обновленными данными.  
  
```  
#define POSITIONED_UPDATE 100  
#define POSITIONED_DELETE 101  
  
SQLUINTEGER    CustIDArray[10];  
SQLCHAR        NameArray[10][51], AddressArray[10][51],   
               PhoneArray[10][11];  
SQLINTEGER     CustIDIndArray[10], NameLenOrIndArray[10],   
               AddressLenOrIndArray[10],  
               PhoneLenOrIndArray[10];  
SQLUSMALLINT   RowStatusArray[10], Action, RowNum;  
SQLHSTMT       hstmtCust, hstmtUpdate, hstmtDelete;  
  
// Set the SQL_ATTR_BIND_TYPE statement attribute to use column-wise   
// binding. Declare the rowset size with the SQL_ATTR_ROW_ARRAY_SIZE   
// statement attribute. Set the SQL_ATTR_ROW_STATUS_PTR statement   
// attribute to point to the row status array.  
SQLSetStmtAttr(hstmtCust, SQL_ATTR_ROW_BIND_TYPE, SQL_BIND_BY_COLUMN, 0);  
SQLSetStmtAttr(hstmtCust, SQL_ATTR_ROW_ARRAY_SIZE, 10, 0);  
SQLSetStmtAttr(hstmtCust, SQL_ATTR_ROW_STATUS_PTR, RowStatusArray, 0);  
  
// Bind arrays to the CustID, Name, Address, and Phone columns.  
SQLBindCol(hstmtCust, 1, SQL_C_ULONG, CustIDArray, 0, CustIDIndArray);  
SQLBindCol(hstmtCust, 2, SQL_C_CHAR, NameArray, sizeof(NameArray[0]),  
            NameLenOrIndArray);  
SQLBindCol(hstmtCust, 3, SQL_C_CHAR, AddressArray, sizeof(AddressArray[0]),  
         AddressLenOrIndArray);  
SQLBindCol(hstmtCust, 4, SQL_C_CHAR, PhoneArray, sizeof(PhoneArray[0]),  
            PhoneLenOrIndArray);  
  
// Set the cursor name to Cust.  
SQLSetCursorName(hstmtCust, "Cust", SQL_NTS);  
  
// Prepare positioned update and delete statements.  
SQLPrepare(hstmtUpdate,  
   "UPDATE Customers SET Address = ?, Phone = ? WHERE CURRENT OF Cust",  
   SQL_NTS);  
SQLPrepare(hstmtDelete, "DELETE FROM Customers WHERE CURRENT OF Cust", SQL_NTS);  
  
// Execute a statement to retrieve rows from the Customers table.  
SQLExecDirect(hstmtCust,  
   "SELECT CustID, Name, Address, Phone FROM Customers FOR UPDATE OF Address, Phone",  
   SQL_NTS);  
  
// Fetch and display the first 10 rows.  
SQLFetchScroll(hstmtCust, SQL_FETCH_NEXT, 0);  
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
         SQLFetchScroll(hstmtCust, Action, RowNum);  
         DisplayData(CustIDArray, CustIDIndArray, NameArray, NameLenOrIndArray,  
                     AddressArray, AddressLenOrIndArray, PhoneArray,  
                     PhoneLenOrIndArray, RowStatusArray);  
         break;  
  
      case POSITIONED_UPDATE:  
         // Get the new data and place it in the rowset buffers.  
         GetNewData(AddressArray[RowNum - 1], &AddressLenOrIndArray[RowNum - 1],  
                     PhoneArray[RowNum - 1], &PhoneLenOrIndArray[RowNum - 1]);  
  
         // Bind the elements of the arrays at position RowNum-1 to the   
         // parameters of the positioned update statement.  
         SQLBindParameter(hstmtUpdate, 1, SQL_PARAM_INPUT, SQL_C_CHAR, SQL_CHAR,  
                           50, 0, AddressArray[RowNum - 1], sizeof(AddressArray[0]),  
                           &AddressLenOrIndArray[RowNum - 1]);  
         SQLBindParameter(hstmtUpdate, 2, SQL_PARAM_INPUT, SQL_C_CHAR, SQL_CHAR,  
                           10, 0, PhoneArray[RowNum - 1], sizeof(PhoneArray[0]),  
                           &PhoneLenOrIndArray[RowNum - 1]);  
  
         // Position the rowset cursor. The rowset is 1-based.  
         SQLSetPos(hstmtCust, RowNum, SQL_POSITION, SQL_LOCK_NO_CHANGE);  
  
         // Execute the positioned update statement to update the row.  
         SQLExecute(hstmtUpdate);  
         break;  
  
      case POSITIONED_DELETE:  
         // Position the rowset cursor. The rowset is 1-based.  
         SQLSetPos(hstmtCust, RowNum, SQL_POSITION, SQL_LOCK_NO_CHANGE);  
  
         // Execute the positioned delete statement to delete the row.  
         SQLExecute(hstmtDelete);  
         break;  
   }  
}  
  
// Close the cursor.  
SQLCloseCursor(hstmtCust);  
```
