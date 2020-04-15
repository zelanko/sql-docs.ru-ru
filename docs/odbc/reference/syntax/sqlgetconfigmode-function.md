---
title: Функция S'LGetConfigMode Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: cc11bec24ede3352dd43f3645fb8c720b77fdabe
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81285694"
---
# <a name="sqlgetconfigmode-function"></a>Функция SQLGetConfigMode
**Соответствия**  
 Представлена версия: ODBC 3.0  
  
 **Сводка**  
 **S'LGetConfigMode** получает режим конфигурации, который указывает, где в системе находится запись Odbc.ini, в которой перечислены значения DSN.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
  
BOOL SQLGetConfigMode(  
     UWORD *   pwConfigMode);  
```  
  
## <a name="arguments"></a>Аргументы  
 *pwConfigMode*  
 (Выход) Указатель на буфер, содержащий режим конфигурации. (См. "Комментарии.") Значение в * \*pwConfigMode* может быть:  
  
 ODBC_USER_DSN  
  
 ODBC_SYSTEM_DSN  
  
 ODBC_BOTH_DSN  
  
## <a name="returns"></a>Результаты  
 Функция возвращает TRUE, если она успешна, FALSE, если она не удается.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **S'LGetConfigMode** возвращает FALSE, связанное * \*значение pfErrorCode* можно получить, позвонив по **телефону S'LInstallerError.** В следующей таблице перечислены * \*значения pfErrorCode,* которые могут быть возвращены **S'LInstallerError,** и приведены в изъяны каждое из них в контексте этой функции.  
  
|*\*pfErrorCode*|Error|Описание|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_OUT_OF_MEM|Недостаточно памяти|Установщик не мог выполнить функцию из-за отсутствия памяти.|  
  
## <a name="comments"></a>Комментарии  
 Эта функция используется для определения того, где в системе находится запись Odbc.ini, в которой перечислены значения DSN. Если * \*pwConfigMode* является ODBC_USER_DSN, DSN является пользователем DSN и функция читается с записи Odbc.ini в HKEY_CURRENT_USER. Если это ODBC_SYSTEM_DSN, DSN является системой DSN и функция читается из Записи Odbc.ini в HKEY_LOCAL_MACHINE. Если он ODBC_BOTH_DSN, HKEY_CURRENT_USER судят, а если не получается, используется HKEY_LOCAL_MACHINE.  
  
 По **умолчанию, sLGetConfigMode** возвращает ODBC_BOTH_DSN. Когда пользователь DSN или Система DSN создается путем вызова на **S'LConfigDataSource**, функция устанавливает режим конфигурации, чтобы ODBC_USER_DSN или ODBC_SYSTEM_DSN, чтобы различать пользователя и системы DSNs при изменении DSN. Перед **возвращением, S'LConfigDataSource** сбрасывает режим конфигурации для ODBC_BOTH_DSN.  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Настройка режима конфигурации|[СЗЛСККонзигМой](../../../odbc/reference/syntax/sqlsetconfigmode-function.md)|
