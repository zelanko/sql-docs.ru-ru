---
title: SQLFetchScroll | Документация Майкрософт
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLFetchScroll function
ms.assetid: 524a3985-a08d-4445-99e0-bb551a666615
caps.latest.revision: 35
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 4418a1ce37958c704e30692ab1cfed57aca471f5
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37410253"
---
# <a name="sqlfetchscroll"></a>SQLFetchScroll
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Функция**SQLFetchScroll** возвращает приложению один набор строк данных. Размер набора строк задается с помощью [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md). [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Драйвер ODBC для собственного клиента поддерживает все определенные инструкции выборки (например, SQL_FETCH_RELATIVE) со следующими ограничениями:  
  
-   Если для инструкции определен однопроходный курсор, необходимо использовать инструкцию SQL_FETCH_NEXT, а попытки произвести выборку любым другим способом приведут к ошибке.  
  
-   Инструкция SQL_FETCH_BOOKMARK поддерживается только для статических курсоров и курсоров, управляемых набором ключей.  
  
## <a name="sqlfetchscroll-support-for-enhanced-date-and-time-features"></a>Поддержка функцией SQLFetchScroll улучшенных функций даты и времени  
 Значения результирующих столбцов типов даты времени преобразуются, как описано в разделе [преобразования из SQL в C](../../relational-databases/native-client-odbc-date-time/datetime-data-type-conversions-from-sql-to-c.md).  
  
 Дополнительные сведения см. в разделе [время улучшения функций даты и &#40;ODBC&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlfetchscroll-support-for-large-clr-udts"></a>Поддержка функцией SQLFetchScroll больших определяемых пользователем типов CLR  
 Функция**SQLFetchScroll** поддерживает большие определяемые пользователем типы данных CLR. Дополнительные сведения см. в разделе [Large CLR User-Defined типы &#40;ODBC&#41;](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>См. также  
 [Функция SQLFetchScroll](http://go.microsoft.com/fwlink/?LinkId=59343)   
 [Подробные сведения о реализации API-интерфейсов ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
