---
title: Выделение дескриптора среды | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7a8eefe5bc6678462099afda8381d6b16bd076dd
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47602982"
---
# <a name="allocating-the-environment-handle"></a>Выделение дескриптора среды
Первая задача для любого приложения ODBC является загрузка диспетчера драйверов; как это можно сделать зависит от операционной системы. Например, на компьютере под управлением Microsoft® Windows NT® Server и Windows 2000 Server, Windows NT Workstation и Windows 2000 Professional или Microsoft Windows® 95/98, либо ссылается приложение библиотеки диспетчера драйверов или вызовы  **LoadLibrary** загрузить библиотеку DLL диспетчера драйверов.  
  
 Следующая задача, что должно быть выполнено, прежде чем приложение может вызвать любой другой функции ODBC, — инициализировать среду ODBC и выделить дескриптор среды следующим образом:  
  
1.  Приложение объявляет переменную типа SQLHENV. Затем он вызывает **SQLAllocHandle** и передает адрес этой переменной и параметр SQL_HANDLE_ENV. Пример:  
  
    ```  
    SQLHENV henv1;  
  
    SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &henv1);  
    ```  
  
2.  Диспетчер драйверов выделяет структуру для хранения сведений о среде и возвращает дескриптор среды в переменной.  
  
 Диспетчер драйверов не вызывает **SQLAllocHandle** в драйвере в это время, так как он не знает, какой драйвер следует вызывать. Она задерживает вызов **SQLAllocHandle** в драйвере, пока приложение не вызовет функцию для подключения к источнику данных. Дополнительные сведения см. в разделе [роль диспетчера драйверов в процессе подключения](../../../odbc/reference/develop-app/driver-manager-s-role-in-the-connection-process.md)далее в этом разделе.  
  
 Когда приложение завершило использование ODBC, он освобождает дескриптор среды с **SQLFreeHandle**. После освобождения среды, это ошибка программирования приложения для использования дескриптора среды в вызове функции ODBC; имеет неопределенный, но, возможно, Неустранимая последствия.  
  
 Когда **SQLFreeHandle** вызывается выпуски драйверов, структуры, используемый для хранения сведений о среде. Обратите внимание, что **SQLFreeHandle** не может вызываться для дескриптора среды до, после освобождения всех дескрипторов соединений на этот дескриптор среды.  
  
 Дополнительные сведения о дескриптора среды, см. в разделе [эти задачи выполняет среда](../../../odbc/reference/develop-app/environment-handles.md).
