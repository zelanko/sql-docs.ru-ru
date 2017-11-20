---
title: "Функция SQLGetConfigMode | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLGetConfigMode
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetConfigMode
helpviewer_keywords:
- SQLGetConfigMode function [ODBC]
ms.assetid: b96ab3b8-08d5-4fea-9ffe-e03043efbf2d
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d52a471de1590df140f766a417820126ac191f77
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="sqlgetconfigmode-function"></a>Функция SQLGetConfigMode
**Соответствия**  
 Появился в версии: ODBC 3.0  
  
 **Сводка**  
 **SQLGetConfigMode** извлекает режим конфигурации, указывающей место записи Odbc.ini со списком значений источника данных сведений о системе.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
BOOL SQLGetConfigMode(  
     UWORD *   pwConfigMode);  
```  
  
## <a name="arguments"></a>Аргументы  
 *pwConfigMode*  
 [Выход] Указатель на буфер, содержащий режим конфигурации. (В разделе «Комментарии».) Значение в  *\*pwConfigMode* может быть:  
  
 ODBC_USER_DSN  
  
 ODBC_SYSTEM_DSN  
  
 ODBC_BOTH_DSN  
  
## <a name="returns"></a>Возвращает  
 Функция возвращает значение TRUE, если он прошел успешно, FALSE в случае неудачи.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLGetConfigMode** возвращает значение FALSE, связанный с ним  *\*pfErrorCode* значение можно получить путем вызова **SQLInstallerError**. В следующей таблице перечислены  *\*pfErrorCode* значения, которые могут быть возвращены **SQLInstallerError** и описание каждого из них в контексте этой функции.  
  
|*\*pfErrorCode*|Ошибка|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_OUT_OF_MEM|Недостаточно памяти|Программе установки не удалось выполнить функцию из-за нехватки памяти.|  
  
## <a name="comments"></a>Комментарии  
 Эта функция используется для определения, где операция Odbc.ini со списком значений источника данных — сведения о системе. Если  *\*pwConfigMode* ODBC_USER_DSN, имя источника данных является пользовательское имя DSN и функция считывает из записи Odbc.ini в HKEY_CURRENT_USER. Если это ODBC_SYSTEM_DSN источника данных является системный DSN и функция считывает из записи Odbc.ini в HKEY_LOCAL_MACHINE. Если это ODBC_BOTH_DSN, предпринимается попытка HKEY_CURRENT_USER и используется в случае неудачи HKEY_LOCAL_MACHINE.  
  
 По умолчанию **SQLGetConfigMode** возвращает ODBC_BOTH_DSN. При создании DSN пользователя или системный DSN с помощью вызова **SQLConfigDataSource**, функция задает режим конфигурации ODBC_USER_DSN или ODBC_SYSTEM_DSN, чтобы различать пользователей и системных источников данных при изменении имени DSN. Перед возвратом, **SQLConfigDataSource** восстанавливает режим конфигурации ODBC_BOTH_DSN.  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Установка режима конфигурации|[SQLSetConfigMode](../../../odbc/reference/syntax/sqlsetconfigmode-function.md)|

