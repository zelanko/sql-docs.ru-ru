---
description: Функция SQLSetConfigMode
title: Функция Склсетконфигмоде | Документация Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5aab5274403a654362c5732d8ec3f6eccae3be96
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88499587"
---
# <a name="sqlsetconfigmode-function"></a>Функция SQLSetConfigMode
**Соответствия**  
 Введенная версия: ODBC 3,0  
  
 **Сводка**  
 **Склсетконфигмоде** задает режим конфигурации, указывающий, где в сведениях о системе отображается запись Odbc.ini с перечнем значений DSN.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
  
BOOL SQLSetConfigMode(  
     UWORD     wConfigMode);  
```  
  
## <a name="arguments"></a>Аргументы  
 *вконфигмоде*  
 Входной Режим конфигурации установщика (см. раздел "Комментарии"). Значение в *вконфигмоде* может быть следующим:  
  
 ODBC_USER_DSN  
  
 ODBC_SYSTEM_DSN  
  
 ODBC_BOTH_DSN  
  
## <a name="returns"></a>Возвращаемое значение  
 Функция возвращает TRUE, если она успешна, и FALSE в случае сбоя.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **склсетконфигмоде** возвращает значение false, связанное значение * \* пферроркоде* может быть получено путем вызова **склинсталлереррор**. В следующей таблице перечислены значения * \* пферроркоде* , которые могут быть возвращены **склинсталлереррор** , и объясняется каждый из них в контексте этой функции.  
  
|*\*пферроркоде*|Ошибка|Описание|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_INVALID_PARAM_SEQUENCE|Недопустимая последовательность параметров|Аргумент *вконфигмоде* не содержит ODBC_USER_DSN, ODBC_SYSTEM_DSN или ODBC_BOTH_DSN.|  
  
## <a name="comments"></a>Комментарии  
 Эта функция используется, чтобы задать расположение записи Odbc.ini, в которой перечислены значения DSN, в системной информации. Если *вконфигмоде* имеет значение ODBC_USER_DSN, то DSN является ПОЛЬЗОВАТЕЛЬСКИМ именем DSN, а функция считывает из записи Odbc.ini в HKEY_CURRENT_USER. Если это ODBC_SYSTEM_DSN, то DSN является системным именем DSN, а функция считывает из записи Odbc.ini в HKEY_LOCAL_MACHINE. Если это ODBC_BOTH_DSN, HKEY_CURRENT_USER пытается выполнить операцию, а в случае сбоя HKEY_LOCAL_MACHINE используется.  
  
 Эта функция не влияет на **склкреатедатасаурце** и **SQLDriverConnect**. Режим конфигурации должен быть установлен, когда драйвер считывает данные из реестра путем вызова **SQLGetPrivateProfileString** или записи в реестр путем вызова **склвритеприватепрофилестринг**. Вызовы **SQLGetPrivateProfileString** и **склвритеприватепрофилестринг** используют режим конфигурации, чтобы выяснить, на какую часть реестра следует работать.  
  
> [!CAUTION]  
>  **Склсетконфигмоде** следует вызывать только при необходимости; Если режим задан неправильно, установщик ODBC может работать неправильно.  
  
 **Склсетконфигмоде** делает непосредственным изменение в реестре режима конфигурации. Это далеко не процесс изменения режима настройки путем вызова **SQLConfigDataSource**. Вызов **SQLConfigDataSource** задает режим конфигурации для различения имен пользователей и системных DSN при изменении имени DSN. Перед возвратом **SQLConfigDataSource** сбрасывает режим конфигурации в босдсн.  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Создание источника данных|[склкреатедатасаурце](../../../odbc/reference/syntax/sqlcreatedatasource-function.md)|  
|Соединение с источником данных с помощью строки подключения или диалогового окна|[SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)|  
|Получение режима конфигурации|[склжетконфигмоде](../../../odbc/reference/syntax/sqlgetconfigmode-function.md)|
