---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e2f2bcd3fef2946e5b983c1bbdeee1efe4776512
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68018925"
---
# <a name="sqlsetconfigmode-function"></a>Функция SQLSetConfigMode
**Соответствия**  
 Введенная версия: ODBC 3,0  
  
 **Сводка**  
 **Склсетконфигмоде** задает режим конфигурации, указывающий, где в сведениях о системе отображается запись ODBC. ini значения DSN.  
  
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
  
## <a name="returns"></a>Возвращает  
 Функция возвращает TRUE, если она успешна, и FALSE в случае сбоя.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **склсетконфигмоде** возвращает значение false, связанное * \*значение пферроркоде* может быть получено путем вызова **склинсталлереррор**. В следующей таблице перечислены значения * \*пферроркоде* , которые могут быть возвращены **склинсталлереррор** , и объясняется каждый из них в контексте этой функции.  
  
|*\*пферроркоде*|Ошибка|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_INVALID_PARAM_SEQUENCE|Недопустимая последовательность параметров|Аргумент *вконфигмоде* не содержит ODBC_USER_DSN, ODBC_SYSTEM_DSN или ODBC_BOTH_DSN.|  
  
## <a name="comments"></a>Комментарии  
 Эта функция используется, чтобы указать, где запись ODBC. ini содержит значения DSN, в сведениях о системе. Если *вконфигмоде* имеет значение ODBC_USER_DSN, то DSN является ПОЛЬЗОВАТЕЛЬСКИМ именем DSN, а функция считывает запись из записи ODBC. ini в HKEY_CURRENT_USER. Если это ODBC_SYSTEM_DSN, то DSN является системным именем DSN, а функция считывает из записи ODBC. ini в HKEY_LOCAL_MACHINE. Если это ODBC_BOTH_DSN, HKEY_CURRENT_USER пытается выполнить операцию, а в случае сбоя HKEY_LOCAL_MACHINE используется.  
  
 Эта функция не влияет на **склкреатедатасаурце** и **SQLDriverConnect**. Режим конфигурации должен быть установлен, когда драйвер считывает данные из реестра путем вызова **SQLGetPrivateProfileString** или записи в реестр путем вызова **склвритеприватепрофилестринг**. Вызовы **SQLGetPrivateProfileString** и **склвритеприватепрофилестринг** используют режим конфигурации, чтобы выяснить, на какую часть реестра следует работать.  
  
> [!CAUTION]  
>  **Склсетконфигмоде** следует вызывать только при необходимости; Если режим задан неправильно, установщик ODBC может работать неправильно.  
  
 **Склсетконфигмоде** делает непосредственным изменение в реестре режима конфигурации. Это далеко не процесс изменения режима настройки путем вызова **SQLConfigDataSource**. Вызов **SQLConfigDataSource** задает режим конфигурации для различения имен пользователей и системных DSN при изменении имени DSN. Перед возвратом **SQLConfigDataSource** сбрасывает режим конфигурации в босдсн.  
  
## <a name="related-functions"></a>Связанные функции  
  
|Тема|См. следующие документы.|  
|---------------------------|---------|  
|Создание источника данных|[склкреатедатасаурце](../../../odbc/reference/syntax/sqlcreatedatasource-function.md)|  
|Соединение с источником данных с помощью строки подключения или диалогового окна|[SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)|  
|Получение режима конфигурации|[склжетконфигмоде](../../../odbc/reference/syntax/sqlgetconfigmode-function.md)|
