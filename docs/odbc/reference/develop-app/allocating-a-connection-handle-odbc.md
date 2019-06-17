---
title: Выделение дескриптора подключения ODBC | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- allocating connection handles [ODBC]
- data sources [ODBC], connection handles
- connecting to data source [ODBC], connection handles
- ODBC drivers [ODBC], connection handles
- connecting to driver [ODBC], connection handles
- connection handles [ODBC]
- handles [ODBC], connection
ms.assetid: c99a8159-7693-4f97-8dcf-401336550e77
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 83964bf1e76eef5c7c4ba4121b0c581e8d8a406b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63288315"
---
# <a name="allocating-a-connection-handle-odbc"></a>Выделение дескриптора подключения ODBC
Прежде чем приложение сможет подключиться к источнику данных или драйверу, оно должно выделить дескриптор соединения следующим образом:  
  
1.  Приложение объявляет переменную типа SQLHDBC. Затем он вызывает **SQLAllocHandle** и передает адрес этой переменной, дескриптор среды распределения подключение, а параметр установленным в значение sql_handle_stmt. Пример:  
  
    ```  
    SQLHDBC hdbc1;  
  
    SQLAllocHandle(SQL_HANDLE_DBC, henv1, &hdbc1);  
    ```  
  
2.  Диспетчер драйверов выделяет структуру, в котором хранятся сведения об инструкции и возвращает дескриптор подключения в переменной.  
  
 Диспетчер драйверов не вызывает **SQLAllocHandle** в драйвере в это время, так как он не знает, какой драйвер следует вызывать. Она задерживает вызов **SQLAllocHandle** в драйвере, пока приложение не вызовет функцию для подключения к источнику данных. Дополнительные сведения см. в разделе [роль диспетчера драйверов в процессе подключения](../../../odbc/reference/develop-app/driver-manager-s-role-in-the-connection-process.md)далее в этом разделе.  
  
 Важно отметить, что выделение дескриптора соединения не так же, как загрузка драйвера. Пока не вызывается функция подключения не загружен драйвер. Таким образом, после выделения дескриптора соединения и перед подключением к драйверу или источнику данных, только функции, приложение может вызвать с дескриптором соединения являются **SQLSetConnectAttr**, **SQLGetConnectAttr**, или **SQLGetInfo** с параметром SQL_ODBC_VER. Вызова других функций с дескриптором соединения, таких как **SQLEndTran**, возвращает SQLSTATE 08003 (соединение не открыто). Дополнительные сведения см. в разделе [приложении б: Таблицы перехода состояния ODBC](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md).  
  
 Дополнительные сведения о дескрипторов соединений, см. в разделе [дескрипторов соединений](../../../odbc/reference/develop-app/connection-handles.md).
