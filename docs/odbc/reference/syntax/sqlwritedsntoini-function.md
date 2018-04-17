---
title: Функция SQLWriteDSNToIni | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
apiname:
- SQLWriteDSNToIni
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLWriteDSNToIni
helpviewer_keywords:
- SQLWriteDSNToIni [ODBC]
ms.assetid: dc7018b2-18d4-4657-96d0-086479a47474
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 090c29b141d78a7dbbbfd5b4119408c65f00fa41
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sqlwritedsntoini-function"></a>Функция SQLWriteDSNToIni
**Соответствия**  
 Версии появился: ODBC 1.0  
  
 **Сводка**  
 **SQLWriteDSNToIni** Добавляет источник данных для сведений о системе.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
BOOL SQLWriteDSNToIni(  
     LPCSTR   lpszDSN,  
     LPCSTR   lpszDriver);  
```  
  
## <a name="arguments"></a>Аргументы  
 *lpszDSN*  
 [Вход] Имя источника данных для добавления.  
  
 *lpszDriver*  
 [Вход] Описание драйвера (обычно имя СУБД связанные) пользователям вместо имени физического драйвера.  
  
## <a name="returns"></a>Возвращает  
 Функция возвращает значение TRUE, если он прошел успешно, FALSE в случае неудачи.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLWriteDSNToIni** возвращает значение FALSE, связанный с ним  *\*pfErrorCode* значение можно получить путем вызова **SQLInstallerError**. В следующей таблице перечислены  *\*pfErrorCode* значения, которые могут быть возвращены **SQLInstallerError** и описание каждого из них в контексте этой функции.  
  
|*\*pfErrorCode*|Ошибка|Описание|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Установщик Общие ошибки|Произошла ошибка для которого нет ошибок определенного установщика.|  
|ODBC_ERROR_INVALID_DSN|Недопустимое имя источника данных|*LpszDSN* аргумент содержал строку, которое было указано неверное имя источника данных.|  
|ODBC_ERROR_INVALID_NAME|Недопустимое имя драйвера или преобразователь|*LpszDriver* недопустимый аргумент.|  
|ODBC_ERROR_REQUEST_FAILED|Не удалось выполнить запрос|Программе установки не удалось создать имя источника данных в реестре.|  
|ODBC_ERROR_OUT_OF_MEM|Недостаточно памяти|Программе установки не удалось выполнить функцию из-за нехватки памяти.|  
  
## <a name="comments"></a>Комментарии  
 **SQLWriteDSNToIni** Добавляет источник данных к разделу [источники данных ODBC], информация о системе. Затем он создает раздел спецификация для источника данных и добавляет одно ключевое слово (**драйвер**) с именем драйвера библиотеки DLL в качестве его значения. Если раздел спецификации источника данных уже существует, **SQLWriteDSNToIni** удаляет старого раздела перед созданием нового.  
  
 Код, вызывающий эту функцию необходимо добавить все относящиеся к драйверу ключевые слова и значения в разделе спецификации источника данных сведений о системе.  
  
 Если имя источника данных по умолчанию, **SQLWriteDSNToIni** также создает раздел по умолчанию драйвер спецификации в сведениях о системе.  
  
 Эта функция должна вызываться только из DLL-файлов установки.  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Добавление, изменение или удаление источника данных|[ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md)(в DLL-файлов установки)|  
|Добавление, изменение или удаление источника данных|[SQLConfigDataSource](../../../odbc/reference/syntax/sqlconfigdatasource-function.md)|  
|Удаление из системного имени источника данных|[SQLRemoveDSNFromIni](../../../odbc/reference/syntax/sqlremovedsnfromini-function.md)|
