---
title: Выделение дескриптора соединения ODBC | Документы Microsoft
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
- allocating connection handles [ODBC]
- data sources [ODBC], connection handles
- connecting to data source [ODBC], connection handles
- ODBC drivers [ODBC], connection handles
- connecting to driver [ODBC], connection handles
- connection handles [ODBC]
- handles [ODBC], connection
ms.assetid: c99a8159-7693-4f97-8dcf-401336550e77
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a27daadecb685a64d7c5a05e01cda05ec30dd185
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="allocating-a-connection-handle-odbc"></a>Выделение дескриптора соединения ODBC
Прежде чем приложение может подключиться к источнику данных или драйверу, оно должно выделить дескриптор соединения следующим образом:  
  
1.  Приложение объявляет переменную типа SQLHDBC. Затем он вызывает **SQLAllocHandle** и передает адрес этой переменной дескриптор средой, в которой для выделения соединения, а параметр SQL_HANDLE_DBC. Например:  
  
    ```  
    SQLHDBC hdbc1;  
  
    SQLAllocHandle(SQL_HANDLE_DBC, henv1, &hdbc1);  
    ```  
  
2.  Диспетчер драйверов выделяет структуры, в котором хранятся сведения об инструкции и возвращает дескриптор подключения в переменной.  
  
 Диспетчер драйверов не вызывает **SQLAllocHandle** в драйвере в настоящее время, так как не знает, какой драйвер для вызова. Оно задерживается вызова **SQLAllocHandle** в драйвере, пока приложение не вызовет функцию для подключения к источнику данных. Дополнительные сведения см. в разделе [роли диспетчера драйверов в процесс подключения](../../../odbc/reference/develop-app/driver-manager-s-role-in-the-connection-process.md)далее в этом разделе.  
  
 Это важно отметить, что выделение дескриптора соединения не совпадает с загрузки драйвера. Драйвер не будет загружена, пока функция подключения. Таким образом, после выделения дескриптора соединения и перед подключением к драйверу или источнику данных только функции, приложение может вызвать с дескриптором соединения являются **SQLSetConnectAttr**, **SQLGetConnectAttr**, или **SQLGetInfo** с параметром SQL_ODBC_VER. Вызов других функций с дескриптора соединения, такие как **SQLEndTran**, возвращает SQLSTATE 08003 (соединение не открыто). Дополнительные сведения см. [приложение б: ODBC состояния перехода таблицы](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md).  
  
 Дополнительные сведения о дескрипторов соединений см. в разделе [дескрипторов соединений](../../../odbc/reference/develop-app/connection-handles.md).
