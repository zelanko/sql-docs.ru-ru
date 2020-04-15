---
title: Функция S'LValiddSN Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6dfafca22d0b04f2147b1af24b53e787493efe67
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81286974"
---
# <a name="sqlvaliddsn-function"></a>Функция SQLValidDSN
**Соответствия**  
 Представлена версия: ODBC 2.0  
  
 **Сводка**  
 **СЗЛЛидедСН** проверяет длину и достоверность имени источника данных до добавления имени в системную информацию.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
  
BOOL SQLValidDSN(  
     LPCSTR    lpszDSN);  
```  
  
## <a name="arguments"></a>Аргументы  
 *lpszDSN*  
 (Вход) Имя источника данных для проверки.  
  
## <a name="returns"></a>Результаты  
 Функция возвращает TRUE, если имя источника данных является действительным. Он возвращает FALSE, если имя источника данных является недействительным или вызов функции не работает.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **S'LValidDSN** возвращает FALSE, связанное * \*значение pfErrorCode* можно получить, позвонив по **телефону S'LInstallerError.** PFErrorCode возвращается только в случае сбывания вызова функции, а не в случае возврата FALSE, так как имя источника данных является недействительным. * \** В следующей таблице перечислены * \*значения pfErrorCode,* которые могут быть возвращены **S'LInstallerError,** и приведены в изъяны каждое из них в контексте этой функции.  
  
|*\*pfErrorCode*|Error|Описание|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Общая ошибка установки|Произошла ошибка, для которой не было конкретной ошибки установки.|  
|ODBC_ERROR_OUT_OF_MEM|Недостаточно памяти|Установщик не мог выполнить функцию из-за отсутствия памяти.|  
  
## <a name="comments"></a>Комментарии  
 **СЗЛЛидДСН** вызывается [configDSN](../../../odbc/reference/syntax/configdsn-function.md) водителя для проверки длины имени источника данных и достоверности отдельных символов в названии источника данных. Он проверяет, превышает ли длина имени, чем SQL_MAX_DSN_LENGTH, как это определено в Sqlext.h. (Длина имени источника данных также проверяется [S'LWriteDSNToIni](../../../odbc/reference/syntax/sqlwritedsntoini-function.md).) **SLValidDSN** проверяет, включены ли какие-либо из следующих недействительных символов в имя источника данных:  
  
 [ ] { } ( ) , ; ? * = ! \@ \  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Добавление, изменение или удаление источника данных|[ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md) (в настройке DLL)|  
|Добавление, изменение или удаление источника данных|[SQLConfigDataSource](../../../odbc/reference/syntax/sqlconfigdatasource-function.md)|  
|Написание имени источника данных в системную информацию|[СЗЛДуНТСНОниИ](../../../odbc/reference/syntax/sqlwritedsntoini-function.md)|
