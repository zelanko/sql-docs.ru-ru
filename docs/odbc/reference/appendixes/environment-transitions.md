---
title: "Среда переходит | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- environment transitions [ODBC]
- transitioning states [ODBC], environment
- state transitions [ODBC], environment
ms.assetid: 9d11b1ab-f4c8-48ca-9812-8c04303f939d
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1a47acf216ef707600fad3fd28a8d94603052be6
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="environment-transitions"></a>Среда переходит
Для сред ODBC существует три состояния.  
  
|Состояние|Description|  
|-----------|-----------------|  
|E0|Незанятое среды|  
|E1|Выделенный среды, нераспределенное подключения|  
|E2|Выделенные среды, выделенных соединений|  
  
 В следующих таблицах показано, как каждая функция ODBC влияет на состояние среды.  
  
## <a name="sqlallochandle"></a>SQLAllocHandle  
  
|E0<br /><br /> Не выделено|E1<br /><br /> Выделенные|E2<br /><br /> Соединение|  
|------------------------|----------------------|-----------------------|  
|E1 [1]|--[4]|--[4]|  
|(СИСТЕМЫ) [2]|E2 [5]<br />(HY010) [6]|--[4]|  
|(СИСТЕМЫ) [3]|(СИСТЕМЫ)|--[4]|  
  
 [1] в этой строке показаны переходы при *HandleType* был SQL_HANDLE_ENV.  
  
 [2] в этой строке показаны переходы при *HandleType* был SQL_HANDLE_DBC.  
  
 [3] в этой строке показаны переходы при *HandleType* значение SQL_HANDLE_STMT или SQL_HANDLE_DESC.  
  
 [4] вызова **SQLAllocHandle** с *OutputHandlePtr* указывает допустимый дескриптор перезаписывает этот дескриптор. Это может быть ошибка программирования приложений.  
  
 [5] атрибут SQL_ATTR_ODBC_VERSION среды ранее было задано в среде.  
  
 [6] атрибута среды SQL_ATTR_ODBC_VERSION среды не задано.  
  
## <a name="sqldatasources-and-sqldrivers"></a>SQLDataSources и SQLDrivers  
  
|E0<br /><br /> Не выделено|E1<br /><br /> Выделенные|E2<br /><br /> Соединение|  
|------------------------|----------------------|-----------------------|  
|(СИСТЕМЫ)|--[1]<br />(HY010) [2]|--[1]<br />(HY010) [2]|  
  
 [1] атрибута среды SQL_ATTR_ODBC_VERSION ранее было задано в среде.  
  
 [2] атрибута среды SQL_ATTR_ODBC_VERSION не задано в среде.  
  
## <a name="sqlendtran"></a>SQLEndTran  
  
|E0<br /><br /> Не выделено|E1<br /><br /> Выделенные|E2<br /><br /> Соединение|  
|------------------------|----------------------|-----------------------|  
|(СИСТЕМЫ) [1]|--[3]<br />(HY010) [4]|--[3]<br />(HY010) [4]|  
|(СИСТЕМЫ) [2]|(СИСТЕМЫ)|--|  
  
 [1] в этой строке показаны переходы при *HandleType* был SQL_HANDLE_ENV.  
  
 [2] в этой строке показаны переходы при *HandleType* был SQL_HANDLE_DBC.  
  
 [3] атрибута среды SQL_ATTR_ODBC_VERSION ранее было задано в среде.  
  
 [4] атрибута среды SQL_ATTR_ODBC_VERSION среды не задано.  
  
## <a name="sqlfreehandle"></a>SQLFreeHandle  
  
|E0<br /><br /> Не выделено|E1<br /><br /> Выделенные|E2<br /><br /> Соединение|  
|------------------------|----------------------|-----------------------|  
|(СИСТЕМЫ) [1]|E0|(HY010)|  
|(СИСТЕМЫ) [2]|(СИСТЕМЫ)|--[4]<br />E1 [5]|  
|(СИСТЕМЫ) [3]|(СИСТЕМЫ)|--|  
  
 [1] в этой строке показаны переходы при *HandleType* был SQL_HANDLE_ENV.  
  
 [2] в этой строке показаны переходы при *HandleType* был SQL_HANDLE_DBC.  
  
 [3] в этой строке показаны переходы при *HandleType* значение SQL_HANDLE_STMT или SQL_HANDLE_DESC.  
  
 [4] были других дескрипторах выделенного соединения.  
  
 [5 дескриптор подключения, указанные в *обработки* был только выделенный дескриптор соединения.  
  
## <a name="sqlgetdiagfield-and-sqlgetdiagrec"></a>Функция SQLGetDiagField и SQLGetDiagRec  
  
|E0<br /><br /> Не выделено|E1<br /><br /> Выделенные|E2<br /><br /> Соединение|  
|------------------------|----------------------|-----------------------|  
|(СИСТЕМЫ) [1]|--|--|  
|(СИСТЕМЫ) [2]|(СИСТЕМЫ)|--|  
  
 [1] в этой строке показаны переходы при *HandleType* был SQL_HANDLE_ENV.  
  
 [2] в этой строке показаны переходы при *HandleType* SQL_HANDLE_DBC, значение SQL_HANDLE_STMT или SQL_HANDLE_DESC.  
  
## <a name="sqlgetenvattr"></a>SQLGetEnvAttr  
  
|E0<br /><br /> Не выделено|E1<br /><br /> Выделенные|E2<br /><br /> Соединение|  
|------------------------|----------------------|-----------------------|  
|(СИСТЕМЫ)|--[1]<br />(HY010) [2]|--|  
  
 [1] атрибута среды SQL_ATTR_ODBC_VERSION ранее было задано в среде.  
  
 [2] атрибута среды SQL_ATTR_ODBC_VERSION не задано в среде.  
  
## <a name="sqlsetenvattr"></a>SQLSetEnvAttr  
  
|E0<br /><br /> Не выделено|E1<br /><br /> Выделенные|E2<br /><br /> Соединение|  
|------------------------|----------------------|-----------------------|  
|(СИСТЕМЫ)|--[1]<br />(HY010) [2]|(HY011)|  
  
 [1] атрибута среды SQL_ATTR_ODBC_VERSION ранее было задано в среде.  
  
 [2] *атрибута* аргумент не SQL_ATTR_ODBC_VERSION, и атрибут SQL_ATTR_ODBC_VERSION окружения не ранее было задано в среде.  
  
## <a name="all-other-odbc-functions"></a>Все остальные функции ODBC  
  
|E0<br /><br /> Не выделено|E1<br /><br /> Выделенные|E2<br /><br /> Соединение|  
|------------------------|----------------------|-----------------------|  
|(СИСТЕМЫ)|(СИСТЕМЫ)|--|
