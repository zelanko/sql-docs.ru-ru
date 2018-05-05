---
title: Выделение дескриптора инструкции ODBC | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], statement handles
- statement handles [ODBC]
- allocating statement handles [ODBC]
- handles [ODBC], statement
ms.assetid: 4ce3b446-34ab-46dc-96e5-f40ec95c267e
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: faef5961418634f36f69a0f940e59c3e3b2b16cd
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
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
