---
title: Обрабатывает | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a205a23c4c7e7e45269fd00fc0923d4168ec7091
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63061448"
---
# <a name="handles"></a>Маркеры
Дескрипторы становятся непрозрачных, 32-разрядных значений, определяющих какой-либо элемент; в ODBC этот элемент может быть среды, подключения, инструкции или дескриптора. Когда приложение вызывает **SQLAllocHandle**, диспетчер драйверов или драйвер создает новый элемент указанного типа и возвращает его дескриптор в приложение. Позднее приложение использует маркер для идентификации этого элемента при вызове функций ODBC. Диспетчер драйверов и драйверов с помощью маркера для поиска сведений об элементе.  
  
 Например, следующий код использует двух дескрипторов инструкции (*hstmtOrder* и *hstmtLine*) для определения инструкций, по которым создается результирующих наборов продаж заказов и sales order номера строк. Для идентификации, результирующий набор для получения данных из более поздней версии используются эти маркеры.  
  
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
  
 Маркеры имеют смысл только в компоненте ODBC, создавших их; то есть только диспетчера драйверов может интерпретировать дескрипторы диспетчера драйверов, а только драйвер может интерпретировать свои собственные дескрипторы.  
  
 Например предположим, драйвер в предыдущем примере выделяет структуру для хранения сведений об инструкции и возвращает указатель на эту структуру как дескриптор инструкции. Когда приложение вызывает **SQLPrepare**, он передает инструкции SQL и дескриптор инструкции, используемые для номеров строк заказов на продажу. Драйвер отправляет инструкцию SQL к источнику данных, который подготавливает его и возвращает идентификатор плана доступа. Драйвер использует дескриптор для поиска структуры, в котором будет храниться этот идентификатор.  
  
 Позже, когда приложение вызывает **SQLExecute** для формирования результирующего набора номеров строк для конкретного заказа на продажу, он передает в том же дескрипторе. Драйвер использует дескриптор для извлечения идентификатора плана доступа из структуры. Он отправляет идентификатор источника данных, необходимо сообщить ему, который хотите выполнить.  
  
 ODBC имеет два уровня дескрипторов: Диспетчер драйверов дескрипторы и драйвера дескрипторы. Приложение использует маркеры диспетчера драйверов при вызове функции ODBC, так как он вызывает эти функции диспетчера драйверов. Диспетчер драйверов использует этот дескриптор для поиска соответствующих драйверов дескриптор и дескриптор драйвера при вызове функции в драйвере. Пример того, как использовать драйвер и дескрипторы диспетчера драйверов, см. в разделе [роль диспетчера драйверов в процессе подключения](../../../odbc/reference/develop-app/driver-manager-s-role-in-the-connection-process.md).  
  
 Что существует два уровня дескрипторов является артефактом архитектура ODBC; в большинстве случаев это не относится к приложения или драйвера. Несмотря на то, что обычно нет причин для этого, это приложение может определить драйвера дескрипторы, вызвав **SQLGetInfo**.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Дескрипторы среды](../../../odbc/reference/develop-app/environment-handles.md)  
  
-   [Дескрипторы подключений](../../../odbc/reference/develop-app/connection-handles.md)  
  
-   [Дескрипторы инструкций](../../../odbc/reference/develop-app/statement-handles.md)  
  
-   [Указатели дескрипторов](../../../odbc/reference/develop-app/descriptor-handles.md)  
  
-   [Переходы состояния](../../../odbc/reference/develop-app/state-transitions.md)
