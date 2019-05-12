---
title: Функция SQLGetConfigMode | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7d9065d48e8b4af686e1ff64272fbe902e066cb6
ms.sourcegitcommit: 7a3243c45830cb3f49a7fa71c2991a9454fd6f5a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/11/2019
ms.locfileid: "65537273"
---
# <a name="sqlgetconfigmode-function"></a>Функция SQLGetConfigMode
**Соответствие стандартам**  
 Представленные версии: ODBC 3.0  
  
 **Сводка**  
 **SQLGetConfigMode** извлекает режим конфигурации, указывающее, где операция Odbc.ini, список значений имени DSN в сведениях о системе.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
  
BOOL SQLGetConfigMode(  
     UWORD *   pwConfigMode);  
```  
  
## <a name="arguments"></a>Аргументы  
 *pwConfigMode*  
 [Выход] Указатель на буфер, содержащий режим конфигурации. (См. в разделе «Комментарии».) Значение в  *\*pwConfigMode* может быть:  
  
 ODBC_USER_DSN  
  
 ODBC_SYSTEM_DSN  
  
 ODBC_BOTH_DSN  
  
## <a name="returns"></a>Возвращает  
 Функция возвращает значение TRUE при успешном выполнении, FALSE в случае неудачи.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLGetConfigMode** возвращает значение FALSE, связанным  *\*pfErrorCode* значение можно получить, вызвав **SQLInstallerError**. В следующей таблице перечислены  *\*pfErrorCode* значения, которые могут быть возвращены **SQLInstallerError** и объясняется каждый из них в контексте этой функции.  
  
|*\*pfErrorCode*|Ошибка|Описание|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_OUT_OF_MEM|Недостаточно памяти|Программа установки не удалось выполнить функцию из-за нехватки памяти.|  
  
## <a name="comments"></a>Комментарии  
 Эта функция используется для определения, где операция Odbc.ini, список значений имени DSN в сведениях о системе. Если  *\*pwConfigMode* ODBC_USER_DSN, имя источника данных — это пользовательское имя DSN и функция считывает из файла Odbc.ini записи в HKEY_CURRENT_USER. Если это ODBC_SYSTEM_DSN, имя источника данных является системный DSN и функция считывает из записи Odbc.ini в HKEY_LOCAL_MACHINE. Если это ODBC_BOTH_DSN следующая HKEY_CURRENT_USER и в случае неудачи HKEY_LOCAL_MACHINE используется.  
  
 По умолчанию **SQLGetConfigMode** возвращает ODBC_BOTH_DSN. При создании имени DSN пользователя или системный DSN с помощью вызова **SQLConfigDataSource**, функция задает режим конфигурации ODBC_USER_DSN или ODBC_SYSTEM_DSN для различения пользователей и системных имен DSN при изменении имени DSN. До возвращения, **SQLConfigDataSource** ODBC_BOTH_DSN восстанавливает режим конфигурации.  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Настройка режима конфигурации|[SQLSetConfigMode](../../../odbc/reference/syntax/sqlsetconfigmode-function.md)|
