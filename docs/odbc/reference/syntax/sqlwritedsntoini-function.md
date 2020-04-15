---
title: Функция S'LWriteDSNToIni (ru) Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b8bb141c8f54c49ca3a5c6fc4bc15d434f91795c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81286964"
---
# <a name="sqlwritedsntoini-function"></a>Функция SQLWriteDSNToIni
**Соответствия**  
 Представлена версия: ODBC 1.0  
  
 **Сводка**  
 **S'LWriteDSNToIni** добавляет источник данных в системную информацию.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
  
BOOL SQLWriteDSNToIni(  
     LPCSTR   lpszDSN,  
     LPCSTR   lpszDriver);  
```  
  
## <a name="arguments"></a>Аргументы  
 *lpszDSN*  
 (Вход) Имя источника данных для добавления.  
  
 *lpszDriver*  
 (Вход) Описание драйвера (обычно название связанного DBMS) представлено пользователям вместо физического имени драйвера.  
  
## <a name="returns"></a>Результаты  
 Функция возвращает TRUE, если она успешна, FALSE, если она не удается.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **S'LWriteDSNToIni** возвращает FALSE, связанное * \*значение pfErrorCode* можно получить, позвонив по **телефону S'LInstallerError.** В следующей таблице перечислены * \*значения pfErrorCode,* которые могут быть возвращены **S'LInstallerError,** и приведены в изъяны каждое из них в контексте этой функции.  
  
|*\*pfErrorCode*|Error|Описание|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Общая ошибка установки|Произошла ошибка, для которой не было конкретной ошибки установки.|  
|ODBC_ERROR_INVALID_DSN|Недействительный DSN|Аргумент *lpszDSN* содержал строку, которая была недействительной для DSN.|  
|ODBC_ERROR_INVALID_NAME|Имя недействительного водителя или переводчика|Аргумент *lpszDriver* был недействительным.|  
|ODBC_ERROR_REQUEST_FAILED|Не удалось выполнить запрос|Установщик не смог создать DSN в реестре.|  
|ODBC_ERROR_OUT_OF_MEM|Недостаточно памяти|Установщик не мог выполнить функцию из-за отсутствия памяти.|  
  
## <a name="comments"></a>Комментарии  
 **S'LWriteDSNToIni** добавляет источник данных в раздел системы «Источники данных ODBC». Затем он создает раздел спецификации для источника данных и добавляет одно ключевое слово **(Driver**) с именем драйвера DLL в качестве его значения. Если раздел спецификации источника данных уже существует, **s'LWriteDSNToIni** удаляет старый раздел перед созданием нового.  
  
 Звонящее этой функции должно добавить любые ключевые слова и значения, относясь к драйверу, в раздел спецификации источника данных системной информации.  
  
 Если имя источника данных по умолчанию, **S'LWriteDSNToIni** также создает раздел спецификации драйвера по умолчанию в системе информации.  
  
 Эта функция должна вызываться только из установки DLL.  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Добавление, изменение или удаление источника данных|[ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md)(в настройке DLL)|  
|Добавление, изменение или удаление источника данных|[SQLConfigDataSource](../../../odbc/reference/syntax/sqlconfigdatasource-function.md)|  
|Удаление имени источника данных из системной информации|[СЗЛССНСНИзинини](../../../odbc/reference/syntax/sqlremovedsnfromini-function.md)|
