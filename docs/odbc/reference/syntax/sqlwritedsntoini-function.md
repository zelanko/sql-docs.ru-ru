---
title: Функция SQLWriteDSNToIni | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c5a36be7a98a39cab8b9df428b8d4bd9a1d399a1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65536790"
---
# <a name="sqlwritedsntoini-function"></a>Функция SQLWriteDSNToIni
**Соответствие стандартам**  
 Представленные версии: ODBC 1.0  
  
 **Сводка**  
 **SQLWriteDSNToIni** Добавляет источник данных сведения о системе.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
  
BOOL SQLWriteDSNToIni(  
     LPCSTR   lpszDSN,  
     LPCSTR   lpszDriver);  
```  
  
## <a name="arguments"></a>Аргументы  
 *lpszDSN*  
 [Вход] Имя источника данных для добавления.  
  
 *lpszDriver*  
 [Вход] Описание драйвера (обычно имя связанного СУБД) предоставляемые пользователям вместо имени физического драйвера.  
  
## <a name="returns"></a>Возвращает  
 Функция возвращает значение TRUE при успешном выполнении, FALSE в случае неудачи.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLWriteDSNToIni** возвращает значение FALSE, связанным  *\*pfErrorCode* значение можно получить, вызвав **SQLInstallerError**. В следующей таблице перечислены *\*pfErrorCode* значения, которые могут быть возвращены **SQLInstallerError** и объясняется каждый из них в контексте этой функции.  
  
|*\*pfErrorCode*|Ошибка|Описание|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Ошибки общие установщика|Произошла ошибка для которой нет ошибок определенных установщика.|  
|ODBC_ERROR_INVALID_DSN|Недопустимое имя источника данных|*LpszDSN* аргумент содержит строку, которая была недопустимое имя источника данных.|  
|ODBC_ERROR_INVALID_NAME|Недопустимое имя драйвера или перевода|*LpszDriver* предоставил недопустимый аргумент.|  
|ODBC_ERROR_REQUEST_FAILED|Не удалось выполнить запрос|Установщику не удалось создать имя DSN в реестре.|  
|ODBC_ERROR_OUT_OF_MEM|Недостаточно памяти|Программа установки не удалось выполнить функцию из-за нехватки памяти.|  
  
## <a name="comments"></a>Комментарии  
 **SQLWriteDSNToIni** Добавляет источник данных в разделе [источники данных ODBC], информация о системе. Затем создает раздел спецификации для источника данных и добавляет одним ключевым словом (**драйвер**) с именем драйвера библиотеки DLL в качестве его значения. Если в разделе спецификации источника данных уже существует, **SQLWriteDSNToIni** удаляет старого раздела перед созданием новой.  
  
 Вызывающий объект этой функции необходимо добавить все относящиеся к драйверу ключевые слова и значения раздела спецификации источника данных сведения о системе.  
  
 Если имя источника данных по умолчанию, **SQLWriteDSNToIni** также создает раздел по умолчанию драйвер спецификации в сведениях о системе.  
  
 Эта функция должна вызываться только из DLL-файлов установки.  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Добавление, изменение или удаление источника данных|[ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md)(в DLL-файлов установки)|  
|Добавление, изменение или удаление источника данных|[SQLConfigDataSource](../../../odbc/reference/syntax/sqlconfigdatasource-function.md)|  
|Удаление из системного имени источника данных|[SQLRemoveDSNFromIni](../../../odbc/reference/syntax/sqlremovedsnfromini-function.md)|
