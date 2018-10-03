---
title: SQLFetchScroll | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLFetchScroll function
ms.assetid: 524a3985-a08d-4445-99e0-bb551a666615
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9ee2297f01ef2cc0a4dc94beca66939bf6ae9030
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48145654"
---
# <a name="sqlfetchscroll"></a>SQLFetchScroll
  Функция**SQLFetchScroll** возвращает приложению один набор строк данных. Размер набора строк задается с помощью [SQLSetStmtAttr](sqlsetstmtattr.md). [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Драйвер ODBC для собственного клиента поддерживает все определенные инструкции выборки (например, SQL_FETCH_RELATIVE) со следующими ограничениями:  
  
-   Если для инструкции определен однопроходный курсор, необходимо использовать инструкцию SQL_FETCH_NEXT, а попытки произвести выборку любым другим способом приведут к ошибке.  
  
-   Инструкция SQL_FETCH_BOOKMARK поддерживается только для статических курсоров и курсоров, управляемых набором ключей.  
  
## <a name="sqlfetchscroll-support-for-enhanced-date-and-time-features"></a>Поддержка функцией SQLFetchScroll улучшенных функций даты и времени  
 Значения результирующих столбцов типов даты времени преобразуются, как описано в разделе [преобразования из SQL в C](../native-client-odbc-date-time/datetime-data-type-conversions-from-sql-to-c.md).  
  
 Дополнительные сведения см. в разделе [время улучшения функций даты и &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlfetchscroll-support-for-large-clr-udts"></a>Поддержка функцией SQLFetchScroll больших определяемых пользователем типов CLR  
 Функция**SQLFetchScroll** поддерживает большие определяемые пользователем типы данных CLR. Дополнительные сведения см. в разделе [Large CLR User-Defined типы &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>См. также  
 [Функция SQLFetchScroll](http://go.microsoft.com/fwlink/?LinkId=59343)   
 [Подробные сведения о реализации API-интерфейсов ODBC](odbc-api-implementation-details.md)  
  
  
