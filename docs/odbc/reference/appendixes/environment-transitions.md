---
title: Переходы к окружающей среде Документы Майкрософт
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
ms.openlocfilehash: ebfb5475d24d5fc70c4cb46a666b2573066565a1
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81283304"
---
# <a name="environment-transitions"></a>Переходы среды
Среды ODBC имеют следующие три состояния.  
  
|Состояние|Описание|  
|-----------|-----------------|  
|E0|Нераспределенная среда|  
|E1|Выделенная среда, нераспределенное соединение|  
|E2|Выделенная среда, выделенное соединение|  
  
 Следующие таблицы показывают, как каждая функция ODBC влияет на состояние среды.  
  
## <a name="sqlallochandle"></a>СЗЛАллокХэндл  
  
|E0<br /><br /> Не выделено|E1<br /><br /> Allocated|E2<br /><br /> Соединение|  
|------------------------|----------------------|-----------------------|  
|E1|--[4]|--[4]|  
|(IH) [2]|E2<br />(HY010) [6]|--[4]|  
|(IH) [3]|(IH)|--[4]|  
  
 В этой строке показаны переходы, когда *HandleType* был SQL_HANDLE_ENV.  
  
 В этой строке показаны переходы, когда *HandleType* был SQL_HANDLE_DBC.  
  
 В этой строке показаны переходы, когда *HandleType* был SQL_HANDLE_STMT или SQL_HANDLE_DESC.  
  
 Вызов **S'LAllocHandle** с *помощью OutputHandlePtr,* указывающий на действительную ручку, перезаписывает эту ручку. Это может быть ошибка программирования приложений.  
  
 Атрибут SQL_ATTR_ODBC_VERSION среды был установлен на окружающую среду.  
  
 Атрибут SQL_ATTR_ODBC_VERSION среды не был установлен на окружающую среду.  
  
## <a name="sqldatasources-and-sqldrivers"></a>СЗЛДатаИсточники и S'LDrivers  
  
|E0<br /><br /> Не выделено|E1<br /><br /> Allocated|E2<br /><br /> Соединение|  
|------------------------|----------------------|-----------------------|  
|(IH)|--[1]<br />(HY010) [2]|--[1]<br />(HY010) [2]|  
  
 Атрибут SQL_ATTR_ODBC_VERSION среды был установлен на окружающую среду.  
  
 Атрибут SQL_ATTR_ODBC_VERSION среды не был установлен на окружающую среду.  
  
## <a name="sqlendtran"></a>SQLEndTran  
  
|E0<br /><br /> Не выделено|E1<br /><br /> Allocated|E2<br /><br /> Соединение|  
|------------------------|----------------------|-----------------------|  
|(IH) [1]|--[3]<br />(HY010) [4]|--[3]<br />(HY010) [4]|  
|(IH) [2]|(IH)|--|  
  
 В этой строке показаны переходы, когда *HandleType* был SQL_HANDLE_ENV.  
  
 В этой строке показаны переходы, когда *HandleType* был SQL_HANDLE_DBC.  
  
 Атрибут SQL_ATTR_ODBC_VERSION среды был установлен на окружающую среду.  
  
 Атрибут SQL_ATTR_ODBC_VERSION среды не был установлен на окружающую среду.  
  
## <a name="sqlfreehandle"></a>SQLFreeHandle  
  
|E0<br /><br /> Не выделено|E1<br /><br /> Allocated|E2<br /><br /> Соединение|  
|------------------------|----------------------|-----------------------|  
|(IH) [1]|E0|(HY010)|  
|(IH) [2]|(IH)|--[4]<br />Е1|  
|(IH) [3]|(IH)|--|  
  
 В этой строке показаны переходы, когда *HandleType* был SQL_HANDLE_ENV.  
  
 В этой строке показаны переходы, когда *HandleType* был SQL_HANDLE_DBC.  
  
 В этой строке показаны переходы, когда *HandleType* был SQL_HANDLE_STMT или SQL_HANDLE_DESC.  
  
 Были и другие выделенные ручки соединения.  
  
 Ручка соединения, указанная в *Handle,* была единственной выделенной ручкой соединения.  
  
## <a name="sqlgetdiagfield-and-sqlgetdiagrec"></a>СЗЛГетДиагФилд и СЗЛГетДиагРе  
  
|E0<br /><br /> Не выделено|E1<br /><br /> Allocated|E2<br /><br /> Соединение|  
|------------------------|----------------------|-----------------------|  
|(IH) [1]|--|--|  
|(IH) [2]|(IH)|--|  
  
 В этой строке показаны переходы, когда *HandleType* был SQL_HANDLE_ENV.  
  
 В этой строке показаны переходы, когда *HandleType* был SQL_HANDLE_DBC, SQL_HANDLE_STMT или SQL_HANDLE_DESC.  
  
## <a name="sqlgetenvattr"></a>СЗЛГетЕнвТтр  
  
|E0<br /><br /> Не выделено|E1<br /><br /> Allocated|E2<br /><br /> Соединение|  
|------------------------|----------------------|-----------------------|  
|(IH)|--[1]<br />(HY010) [2]|--|  
  
 Атрибут SQL_ATTR_ODBC_VERSION среды был установлен на окружающую среду.  
  
 Атрибут SQL_ATTR_ODBC_VERSION среды не был установлен на окружающую среду.  
  
## <a name="sqlsetenvattr"></a>SQLSetEnvAttr  
  
|E0<br /><br /> Не выделено|E1<br /><br /> Allocated|E2<br /><br /> Соединение|  
|------------------------|----------------------|-----------------------|  
|(IH)|--[1]<br />(HY010) [2]|(HY011)|  
  
 Атрибут SQL_ATTR_ODBC_VERSION среды был установлен на окружающую среду.  
  
 Аргумент *Attribute* не был SQL_ATTR_ODBC_VERSION, а атрибут SQL_ATTR_ODBC_VERSION среды не был установлен на окружающую среду.  
  
## <a name="all-other-odbc-functions"></a>Все остальные функции ODBC  
  
|E0<br /><br /> Не выделено|E1<br /><br /> Allocated|E2<br /><br /> Соединение|  
|------------------------|----------------------|-----------------------|  
|(IH)|(IH)|--|
