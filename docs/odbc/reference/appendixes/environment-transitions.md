---
title: Переходы среды | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- environment transitions [ODBC]
- transitioning states [ODBC], environment
- state transitions [ODBC], environment
ms.assetid: 9d11b1ab-f4c8-48ca-9812-8c04303f939d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3ed2bbf40ac333db34d3920b2ed2ec688c344bfe
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63188988"
---
# <a name="environment-transitions"></a>Переходы среды
ODBC среды имеют следующих трех состояний.  
  
|Штат|Описание|  
|-----------|-----------------|  
|E0|Нераспределенное среды|  
|E1|Выделенной среды, нераспределенное подключения|  
|E2|Выделенные среды, выделенные подключения|  
  
 В следующих таблицах показано, как каждая функция ODBC влияет на состояние среды.  
  
## <a name="sqlallochandle"></a>SQLAllocHandle  
  
|E0<br /><br /> Не выделено|E1<br /><br /> выделено|E2<br /><br /> Соединение|  
|------------------------|----------------------|-----------------------|  
|E1 [1]|--[4]|--[4]|  
|(IH) [2]|E2 [5]<br />(HY010) [6]|--[4]|  
|(IH) [3]|(IH)|--[4]|  
  
 [1] в этой строке показаны переходы при *HandleType* был SQL_HANDLE_ENV.  
  
 [2] в этой строке показаны переходы при *HandleType* было установленным в значение sql_handle_stmt.  
  
 [3] в этой строке показаны переходы при *HandleType* SQL_HANDLE_STMT или SQL_HANDLE_DESC.  
  
 [4] вызова **SQLAllocHandle** с *OutputHandlePtr* указывает на допустимый дескриптор перезаписывает этот дескриптор. Это может быть ошибка программирования приложений.  
  
 [5] атрибут SQL_ATTR_ODBC_VERSION среды было значение среды.  
  
 [6] атрибут SQL_ATTR_ODBC_VERSION среде не было значение среды.  
  
## <a name="sqldatasources-and-sqldrivers"></a>SQLDataSources и SQLDrivers  
  
|E0<br /><br /> Не выделено|E1<br /><br /> выделено|E2<br /><br /> Соединение|  
|------------------------|----------------------|-----------------------|  
|(IH)|--[1]<br />(HY010) [2]|--[1]<br />(HY010) [2]|  
  
 [1] атрибут SQL_ATTR_ODBC_VERSION среды было значение среды.  
  
 [2] не было значение атрибут SQL_ATTR_ODBC_VERSION среды к среде.  
  
## <a name="sqlendtran"></a>SQLEndTran  
  
|E0<br /><br /> Не выделено|E1<br /><br /> выделено|E2<br /><br /> Соединение|  
|------------------------|----------------------|-----------------------|  
|(IH) [1]|--[3]<br />(HY010) [4]|--[3]<br />(HY010) [4]|  
|(IH) [2]|(IH)|--|  
  
 [1] в этой строке показаны переходы при *HandleType* был SQL_HANDLE_ENV.  
  
 [2] в этой строке показаны переходы при *HandleType* было установленным в значение sql_handle_stmt.  
  
 [3] атрибут SQL_ATTR_ODBC_VERSION среды было значение среды.  
  
 [4] не было значение атрибут SQL_ATTR_ODBC_VERSION среды к среде.  
  
## <a name="sqlfreehandle"></a>SQLFreeHandle  
  
|E0<br /><br /> Не выделено|E1<br /><br /> выделено|E2<br /><br /> Соединение|  
|------------------------|----------------------|-----------------------|  
|(IH) [1]|E0|(HY010)|  
|(IH) [2]|(IH)|--[4]<br />E1 [5]|  
|(IH) [3]|(IH)|--|  
  
 [1] в этой строке показаны переходы при *HandleType* был SQL_HANDLE_ENV.  
  
 [2] в этой строке показаны переходы при *HandleType* было установленным в значение sql_handle_stmt.  
  
 [3] в этой строке показаны переходы при *HandleType* SQL_HANDLE_STMT или SQL_HANDLE_DESC.  
  
 [4] было других дескрипторов выделенного подключения.  
  
 [5 дескриптор подключения, указанные в *обрабатывать* был только выделенный дескриптор соединения.  
  
## <a name="sqlgetdiagfield-and-sqlgetdiagrec"></a>Функция SQLGetDiagField и SQLGetDiagRec  
  
|E0<br /><br /> Не выделено|E1<br /><br /> выделено|E2<br /><br /> Соединение|  
|------------------------|----------------------|-----------------------|  
|(IH) [1]|--|--|  
|(IH) [2]|(IH)|--|  
  
 [1] в этой строке показаны переходы при *HandleType* был SQL_HANDLE_ENV.  
  
 [2] в этой строке показаны переходы при *HandleType* SQL_HANDLE_DBC, имеющим значение SQL_HANDLE_STMT или SQL_HANDLE_DESC.  
  
## <a name="sqlgetenvattr"></a>SQLGetEnvAttr  
  
|E0<br /><br /> Не выделено|E1<br /><br /> выделено|E2<br /><br /> Соединение|  
|------------------------|----------------------|-----------------------|  
|(IH)|--[1]<br />(HY010) [2]|--|  
  
 [1] атрибут SQL_ATTR_ODBC_VERSION среды было значение среды.  
  
 [2] не было значение атрибут SQL_ATTR_ODBC_VERSION среды к среде.  
  
## <a name="sqlsetenvattr"></a>SQLSetEnvAttr  
  
|E0<br /><br /> Не выделено|E1<br /><br /> выделено|E2<br /><br /> Соединение|  
|------------------------|----------------------|-----------------------|  
|(IH)|--[1]<br />(HY010) [2]|(HY011)|  
  
 [1] атрибут SQL_ATTR_ODBC_VERSION среды было значение среды.  
  
 [2] *атрибут* аргумент не SQL_ATTR_ODBC_VERSION, и не было значение SQL_ATTR_ODBC_VERSION атрибуту окружения в среде.  
  
## <a name="all-other-odbc-functions"></a>Все остальные функции ODBC  
  
|E0<br /><br /> Не выделено|E1<br /><br /> выделено|E2<br /><br /> Соединение|  
|------------------------|----------------------|-----------------------|  
|(IH)|(IH)|--|
