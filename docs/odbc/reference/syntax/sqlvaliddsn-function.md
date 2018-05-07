---
title: Функция SQLValidDSN | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
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
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4560f4645bf8e4e8c255b94c940b0922483cf5f6
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sqlvaliddsn-function"></a>Функция SQLValidDSN
**Соответствия**  
 Появился в версии: ODBC 2.0  
  
 **Сводка**  
 **SQLValidDSN** проверяет длину и допустимость имени источника данных перед добавлением имя системной информации.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
BOOL SQLValidDSN(  
     LPCSTR    lpszDSN);  
```  
  
## <a name="arguments"></a>Аргументы  
 *lpszDSN*  
 [Вход] Имя для проверки источника данных.  
  
## <a name="returns"></a>Возвращает  
 Функция возвращает значение TRUE, если источник данных является допустимым. Если источник данных недопустим или сбой вызова функции возвращается значение FALSE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLValidDSN** возвращает значение FALSE, связанный с ним  *\*pfErrorCode* значение можно получить путем вызова **SQLInstallerError**. Объект  *\*pfErrorCode* возвращается только если сбой вызова функции, не в том случае, если из-за недопустимого имени источника данных вернул значение FALSE. В следующей таблице перечислены  *\*pfErrorCode* значения, которые могут быть возвращены **SQLInstallerError** и описание каждого из них в контексте этой функции.  
  
|*\*pfErrorCode*|Ошибка|Описание|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Установщик Общие ошибки|Произошла ошибка для которого нет ошибок определенного установщика.|  
|ODBC_ERROR_OUT_OF_MEM|Недостаточно памяти|Программе установки не удалось выполнить функцию из-за нехватки памяти.|  
  
## <a name="comments"></a>Комментарии  
 **SQLValidDSN** вызывается драйвер [ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md) для проверки длины имени источника данных и допустимость отдельных символов в имени источника данных. Он проверяет, является ли длина имени больше SQL_MAX_DSN_LENGTH, как определено в Sqlext.h. (Кроме того, длина имени источника данных проверяется по [SQLWriteDSNToIni](../../../odbc/reference/syntax/sqlwritedsntoini-function.md).) **SQLValidDSN** проверяет, включены ли любой из следующих недопустимых символов в имени источника данных:  
  
 [ ] { } ( ) , ; ? * = ! @ \  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Добавление, изменение или удаление источника данных|[ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md) (в DLL-файлов установки)|  
|Добавление, изменение или удаление источника данных|[SQLConfigDataSource](../../../odbc/reference/syntax/sqlconfigdatasource-function.md)|  
|Запись имени источника данных в сведения о системе|[SQLWriteDSNToIni](../../../odbc/reference/syntax/sqlwritedsntoini-function.md)|
