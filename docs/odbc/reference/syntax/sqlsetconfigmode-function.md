---
title: Функция S'LSetConfigMode Документы Майкрософт
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
ms.openlocfilehash: c36da48fa1493f61131d23a07f7a820b67ebac82
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81293284"
---
# <a name="sqlsetconfigmode-function"></a>Функция SQLSetConfigMode
**Соответствия**  
 Представлена версия: ODBC 3.0  
  
 **Сводка**  
 **SLSetConfigMode** устанавливает режим конфигурации, который указывает, где в системе находится запись Odbc.ini, в которой перечислены значения DSN.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
  
BOOL SQLSetConfigMode(  
     UWORD     wConfigMode);  
```  
  
## <a name="arguments"></a>Аргументы  
 *wКонфигМодер*  
 (Вход) Режим конфигурации установки (см. "Комментарии"). Значение в *wConfigMode* может быть:  
  
 ODBC_USER_DSN  
  
 ODBC_SYSTEM_DSN  
  
 ODBC_BOTH_DSN  
  
## <a name="returns"></a>Результаты  
 Функция возвращает TRUE, если она успешна, FALSE, если она не удается.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **S'LSetConfigMode** возвращает FALSE, связанное * \*значение pfErrorCode* можно получить, позвонив по **телефону S'LInstallerError.** В следующей таблице перечислены * \*значения pfErrorCode,* которые могут быть возвращены **S'LInstallerError,** и приведены в изъяны каждое из них в контексте этой функции.  
  
|*\*pfErrorCode*|Error|Описание|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_INVALID_PARAM_SEQUENCE|Недействительная последовательность параметров|Аргумент *wConfigMode* не содержал ODBC_USER_DSN, ODBC_SYSTEM_DSN или ODBC_BOTH_DSN.|  
  
## <a name="comments"></a>Комментарии  
 Эта функция используется для установки, где запись Odbc.ini, в которой перечислены значения DSN, находится в системе информации. Если *wConfigMode* является ODBC_USER_DSN, DSN является пользователем DSN и функция читается с записи Odbc.ini в HKEY_CURRENT_USER. Если это ODBC_SYSTEM_DSN, DSN является системой DSN и функция читается из Записи Odbc.ini в HKEY_LOCAL_MACHINE. Если он ODBC_BOTH_DSN, HKEY_CURRENT_USER пытается, и если он не удается, то HKEY_LOCAL_MACHINE используется.  
  
 Эта функция не влияет на **S'LCreateDataSource** и **S'LDriverConnect.** Режим конфигурации должен быть установлен, когда водитель читает из реестра, позвонив в **реестр,** позвонив в реестр, позвонив по **телефону S'LWritePrivateProfileString.** Вызовы на **S'LGetPrivateProfileString** и **S'LWritePrivateProfileString** использовать режим конфигурации, чтобы знать, какая часть реестра для работы.  
  
> [!CAUTION]  
>  **SLSetConfigMode** следует вызывать только в случае необходимости; если режим установлен неправильно, установщик ODBC может не функционировать должным образом.  
  
 **СЗЛСЕтКонигМод** вносит прямую модификацию реестра в режим конфигурации. Это не отличается от процесса изменения режима конфигурации путем вызова на **S'LConfigDataSource**. Вызов на **S'LConfigDataSource** устанавливает режим конфигурации для различения пользователя и системных DSNs при изменении DSN. Перед **возвращением, S'LConfigDataSource** сбрасывает режим конфигурации в BOTHDSN.  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Создание источника данных|[СЗЛСоздатьДатаИсточник](../../../odbc/reference/syntax/sqlcreatedatasource-function.md)|  
|Подключение к источнику данных с помощью строки соединения или диалогового окна|[SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)|  
|Получение режима конфигурации|[СЗЛГетКонигМоид](../../../odbc/reference/syntax/sqlgetconfigmode-function.md)|
