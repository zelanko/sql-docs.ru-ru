---
title: Дескрипторы | Документация Майкрософт
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81300214"
---
# <a name="handles"></a>Маркеры
Дескрипторы — это непрозрачные, 32-разрядные значения, которые определяют конкретный элемент. в ODBC этот элемент может быть средой, соединением, инструкцией или дескриптором. Когда приложение вызывает **функцию SQLAllocHandle**, диспетчер драйверов или драйвер создает новый элемент указанного типа и возвращает его обработчик приложению. В дальнейшем приложение использует этот обработчик для обнаружения этого элемента при вызове функций ODBC. Диспетчер драйверов и драйвер используют этот маркер для нахождение сведений об элементе.  
  
 Например, в следующем коде используются два дескриптора операторов (*хстмтордер* и *хстмтлине*) для указания инструкций, по которым создаются результирующие наборы заказов на продажу и номеров строк заказа на продажу. В дальнейшем эти дескрипторы используются для указания результирующего набора, из которого следует извлечь данные.  
  
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
  
 Дескрипторы имеют смысл только для компонента ODBC, который их создал. то есть только диспетчер драйверов может интерпретировать дескрипторы диспетчера драйверов, и только драйвер может интерпретировать свои собственные дескрипторы.  
  
 Например, предположим, что драйвер в предыдущем примере выделяет структуру для хранения сведений об операторе и возвращает указатель на эту структуру в качестве маркера инструкции. Когда приложение вызывает **SQLPrepare**, оно передает инструкцию SQL и маркер инструкции, используемой для номеров строк заказа на продажу. Драйвер отправляет инструкцию SQL в источник данных, который готовит его и возвращает идентификатор плана доступа. Драйвер использует этот маркер для поиска структуры, в которой хранится этот идентификатор.  
  
 Позже, когда приложение вызывает **SQLExecute** для создания результирующего набора номеров строк для конкретного заказа на продажу, он передает тот же самый маркер. Драйвер использует этот маркер для получения идентификатора плана доступа из структуры. Он отправляет идентификатор источнику данных, чтобы сообщить ему, какой план выполнить.  
  
 ODBC имеет два уровня дескрипторов: дескрипторы диспетчера драйверов и дескрипторы драйверов. Приложение использует диспетчер драйверов при вызове функций ODBC, так как вызывает эти функции в диспетчере драйверов. Диспетчер драйверов использует этот обработчик для поиска соответствующего обработчика драйвера и использует его при вызове функции в драйвере. Пример использования дескрипторов драйвера и диспетчера драйверов см. [в разделе роль диспетчера драйверов в процессе подключения](../../../odbc/reference/develop-app/driver-manager-s-role-in-the-connection-process.md).  
  
 Существует два уровня дескрипторов — это артефакт архитектуры ODBC. в большинстве случаев это не относится к приложению или драйверу. Хотя обычно нет никаких причин, приложение может определить дескрипторы драйвера, вызвав **SQLGetInfo**.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Дескрипторы среды](../../../odbc/reference/develop-app/environment-handles.md)  
  
-   [Дескрипторы подключений](../../../odbc/reference/develop-app/connection-handles.md)  
  
-   [Дескрипторы инструкций](../../../odbc/reference/develop-app/statement-handles.md)  
  
-   [Указатели дескрипторов](../../../odbc/reference/develop-app/descriptor-handles.md)  
  
-   [Переходы состояния](../../../odbc/reference/develop-app/state-transitions.md)
