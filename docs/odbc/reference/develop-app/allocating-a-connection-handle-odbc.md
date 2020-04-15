---
title: Выделение ручки соединения ODBC (ru) Документы Майкрософт
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81288524"
---
# <a name="allocating-a-connection-handle-odbc"></a>Выделение дескриптора подключения ODBC
Прежде чем приложение может подключиться к источнику данных или драйверу, оно должно выделить ручку соединения следующим образом:  
  
1.  Приложение объявляет переменную типа S'LHDBC. Затем он вызывает **s'LAllocHandle** и передает адрес этой переменной, ручку среды, в которой можно выделить соединение, и SQL_HANDLE_DBC опцию. Пример:  
  
    ```  
    SQLHDBC hdbc1;  
  
    SQLAllocHandle(SQL_HANDLE_DBC, henv1, &hdbc1);  
    ```  
  
2.  Менеджер драйвера выделяет структуру, в которой для хранения информации об отчете и возвращает ручку соединения в переменной.  
  
 В настоящее время менеджер драйвера не вызывает вызов в **драйвере,** так как не знает, какой драйвер звонить. Он задерживает вызов **s'LAllocHandle** в драйвере до тех пор, пока приложение не вызывает функцию для подключения к источнику данных. Для получения дополнительной информации см. [Роль менеджера драйвера в процессе подключения,](../../../odbc/reference/develop-app/driver-manager-s-role-in-the-connection-process.md)позже в этом разделе.  
  
 Важно отметить, что выделение ручки соединения не то же самое, что загрузка драйвера. Драйвер не загружается до вызова функции соединения. Таким образом, после выделения ручки соединения и перед подключением к драйверу или источнику данных, единственными функциями, которые приложение может вызвать с ручкой соединения, являются **S'LSetConnectAttr,** **S'LGetConnectAttr**, или **S'LGetInfo** с SQL_ODBC_VER опцией. Вызов других функций с ручкой соединения, таких как **S'LEndTran**, возвращает S'LSTATE 08003 (Соединение не открывается). Для получения подробной информации [см.](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md)  
  
 Для получения дополнительной информации [Connection Handles](../../../odbc/reference/develop-app/connection-handles.md)о ручках соединения см.
