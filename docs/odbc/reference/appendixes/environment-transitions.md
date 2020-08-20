---
description: Переходы среды
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4cb4366a044f42440eb70934b9f853947e4f3224
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88466234"
---
# <a name="environment-transitions"></a>Переходы среды
Среды ODBC имеют следующие три состояния.  
  
|Состояние|Описание|  
|-----------|-----------------|  
|E0|Нераспределенная среда|  
|E1|Выделенная среда, нераспределенное подключение|  
|E2|Выделенная среда, выделенное соединение|  
  
 В следующих таблицах показано, как каждая функция ODBC влияет на состояние среды.  
  
## <a name="sqlallochandle"></a>Функцию SQLAllocHandle  
  
|E0<br /><br /> Не выделено|E1<br /><br /> Allocated|E2<br /><br /> Соединение|  
|------------------------|----------------------|-----------------------|  
|E1 [1]|--[4]|--[4]|  
|IH открыт|E2 [5]<br />(HY010) 1-6|--[4]|  
|IH 3-5|IH|--[4]|  
  
 [1] в этой строке отображаются переходы, когда *параметром handletype* был SQL_HANDLE_ENV.  
  
 [2] в этой строке отображаются переходы, когда *параметром handletype* был SQL_HANDLE_DBC.  
  
 [3] в этой строке отображаются переходы, если *параметром handletype* был SQL_HANDLE_STMT или SQL_HANDLE_DESC.  
  
 [4] вызов **функцию SQLAllocHandle** с *аутпусандлептр* , указывающим на допустимый обработчик, перезаписывает этот обработчик. Это может быть ошибка программирования приложения.  
  
 [5] в среде было задано значение атрибута среды SQL_ATTR_ODBC_VERSION.  
  
 [6] в среде не был задан атрибут среды SQL_ATTR_ODBC_VERSION.  
  
## <a name="sqldatasources-and-sqldrivers"></a>SQLDataSources и SQLDrivers  
  
|E0<br /><br /> Не выделено|E1<br /><br /> Allocated|E2<br /><br /> Соединение|  
|------------------------|----------------------|-----------------------|  
|IH|--[1]<br />(HY010) открыт|--[1]<br />(HY010) открыт|  
  
 [1] в среде было задано значение атрибута среды SQL_ATTR_ODBC_VERSION.  
  
 [2] для окружения не был задан атрибут среды SQL_ATTR_ODBC_VERSION.  
  
## <a name="sqlendtran"></a>SQLEndTran  
  
|E0<br /><br /> Не выделено|E1<br /><br /> Allocated|E2<br /><br /> Соединение|  
|------------------------|----------------------|-----------------------|  
|IH одного|--[3]<br />(HY010) четырех|--[3]<br />(HY010) четырех|  
|IH открыт|IH|--|  
  
 [1] в этой строке отображаются переходы, когда *параметром handletype* был SQL_HANDLE_ENV.  
  
 [2] в этой строке отображаются переходы, когда *параметром handletype* был SQL_HANDLE_DBC.  
  
 [3] в среде было задано значение атрибута среды SQL_ATTR_ODBC_VERSION.  
  
 [4] для окружения не был задан атрибут среды SQL_ATTR_ODBC_VERSION.  
  
## <a name="sqlfreehandle"></a>SQLFreeHandle  
  
|E0<br /><br /> Не выделено|E1<br /><br /> Allocated|E2<br /><br /> Соединение|  
|------------------------|----------------------|-----------------------|  
|IH одного|E0|(HY010)|  
|IH открыт|IH|--[4]<br />E1 [5]|  
|IH 3-5|IH|--|  
  
 [1] в этой строке отображаются переходы, когда *параметром handletype* был SQL_HANDLE_ENV.  
  
 [2] в этой строке отображаются переходы, когда *параметром handletype* был SQL_HANDLE_DBC.  
  
 [3] в этой строке отображаются переходы, если *параметром handletype* был SQL_HANDLE_STMT или SQL_HANDLE_DESC.  
  
 [4] существуют другие выделенные дескрипторы подключений.  
  
 [5] маркер подключения, указанный в *Handle* , является единственным выделенным маркером подключения.  
  
## <a name="sqlgetdiagfield-and-sqlgetdiagrec"></a>SQLGetDiagField и SQLGetDiagRec  
  
|E0<br /><br /> Не выделено|E1<br /><br /> Allocated|E2<br /><br /> Соединение|  
|------------------------|----------------------|-----------------------|  
|IH одного|--|--|  
|IH открыт|IH|--|  
  
 [1] в этой строке отображаются переходы, когда *параметром handletype* был SQL_HANDLE_ENV.  
  
 [2] в этой строке отображаются переходы, когда *параметром handletype* был SQL_HANDLE_DBC, SQL_HANDLE_STMT или SQL_HANDLE_DESC.  
  
## <a name="sqlgetenvattr"></a>SQLGetEnvAttr  
  
|E0<br /><br /> Не выделено|E1<br /><br /> Allocated|E2<br /><br /> Соединение|  
|------------------------|----------------------|-----------------------|  
|IH|--[1]<br />(HY010) открыт|--|  
  
 [1] в среде было задано значение атрибута среды SQL_ATTR_ODBC_VERSION.  
  
 [2] для окружения не был задан атрибут среды SQL_ATTR_ODBC_VERSION.  
  
## <a name="sqlsetenvattr"></a>SQLSetEnvAttr  
  
|E0<br /><br /> Не выделено|E1<br /><br /> Allocated|E2<br /><br /> Соединение|  
|------------------------|----------------------|-----------------------|  
|IH|--[1]<br />(HY010) открыт|(HY011)|  
  
 [1] в среде было задано значение атрибута среды SQL_ATTR_ODBC_VERSION.  
  
 [2] аргумент *атрибута* не SQL_ATTR_ODBC_VERSION, а атрибут среды SQL_ATTR_ODBC_VERSION не был задан в окружении.  
  
## <a name="all-other-odbc-functions"></a>Все остальные функции ODBC  
  
|E0<br /><br /> Не выделено|E1<br /><br /> Allocated|E2<br /><br /> Соединение|  
|------------------------|----------------------|-----------------------|  
|IH|IH|--|
