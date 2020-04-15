---
title: Распределение окружающей среды Ручка (ru) Документы Майкрософт
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
ms.openlocfilehash: e33b850b2786960a368720deaf89a2203c7dd159
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303007"
---
# <a name="allocating-the-environment-handle"></a>Выделение дескриптора среды
Первая задача для любого приложения ODBC заключается в загрузке менеджера драйвера; как это делается, зависит операционная система. Например, на компьютере под управлением Microsoft® Windows NT® Server/Windows 2000 Server, Windows NT Workstation/Windows 2000 Professional или Microsoft Windows® 95/98, приложение либо ссылается на библиотеку диспетчера драйверов, либо вызывает **LoadLibrary** для загрузки DLL менеджера драйверов.  
  
 Следующая задача, которая должна быть выполнена до того, как приложение может вызвать любую другую функцию ODBC, состоит в том, чтобы инициализировать среду ODBC и выделить ручку среды следующим образом:  
  
1.  Приложение объявляет переменную типа S'LHENV. Затем он вызывает **S'LAllocHandle** и передает адрес этой переменной и SQL_HANDLE_ENV опцию. Пример:  
  
    ```  
    SQLHENV henv1;  
  
    SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &henv1);  
    ```  
  
2.  Менеджер драйвера выделяет структуру, в которой для хранения информации об окружающей среде, и возвращает обработку среды в переменной.  
  
 В настоящее время менеджер драйвера не вызывает вызов в **драйвере,** так как не знает, какой драйвер звонить. Он задерживает вызов **s'LAllocHandle** в драйвере до тех пор, пока приложение не вызывает функцию для подключения к источнику данных. Для получения дополнительной информации см. [Роль менеджера драйвера в процессе подключения,](../../../odbc/reference/develop-app/driver-manager-s-role-in-the-connection-process.md)позже в этом разделе.  
  
 Когда приложение закончило использовать ODBC, оно освобождает обработку среды с **помощью S'LFreeHandle.** После освобождения среды ошибка программирования приложений — использование ручки среды при вызове к функции ODBC; это имеет неопределенные, но, вероятно, фатальные последствия.  
  
 При вызове **S'LFreeHandle** драйвер выпускает структуру, используемую для хранения информации об окружающей среде. Обратите внимание, что **S'LFreeHandle** не может быть вызван для обработки среды до тех пор, пока не будут освобождены все ручки соединения на этой ручке среды.  
  
 Для получения дополнительной информации о обработке [среды](../../../odbc/reference/develop-app/environment-handles.md)см.
