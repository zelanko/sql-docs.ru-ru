---
description: Выделение дескриптора среды
title: Выделение маркера среды | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 390d7f4248d43e6fc6cb7910be5f42cb286f37e9
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88429456"
---
# <a name="allocating-the-environment-handle"></a>Выделение дескриптора среды
Первой задачей для любого приложения ODBC является загрузка диспетчера драйверов. как это делается, зависит от операционной системы. Например, на компьютере, работающем под управлением Microsoft® Windows NT® Server/Windows 2000 Server, Windows NT Workstation/Windows 2000 Professional или Microsoft Windows® 95/98, приложение либо ссылается на библиотеку диспетчера драйверов, либо вызывает **LoadLibrary** для загрузки библиотеки DLL диспетчера драйверов.  
  
 Следующая задача, которая должна быть выполнена до того, как приложение сможет вызвать любую другую функцию ODBC, заключается в инициализации среды ODBC и выделении обработчика среды следующим образом:  
  
1.  Приложение объявляет переменную типа СКЛХЕНВ. Затем он вызывает **функцию SQLAllocHandle** и передает адрес этой переменной и параметр SQL_HANDLE_ENV. Например:  
  
    ```  
    SQLHENV henv1;  
  
    SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &henv1);  
    ```  
  
2.  Диспетчер драйверов выделяет структуру, в которой хранятся сведения о среде, и возвращает маркер среды в переменной.  
  
 Диспетчер драйверов в настоящее время не вызывает **функцию SQLAllocHandle** в драйвере, так как не знает, какой драйвер следует вызвать. Он откладывает вызов **функцию SQLAllocHandle** в драйвере до тех пор, пока приложение не вызовет функцию для подключения к источнику данных. Дополнительные сведения см. Далее в подразделе [роль диспетчера драйверов в процессе подключения](../../../odbc/reference/develop-app/driver-manager-s-role-in-the-connection-process.md).  
  
 Когда приложение завершит работу с ODBC, оно освобождает обработчик среды с помощью **SQLFreeHandle**. После освобождения среды это ошибка программирования приложения для использования обработчика среды в вызове функции ODBC. Это не определено, но, возможно, некритические последствия.  
  
 При вызове **SQLFreeHandle** драйвер освобождает структуру, используемую для хранения сведений о среде. Обратите внимание, что **SQLFreeHandle** нельзя вызывать для дескриптора среды до тех пор, пока не будут освобождены все дескрипторы подключения в этом дескрипторе среды.  
  
 Дополнительные сведения о дескрипторе среды см. в разделе [дескрипторы среды](../../../odbc/reference/develop-app/environment-handles.md).
