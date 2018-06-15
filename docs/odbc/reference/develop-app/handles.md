---
title: Обрабатывает | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- handles [ODBC]
- driver handles [ODBC]
- driver manager [ODBC], handles
- handles [ODBC], about handles
ms.assetid: f663101e-a4cc-402b-b9d7-84d5e975be71
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 830c4b653af74097c59c9aff9e073267792a84b7
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32912899"
---
# <a name="handles"></a>Маркеры
Дескрипторы являются непрозрачных, 32-разрядных значений, определяющих какой-либо элемент; в ODBC этот элемент может быть среды, соединения, оператор или дескриптора. Когда приложение вызывает **SQLAllocHandle**, диспетчер драйверов или драйвер создает новый элемент заданного типа и возвращает его дескриптор в приложение. Позднее приложение использует маркер для идентификации этого элемента при вызове функций ODBC. Диспетчер драйверов и драйвер найдите сведения об элементе с помощью маркера.  
  
 Например, следующий код использует двух дескрипторов инструкции (*hstmtOrder* и *hstmtLine*) для идентификации операторов, по которым создается результирующих наборов продаж заказов и sales order номера строк. Для определения, какие результирующий набор для выборки данных из более поздней версии применяет эти маркеры.  
  
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
  
 Маркеры имеют смысл только в ODBC компонента, который создал их; то есть только диспетчер драйверов может интерпретировать дескрипторы диспетчера драйверов, а только драйвер может интерпретировать свои собственные дескрипторы.  
  
 Предположим, например, драйвер в предыдущем примере выделяет структура для хранения сведений об инструкции и возвращает указатель на эту структуру как дескриптор инструкции. Когда приложение вызывает **SQLPrepare**, он передает инструкции SQL и дескриптор инструкции, используемые для номеров строк заказов на продажу. Драйвер отправляет инструкцию SQL для источника данных, который подготавливает его и возвращает идентификатор плана доступа. Драйвер использует дескриптор для поиска структуры, в котором будет храниться этот идентификатор.  
  
 Позже, когда приложение вызывает **SQLExecute** для создания результирующего набора номера строк для конкретного заказа на продажу, он передает тот же дескриптор. Драйвер использует дескриптор для извлечения идентификатора плана доступ из структуры. Он отправляет идентификатор источника данных о том, который планируется выполнить.  
  
 ODBC имеет два уровня дескрипторов: дескрипторах диспетчера драйверов и драйверов. Приложение с помощью диспетчера драйверов дескрипторы при вызове функции ODBC, так как он вызывает эти функции диспетчера драйверов. Диспетчер драйверов использует этот дескриптор для поиска соответствующих драйверов дескриптор и использует маркер драйвера при вызове функции в драйвере. Пример использования драйвера и обрабатывает диспетчера драйверов см. в разделе [роли диспетчера драйверов в процесс подключения](../../../odbc/reference/develop-app/driver-manager-s-role-in-the-connection-process.md).  
  
 Том, что существует два уровня дескрипторов является артефактом архитектура ODBC; в большинстве случаев не применимо к приложения или драйвера. Хотя обычно нет причин для этого, это приложение может определить драйвера дескрипторы, вызвав **SQLGetInfo**.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Дескрипторы среды](../../../odbc/reference/develop-app/environment-handles.md)  
  
-   [Дескрипторы подключений](../../../odbc/reference/develop-app/connection-handles.md)  
  
-   [Дескрипторы инструкций](../../../odbc/reference/develop-app/statement-handles.md)  
  
-   [Указатели дескрипторов](../../../odbc/reference/develop-app/descriptor-handles.md)  
  
-   [Переходы состояния](../../../odbc/reference/develop-app/state-transitions.md)
