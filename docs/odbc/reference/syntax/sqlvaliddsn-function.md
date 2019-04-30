---
title: Функция SQLValidDSN | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLValidDSN
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLValidDSN
helpviewer_keywords:
- SQLValidDSN [ODBC]
ms.assetid: 930d1d89-337a-4429-85a2-84ee10555ac9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fb490b475c5795125d11915729693eb630934eb8
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63233490"
---
# <a name="sqlvaliddsn-function"></a>Функция SQLValidDSN
**Соответствие стандартам**  
 Представленные версии: ODBC 2.0  
  
 **Сводка**  
 **SQLValidDSN** проверяет длины и допустимости имя источника данных перед добавлением имени сведения о системе.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
BOOL SQLValidDSN(  
     LPCSTR    lpszDSN);  
```  
  
## <a name="arguments"></a>Аргументы  
 *lpszDSN*  
 [Вход] Имя для проверки источника данных.  
  
## <a name="returns"></a>Возвращает  
 Функция возвращает значение TRUE, если имя источника данных является допустимым. Возвращается значение FALSE, если имя источника данных является недопустимым или сбой вызова функции.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLValidDSN** возвращает значение FALSE, связанным  *\*pfErrorCode* значение можно получить, вызвав **SQLInstallerError**. Объект  *\*pfErrorCode* возвращается только если сбой вызова функции, не в том случае, если было возвращено FALSE, так как имя источника данных недопустимо. В следующей таблице перечислены  *\*pfErrorCode* значения, которые могут быть возвращены **SQLInstallerError** и объясняется каждый из них в контексте этой функции.  
  
|*\*pfErrorCode*|Ошибка|Описание|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Ошибки общие установщика|Произошла ошибка для которой нет ошибок определенных установщика.|  
|ODBC_ERROR_OUT_OF_MEM|Недостаточно памяти|Программа установки не удалось выполнить функцию из-за нехватки памяти.|  
  
## <a name="comments"></a>Комментарии  
 **SQLValidDSN** вызывается драйвера [ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md) проверить длину имени источника данных и допустимость отдельных символов в имени источника данных. Он проверяет, является ли длина имени больше, чем SQL_MAX_DSN_LENGTH, как определено в Sqlext.h. (Длина имени источника данных, кроме того, проверяется по [SQLWriteDSNToIni](../../../odbc/reference/syntax/sqlwritedsntoini-function.md).) **SQLValidDSN** проверяет, включены ли любой из следующих недопустимых символов в имени источника данных:  
  
 [ ] { } ( ) , ; ? * = ! \@ \  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Добавление, изменение или удаление источника данных|[ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md) (в DLL-файлов установки)|  
|Добавление, изменение или удаление источника данных|[SQLConfigDataSource](../../../odbc/reference/syntax/sqlconfigdatasource-function.md)|  
|Запись имени источника данных в сведения о системе|[SQLWriteDSNToIni](../../../odbc/reference/syntax/sqlwritedsntoini-function.md)|
