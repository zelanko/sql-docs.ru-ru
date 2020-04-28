---
title: Выделение памяти для обработчика соединений ODBC | Документация Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 12e9f65ee81612e269c1f86ebabd049588443cb8
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81288524"
---
# <a name="allocating-a-connection-handle-odbc"></a>Выделение дескриптора подключения ODBC
Прежде чем приложение сможет подключиться к источнику данных или драйверу, оно должно выделить маркер подключения следующим образом:  
  
1.  Приложение объявляет переменную типа СКЛХДБК. Затем он вызывает **функцию SQLAllocHandle** и передает адрес этой переменной, маркер среды, в которой выделяется соединение, и параметр SQL_HANDLE_DBC. Пример:  
  
    ```  
    SQLHDBC hdbc1;  
  
    SQLAllocHandle(SQL_HANDLE_DBC, henv1, &hdbc1);  
    ```  
  
2.  Диспетчер драйверов выделяет структуру, в которой хранятся сведения об инструкции, и возвращает маркер соединения в переменной.  
  
 Диспетчер драйверов в настоящее время не вызывает **функцию SQLAllocHandle** в драйвере, так как не знает, какой драйвер следует вызвать. Он откладывает вызов **функцию SQLAllocHandle** в драйвере до тех пор, пока приложение не вызовет функцию для подключения к источнику данных. Дополнительные сведения см. Далее в подразделе [роль диспетчера драйверов в процессе подключения](../../../odbc/reference/develop-app/driver-manager-s-role-in-the-connection-process.md).  
  
 Важно отметить, что выделение маркера соединения не совпадает с загрузкой драйвера. Драйвер не загружается, пока не будет вызвана функция подключения. Поэтому после выделения маркера соединения и перед подключением к драйверу или источнику данных единственные функции, которые приложение может вызвать с помощью этого обработчика соединения, — это **SQLSetConnectAttr**, **SQLGetConnectAttr**или **SQLGetInfo** с параметром SQL_ODBC_VER. Вызов других функций с помощью маркера соединения, например **SQLEndTran**, ВОЗВРАЩАЕТ значение SQLSTATE 08003 (соединение не открыто). Подробные сведения см. в [приложении б: таблицы переходов состояния ODBC](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md).  
  
 Дополнительные сведения о дескрипторах подключений см. в разделе [Handles Connections](../../../odbc/reference/develop-app/connection-handles.md).
