---
title: Функция SQLSetConfigMode | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLSetConfigMode
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLSetConfigMode
helpviewer_keywords:
- SQLSetConfigMode function [ODBC]
ms.assetid: 09eb88ea-b6f6-4eca-b19d-0951cebc6c0a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a10ec8f8fa6ef2b0e310680f58252f98628ff045
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2018
ms.locfileid: "53215613"
---
# <a name="sqlsetconfigmode-function"></a>Функция SQLSetConfigMode
**Соответствие стандартам**  
 Представленные версии: ODBC 3.0  
  
 **Сводка**  
 **SQLSetConfigMode** задает режим конфигурации, который указывает, где запись Odbc.ini, список значений имени DSN в сведениях о системе.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
BOOL SQLSetConfigMode(  
     UWORD     wConfigMode);  
```  
  
## <a name="arguments"></a>Аргументы  
 *wConfigMode*  
 [Вход] Режим настройки установщика (см. в разделе «Комментарии»). Значение в *wConfigMode* может быть:  
  
 ODBC_USER_DSN  
  
 ODBC_SYSTEM_DSN  
  
 ODBC_BOTH_DSN  
  
## <a name="returns"></a>Возвращает  
 Функция возвращает значение TRUE при успешном выполнении, FALSE в случае неудачи.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLSetConfigMode** возвращает значение FALSE, связанным  *\*pfErrorCode* значение можно получить, вызвав **SQLInstallerError**. В следующей таблице перечислены  *\*pfErrorCode* значения, которые могут быть возвращены **SQLInstallerError** и объясняется каждый из них в контексте этой функции.  
  
|*\*pfErrorCode*|Ошибка|Описание|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_INVALID_PARAM_SEQUENCE|Недопустимый параметр последовательности|*WConfigMode* ODBC_USER_DSN, ODBC_SYSTEM_DSN или ODBC_BOTH_DSN не содержит аргументов.|  
  
## <a name="comments"></a>Комментарии  
 Эта функция используется для задания, где операция Odbc.ini, список значений имени DSN в сведениях о системе. Если *wConfigMode* ODBC_USER_DSN, имя источника данных — это пользовательское имя DSN и функция считывает из файла Odbc.ini записи в HKEY_CURRENT_USER. Если это ODBC_SYSTEM_DSN, имя источника данных является системный DSN и функция считывает из записи Odbc.ini в HKEY_LOCAL_MACHINE. Если это ODBC_BOTH_DSN следующая HKEY_CURRENT_USER и в случае, используется HKEY_LOCAL_MACHINE.  
  
 Эта функция не влияет на **SQLCreateDataSource** и **SQLDriverConnect**. Режим конфигурации должно иметь значение, драйвер считывает из реестра, вызвав **SQLGetPrivateProfileString** или записывает в реестр, вызвав **SQLWritePrivateProfileString**. Вызовы **SQLGetPrivateProfileString** и **SQLWritePrivateProfileString** использовать режим конфигурации знать, какую часть реестра для работы.  
  
> [!CAUTION]  
>  **SQLSetConfigMode** должен вызываться только при необходимости; Если неправильно установлен режим, установщик ODBC может произойти сбой надлежащего функционирования.  
  
 **SQLSetConfigMode** изменений реестра прямого режима конфигурации. Это помимо изменяет режим конфигурации с помощью вызова **SQLConfigDataSource**. Вызов **SQLConfigDataSource** задает режим для различения пользователей и системных имен DSN, при изменении имени DSN. До возвращения, **SQLConfigDataSource** BOTHDSN восстанавливает режим конфигурации.  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Создание источника данных|[SQLCreateDataSource](../../../odbc/reference/syntax/sqlcreatedatasource-function.md)|  
|Подключение к источнику данных с помощью соединения строки или в диалоговом окне|[SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)|  
|Получение режима конфигурации|[SQLGetConfigMode](../../../odbc/reference/syntax/sqlgetconfigmode-function.md)|
