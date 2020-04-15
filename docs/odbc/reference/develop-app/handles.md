---
title: Ручки Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- handles [ODBC]
- driver handles [ODBC]
- driver manager [ODBC], handles
- handles [ODBC], about handles
ms.assetid: f663101e-a4cc-402b-b9d7-84d5e975be71
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 713c2a71ec195b75d682b97239413e98d07b5861
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300214"
---
# <a name="handles"></a>Маркеры
Ручки являются непрозрачными, 32-битные значения, которые определяют конкретный элемент; в ODBC этот элемент может быть средой, соединением, заявлением или дескриптором. Когда приложение вызывает **S'LAllocHandle,** менеджер драйвера или драйвер создает новый элемент указанного типа и возвращает свою ручку в приложение. Позже приложение использует ручку для идентификации этого элемента при вызове функций ODBC. Менеджер драйвера и водитель используют ручку для поиска информации о товаре.  
  
 Например, в следующем коде используются две ручки оператора *(hstmtOrder* и *hstmtLine)* для определения инструкций, на которых можно создавать наборы заказов на продажи и номера линий заказов продаж. Позже он использует эти ручки, чтобы определить, какой набор результатов для получения данных.  
  
```  
SQLHSTMT      hstmtOrder, hstmtLine; // Statement handles.  
SQLUINTEGER   OrderID;  
SQLINTEGER    OrderIDInd = 0;  
SQLRETURN     rc;  
  
// Prepare the statement that retrieves line number information.  
SQLPrepare(hstmtLine, "SELECT * FROM Lines WHERE OrderID = ?", SQL_NTS);  
  
// Bind OrderID to the parameter in the preceding statement.  
SQLBindParameter(hstmtLine, 1, SQL_PARAM_INPUT, SQL_C_ULONG, SQL_INTEGER, 5, 0,  
               &OrderID, 0, &OrderIDInd);  
  
// Bind the result sets for the Order table and the Lines table. Bind  
// OrderID to the OrderID column in the Orders table. When each row is  
// fetched, OrderID will contain the current order ID, which will then be  
// passed as a parameter to the statement tofetch line number  
// information. Code not shown.  
  
// Create a result set of sales orders.  
SQLExecDirect(hstmtOrder, "SELECT * FROM Orders", SQL_NTS);  
  
// Fetch and display the sales order data. Code to check if rc equals  
// SQL_ERROR or SQL_SUCCESS_WITH_INFO not shown.  
while ((rc = SQLFetch(hstmtOrder)) != SQL_NO_DATA) {  
   // Display the sales order data. Code not shown.  
  
   // Create a result set of line numbers for the current sales order.  
   SQLExecute(hstmtLine);  
  
   // Fetch and display the sales order line number data. Code to check  
   // if rc equals SQL_ERROR or SQL_SUCCESS_WITH_INFO not shown.  
   while ((rc = SQLFetch(hstmtLine)) != SQL_NO_DATA) {  
      // Display the sales order line number data. Code not shown.  
   }  
  
   // Close the sales order line number result set.  
   SQLCloseCursor(hstmtLine);  
}  
  
// Close the sales order result set.  
SQLCloseCursor(hstmtOrder);  
```  
  
 Ручки имеют значение только для компонента ODBC, который их создал; то есть только менеджер драйвера может интерпретировать ручки менеджера драйвера, и только водитель может интерпретировать свои собственные ручки.  
  
 Например, предположим, что драйвер в предыдущем примере выделяет структуру для хранения информации об отчете и возвращает указатель в эту структуру по мере обработки оператора. Когда приложение вызывает **s'LPrepare,** оно проходит выписку s'L и ручку оператора, используемого для номеров линии заказов продаж. Водитель отправляет выписку по S'L в источник данных, который готовит его и возвращает идентификатор плана доступа. Водитель использует ручку, чтобы найти структуру, в которой для хранения этого идентификатора.  
  
 Позже, когда приложение вызывает **S'LExecute** для генерации набора строк для конкретного заказа продаж, оно проходит ту же ручку. Драйвер использует ручку для извлечения идентификатора плана доступа из структуры. Он отправляет идентификатор в источник данных, чтобы сказать ему, какой план выполнить.  
  
 ODBC имеет два уровня ручек: ручки Driver Manager и ручки драйверов. Приложение использует ручки Driver Manager при вызове функций ODBC, поскольку оно вызывает эти функции в менеджере драйвера. Менеджер драйвера использует эту ручку, чтобы найти соответствующую ручку драйвера и использует ручку драйвера при вызове функции в драйвере. На примере использования ручек драйвера и менеджера драйверов см. [роль менеджера драйвера в процессе подключения.](../../../odbc/reference/develop-app/driver-manager-s-role-in-the-connection-process.md)  
  
 То, что существует два уровня ручек, является артефактом архитектуры ODBC; в большинстве случаев это не имеет отношения ни к приложению, ни к водителю. Хотя, как правило, нет никаких причин, чтобы сделать это, это возможно для приложения, чтобы определить ручки драйвера, позвонив **s'LGetInfo**.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Дескрипторы среды](../../../odbc/reference/develop-app/environment-handles.md)  
  
-   [Дескрипторы подключений](../../../odbc/reference/develop-app/connection-handles.md)  
  
-   [Дескрипторы инструкций](../../../odbc/reference/develop-app/statement-handles.md)  
  
-   [Указатели дескрипторов](../../../odbc/reference/develop-app/descriptor-handles.md)  
  
-   [Переходы состояния](../../../odbc/reference/develop-app/state-transitions.md)
