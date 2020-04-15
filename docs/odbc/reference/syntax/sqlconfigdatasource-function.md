---
title: Функция S'LConfigDataИсточник (ru) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLConfigDataSource
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLConfigDataSource
helpviewer_keywords:
- SQLConfigDataSource function [ODBC]
ms.assetid: f8d6e342-c010-434e-b1cd-f5371fb50a14
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 90a51193a8f4edbb013527c4dde0625b75131583
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299634"
---
# <a name="sqlconfigdatasource-function"></a>SQLConfigDataSource, функция
**Соответствия**  
 Представлена версия: ODBC 1.0  
  
 **Сводка**  
 **S'LConfigDataSource** добавляет, изменяет или удаляет источники данных.  
  
 Функциональность **S'LConfigDataSource** также может быть доступна с [ODBCCONF. EXE](../../../odbc/odbcconf-exe.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
  
BOOL SQLConfigDataSource(  
     HWND     hwndParent,  
     WORD     fRequest,  
     LPCSTR   lpszDriver,  
     LPCSTR   lpszAttributes);  
```  
  
## <a name="arguments"></a>Аргументы  
 *hwndParent*  
 (Вход) Ручка родительского окна. Функция не будет отображать диалоговые коробки, если ручка недействительна.  
  
 *fЗапрос*  
 (Вход) Тип запроса. Аргумент *fRequest* должен содержать одно из следующих значений:  
  
 ODBC_ADD_DSN: Добавьте новый источник пользовательских данных.  
  
 ODBC_CONFIG_DSN: Налаживать (изменять) существующий источник пользовательских данных.  
  
 ODBC_REMOVE_DSN: Удалите существующий источник пользовательских данных.  
  
 ODBC_ADD_SYS_DSN: Добавьте новый источник системных данных.  
  
 ODBC_CONFIG_SYS_DSN: Изменить существующий источник системных данных.  
  
 ODBC_REMOVE_SYS_DSN: Удалите существующий источник системных данных.  
  
 ODBC_REMOVE_DEFAULT_DSN: Удалите из системной информации раздел спецификации источника данных по умолчанию. (Он также удаляет раздел спецификации драйвера по умолчанию из входа Odbcinst.ini в системной информации. Этот *fRequest* выполняет ту же функцию, что и удручаемый функция **S'LRemoveDefaultDataSource.)** Когда эта опция указана, все остальные параметры в вызове на **S'LConfigDataSource** должны быть NULLs; если они не являются NULL, они будут проигнорированы.  
  
 *lpszDriver*  
 (Вход) Описание драйвера (обычно название связанного DBMS) представлено пользователям вместо физического имени драйвера.  
  
 *lpszАтрибуты*  
 (Вход) Вдвойне нулевой-завершенный список атрибутов в виде пар значения ключевых слов. Для получения дополнительной информации [см.](../../../odbc/reference/syntax/configdsn-function.md)  
  
## <a name="returns"></a>Результаты  
 Функция возвращает TRUE, если она успешна, FALSE, если она не удается. Если в системе нет входа, когда эта функция вызывается, функция возвращает FALSE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **S'LConfigDataSource** возвращает FALSE, связанное * \*значение pfErrorCode* можно получить, позвонив по **телефону S'LInstallerError.** В следующей таблице перечислены * \*значения pfErrorCode,* которые могут быть возвращены **S'LInstallerError,** и приведены в изъяны каждое из них в контексте этой функции.  
  
|*\*pfErrorCode*|Error|Описание|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Общая ошибка установки|Произошла ошибка, для которой не было конкретной ошибки установки.|  
|ODBC_ERROR_INVALID_HWND|Недействительная ручка окна|Аргумент *hwndParent* был недействительным или NULL.|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|Недействительный тип запроса|Аргумент *fRequest* не был одним из следующих:<br /><br /> ODBC_ADD_DSN ODBC_CONFIG_DSN ODBC_REMOVE_DSN ODBC_ADD_SYS_DSN ODBC_CONFIG_SYS_DSN ODBC_REMOVE_SYS_DSN ODBC_REMOVE_DEFAULT_DSN|  
|ODBC_ERROR_INVALID_NAME|Имя недействительного водителя или переводчика|Аргумент *lpszDriver* был недействительным. Его не удалось найти в реестре.|  
|ODBC_ERROR_INVALID_KEYWORD_VALUE|Недействительные пары значения ключевых слов|Аргумент *lpszAttributes* содержал ошибку синтаксиса.|  
|ODBC_ERROR_REQUEST_FAILED|*Запрос* не удался|Установщик не смог выполнить операцию, запрошенную аргументом *fRequest.* Вызов на **ConfigDSN** не удалось.|  
|ODBC_ERROR_LOAD_LIBRARY_FAILED|Не удалось загрузить библиотеку установки драйвера или переводчика|Библиотека установки драйвера не может быть загружена.|  
|ODBC_ERROR_OUT_OF_MEM|Недостаточно памяти|Установщик не мог выполнить функцию из-за отсутствия памяти.|  
  
## <a name="comments"></a>Комментарии  
 **SLConfigDataSource** использует значение *lpszDriver,* чтобы прочитать полный путь установки DLL для драйвера из системной информации. Он загружает DLL и вызывает **ConfigDSN** с теми же аргументами, которые были переданы ему.  
  
 **S'LConfigDataSource** возвращает FALSE, если он не в состоянии найти или загрузить настройку DLL или если пользователь отменяет диалоговый ящик. В противном случае он возвращает статус, полученный от **ConfigDSN**.  
  
 **S'LConfigDataSource** карты системы DSN *fRequest*s для пользователя DSN *fRequest*s (ODBC_ADD_SYS_DSN ODBC_ADD_DSN, ODBC_CONFIG_SYS_DSN ODBC_CONFIG_DSN, и ODBC_REMOVE_SYS_DSN ODBC_REMOVE_DSN). Для различения пользователей и системных DSNs, **S'LConfigDataSource** устанавливает режим конфигурации установки в соответствии со следующей таблицей. Перед возвращением режим конфигурации с системой **«SLConfigDataSource»** сбрасывает режим конфигурации в BOTHDSN. **ConfigDSN** (реализованный драйверами) должен вызывать **S'LWriteDSNToIni** и **S'LWritePrivateProfileString** для поддержки системы DSN. Для получения дополнительной [ConfigDSN Function](../../../odbc/reference/syntax/configdsn-function.md)информации см.  
  
|*fЗапрос*|Режим конфигурации|  
|----------------|------------------------|  
|ODBC_ADD_DSN|USERDSN_ONLY|  
|ODBC_CONFIG_DSN|USERDSN_ONLY|  
|ODBC_REMOVE_DSN|USERDSN_ONLY|  
|ODBC_ADD_SYS_DSN|SYSTEMDSN_ONLY|  
|ODBC_CONFIG_SYS_DSN|SYSTEMDSN_ONLY|  
|ODBC_REMOVE_SYS_DSN|SYSTEMDSN_ONLY|  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Добавление, изменение или удаление источника данных|[ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md) (в установке DLL)|  
|Удаление имени источника данных из системной информации|[СЗЛССНСНИзинини](../../../odbc/reference/syntax/sqlremovedsnfromini-function.md)|  
|Добавление имени источника данных в системную информацию|[СЗЛДуНТСНОниИ](../../../odbc/reference/syntax/sqlwritedsntoini-function.md)|
