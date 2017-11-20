---
title: "Выделение дескриптора инструкции ODBC | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL statements [ODBC], statement handles
- statement handles [ODBC]
- allocating statement handles [ODBC]
- handles [ODBC], statement
ms.assetid: 4ce3b446-34ab-46dc-96e5-f40ec95c267e
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: a96868755475c6fd72b2dd977375fbe0d88c22df
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="allocating-a-statement-handle-odbc"></a>Выделение дескриптора инструкции ODBC
Прежде чем приложение сможет выполнить инструкцию, оно должно выделить дескриптор инструкции следующим образом:  
  
1.  Приложение объявляет переменную типа HSTMT. Затем он вызывает **SQLAllocHandle** и передает адрес этой переменной дескриптор подключения, в котором для распределения инструкцию, а параметр значение SQL_HANDLE_STMT. Например:  
  
    ```  
    SQLHSTMT hstmt1;  
  
    SQLAllocHandle(SQL_HANDLE_STMT, hdbc1, &hstmt1);  
    ```  
  
2.  Диспетчер драйверов выделяет структуры, в котором хранятся сведения об инструкции и вызовы **SQLAllocHandle** в драйвере с параметром значение SQL_HANDLE_STMT.  
  
3.  Драйвер выделяет отдельную структуру, в котором хранятся сведения об инструкции и возвращает дескриптор инструкции драйвер диспетчера драйверов.  
  
4.  Диспетчер драйверов возвращает дескриптор инструкции диспетчера драйверов к приложению в переменную приложения.  
  
 Дескриптор инструкции определяет, какие инструкции для использования при вызове функций ODBC. Дополнительные сведения о дескрипторах инструкции см. в разделе [дескрипторов инструкций](../../../odbc/reference/develop-app/statement-handles.md).

