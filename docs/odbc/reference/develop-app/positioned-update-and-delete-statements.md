---
title: Позиционируется обновление и удаление заявления (ru) Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6e5316bee7057b30eace326b3ca82b30b75741fb
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81282365"
---
# <a name="positioned-update-and-delete-statements"></a>Инструкции позиционированного обновления и удаления
Приложения могут обновлять или удалять текущую строку в наборе результатов с позиционированным обновлением или удалением оператора. Позиционированные операторы обновления и удаления поддерживаются некоторыми источниками данных, но не всеми из них. Чтобы определить, поддерживает ли источник данных позиционированные операторы обновления и удаления, приложение вызывает **S'LGetInfo** с SQL_DYNAMIC_CURSOR_ATTRIBUTES1, SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1, SQL_KEYSET_CURSOR_ATTRIBUTES1 или SQL_STATIC_CURSOR_ATTRIBUTES1 *InfoType* (в зависимости от типа курсора). Обратите внимание, что библиотека курсора ODBC имитирует позиционированные обновления и удаления инструкций.  
  
 Чтобы использовать позиционированное обновление или удаление оператора, приложение должно создать набор результатов с заявлением **SELECT FOR UPDATE.** Синтаксис этого заявления:  
  
 **SELECT** -**ВСЕ** &#124; **ОТЛИЧИЕ**- *список выбора*  
  
 **Из** *списка таблицы-справочника*  
  
 **Где** *поиск-условие*  
  
 **ДЛЯ ОБНОВЛЕНИЕ** ИЗ -*название столбца* **,** *колонка-имя*  
  
 Затем приложение позиционирует курсор на строке для обновления или удаления. Он может сделать это, позвонив в **S'LFetchScroll,** чтобы получить набор строк, содержащий требуемую строку, и позвонив в **S'LSetPos** для размещения курсора строки на этой строке. Затем приложение выполняет позиционированное обновление или удаляет выписку по другому заявлению, чем утверждение, используемое набором результатов. Синтаксис этих утверждений:  
  
 **ОБНОВЛЕНИЕ** *название таблицы*  
  
 **SET** *столбец-идентификатор* **=** -*выражение* &#124; **NULL**  
  
 - **=** **,** *столбец-идентификатор* -*выражение* &#124; **NULL**  
  
 **ГДЕ CURRENT Of** *курсор-имя*  
  
 **DELETE От** *таблицы-имя* ГДЕ CURRENT *курсора-имя* **WHERE CURRENT OF**  
  
 Обратите внимание, что эти операторы требуют имени курсора. Приложение может либо указать имя курсора с **s'LSetCursorName** перед выполнением оператора, который создает набор результатов, либо может позволить источнику данных автоматически генерировать имя курсора при создании курсора. В последнем случае приложение получает это имя курсора для использования в позиционированном обновлении и удалении выписок, позвонив по **s'LGetCursorName.**  
  
 Например, следующий код позволяет пользователю прокручивать таблицу Клиентов и удалять записи клиентов или обновлять их адреса и номера телефонов. Он вызывает **имя cursor,** прежде чем он создает набор результатов клиентов и использует три ручки оператора: *hstmtCust* для набора результатов, *hstmtUpdate* для позиционированного оператора обновления и *hstmtDelete* для оператора удаления. Хотя код может связывать отдельные переменные с параметрами в позиционированном отчете обновления, он обновляет буферы строк и связывает элементы этих буферов. Это позволяет синхронизировать буферы строк с обновленными данными.  
  
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
