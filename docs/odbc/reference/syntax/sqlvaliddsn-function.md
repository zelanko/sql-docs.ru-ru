---
title: Функция Склвалиддсн | Документация Майкрософт
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81286974"
---
# <a name="sqlvaliddsn-function"></a>Функция SQLValidDSN
**Соответствия**  
 Введенная версия: ODBC 2,0  
  
 **Сводка**  
 **Склвалиддсн** проверяет длину и допустимость имени источника данных перед добавлением имени в сведения о системе.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
  
BOOL SQLValidDSN(  
     LPCSTR    lpszDSN);  
```  
  
## <a name="arguments"></a>Аргументы  
 *лпсздсн*  
 Входной Имя проверяемого источника данных.  
  
## <a name="returns"></a>Результаты  
 Функция возвращает значение TRUE, если имя источника данных является допустимым. Он возвращает значение FALSE, если имя источника данных является недопустимым, или вызов функции завершился неудачно.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **склвалиддсн** возвращает значение false, связанное * \*значение пферроркоде* может быть получено путем вызова **склинсталлереррор**. Пферроркоде возвращается только в том случае, если вызов функции завершился ошибкой, а не если возвращено значение false, так как имя источника данных является недопустимым. * \** В следующей таблице перечислены значения * \*пферроркоде* , которые могут быть возвращены **склинсталлереррор** , и объясняется каждый из них в контексте этой функции.  
  
|*\*пферроркоде*|Error|Описание|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Общая ошибка установщика|Произошла ошибка, для которой не возникала конкретная ошибка установщика.|  
|ODBC_ERROR_OUT_OF_MEM|Недостаточно памяти|Установщику не удалось выполнить функцию из-за нехватки памяти.|  
  
## <a name="comments"></a>Комментарии  
 **Склвалиддсн** вызывается [ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md) драйвера для проверки длины имени источника данных и допустимости отдельных символов в имени источника данных. Он проверяет, превышает ли длина имени SQL_MAX_DSN_LENGTH, как определено в Sqlext. h. (Длина имени источника данных также проверяется с помощью [склвритедснтоини](../../../odbc/reference/syntax/sqlwritedsntoini-function.md).) **Склвалиддсн** проверяет, включены ли в имя источника данных любые из следующих недопустимых символов:  
  
 [ ] { } ( ) , ; ? * = ! \@ \  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Добавление, изменение или удаление источника данных|[ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md) (в библиотеке DLL установки)|  
|Добавление, изменение или удаление источника данных|[SQLConfigDataSource](../../../odbc/reference/syntax/sqlconfigdatasource-function.md)|  
|Запись имени источника данных в сведения о системе|[склвритедснтоини](../../../odbc/reference/syntax/sqlwritedsntoini-function.md)|
