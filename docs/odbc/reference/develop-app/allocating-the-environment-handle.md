---
title: Выделение дескриптора среды | Документы Microsoft
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
- ODBC drivers [ODBC], environment handles
- allocating environment handles [ODBC]
- connecting to driver [ODBC], environment handles
- environment handles [ODBC]
- data sources [ODBC], environment handles
- connecting to data source [ODBC], environment handles
- handles [ODBC], environment
ms.assetid: 77b5d1d6-7eb7-428d-bf75-a5c5a325d25c
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 23851cae822210fd13061b5e4f5de67e0c510e89
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="allocating-the-environment-handle"></a>Выделение дескриптора среды
Первая задача для любого приложения ODBC является загрузка диспетчера драйверов; как это можно сделать зависит от операционной системы. Например, на компьютере под управлением Microsoft® Windows NT® Server или Windows 2000 Server, Windows NT Workstation или Windows 2000 Professional или Microsoft Windows 95/98 приложения либо ссылки на библиотеку диспетчера драйверов или вызовы  **LoadLibrary** для загрузки библиотеки DLL диспетчера драйверов.  
  
 Следующей задачей, которая должна выполняться, прежде чем приложение может вызывать любой другой функции ODBC, является инициализировать среду ODBC и выделить дескриптор среды, как показано ниже:  
  
1.  Приложение объявляет переменную типа SQLHENV. Затем он вызывает **SQLAllocHandle** и передает адрес этой переменной и параметр SQL_HANDLE_ENV. Например:  
  
    ```  
    SQLHENV henv1;  
  
    SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &henv1);  
    ```  
  
2.  Диспетчер драйверов выделяет структуры для хранения сведений о среде и возвращает дескриптор среды в переменную.  
  
 Диспетчер драйверов не вызывает **SQLAllocHandle** в драйвере в настоящее время, так как не знает, какой драйвер для вызова. Оно задерживается вызова **SQLAllocHandle** в драйвере, пока приложение не вызовет функцию для подключения к источнику данных. Дополнительные сведения см. в разделе [роли диспетчера драйверов в процесс подключения](../../../odbc/reference/develop-app/driver-manager-s-role-in-the-connection-process.md)далее в этом разделе.  
  
 Когда приложение завершило с использованием ODBC, он освобождает дескриптор среды с **SQLFreeHandle**. После освобождения среды, это ошибка программирования приложения для использования дескриптора среды в вызове функции ODBC; Таким образом, это должна не определено, но, возможно, Неустранимая последствия.  
  
 Когда **SQLFreeHandle** вызывается версиях драйвера, структура, используемая для хранения сведений о среде. Обратите внимание, что **SQLFreeHandle** не может вызываться для дескриптора среды до после освобождения всех дескрипторов соединений на этот дескриптор среды.  
  
 Дополнительные сведения о дескриптора среды см. в разделе [обрабатывает среды](../../../odbc/reference/develop-app/environment-handles.md).
