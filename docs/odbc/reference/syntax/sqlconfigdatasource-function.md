---
title: Функция SQLConfigDataSource | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 59b5cae9075d9d3c692d56e74edebabda8884fe2
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65537583"
---
# <a name="sqlconfigdatasource-function"></a>SQLConfigDataSource, функция
**Соответствие стандартам**  
 Представленные версии: ODBC 1.0  
  
 **Сводка**  
 **SQLConfigDataSource** добавляет, изменяет или удаляет источники данных.  
  
 Функциональные возможности **SQLConfigDataSource** также может осуществляться с помощью [ODBCCONF. EXE](../../../odbc/odbcconf-exe.md).  
  
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
 [Вход] Дескриптор родительского окна. Функция не будет отображать все диалоговые окна, если дескриптор имеет значение null.  
  
 *fRequest*  
 [Вход] Тип запроса. *FRequest* аргумент должен иметь один из следующих значений:  
  
 ODBC_ADD_DSN: Добавление нового источника данных.  
  
 ODBC_CONFIG_DSN: Настройка (изменить) существующего источника данных.  
  
 ODBC_REMOVE_DSN: Удаление существующего источника данных.  
  
 ODBC_ADD_SYS_DSN: Добавьте новый источник данных системы.  
  
 ODBC_CONFIG_SYS_DSN: Изменение существующего системного источника данных.  
  
 ODBC_REMOVE_SYS_DSN: Удаление существующего системного источника данных.  
  
 ODBC_REMOVE_DEFAULT_DSN: Удалите раздел спецификации источника данных по умолчанию из сведений о системе. (Он также удаляет раздел по умолчанию драйвер спецификации из записи файла Odbcinst.ini в сведениях о системе. Это *fRequest* выполняет ту же функцию, что устаревшие **SQLRemoveDefaultDataSource** функции.) Если этот параметр указан, все другие параметры в вызове **SQLConfigDataSource** должны быть значения NULL; если они не равны NULL, они будут игнорироваться.  
  
 *lpszDriver*  
 [Вход] Описание драйвера (обычно имя связанного СУБД) предоставляемые пользователям вместо имени физического драйвера.  
  
 *lpszAttributes*  
 [Вход] Двойной завершающий список атрибутов в виде пар "ключевое слово значение". Дополнительные сведения см. в разделе [ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md).  
  
## <a name="returns"></a>Возвращает  
 Функция возвращает значение TRUE при успешном выполнении, FALSE в случае неудачи. Если запись не существует в сведениях о системе, при вызове этой функции, функция возвращает значение FALSE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLConfigDataSource** возвращает значение FALSE, связанным  *\*pfErrorCode* значение можно получить, вызвав **SQLInstallerError**. В следующей таблице перечислены  *\*pfErrorCode* значения, которые могут быть возвращены **SQLInstallerError** и объясняется каждый из них в контексте этой функции.  
  
|*\*pfErrorCode*|Ошибка|Описание|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Ошибки общие установщика|Произошла ошибка для которой нет ошибок определенных установщика.|  
|ODBC_ERROR_INVALID_HWND|Недопустимый дескриптор окна|*HwndParent* аргумент был недопустимым, или значение NULL.|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|Недопустимый тип запроса|*FRequest* аргумент не является одним из следующих:<br /><br /> ODBC_ADD_DSN ODBC_CONFIG_DSN ODBC_REMOVE_DSN ODBC_ADD_SYS_DSN ODBC_CONFIG_SYS_DSN ODBC_REMOVE_SYS_DSN ODBC_REMOVE_DEFAULT_DSN|  
|ODBC_ERROR_INVALID_NAME|Недопустимое имя драйвера или перевода|*LpszDriver* предоставил недопустимый аргумент. Он не будет найден в реестре.|  
|ODBC_ERROR_INVALID_KEYWORD_VALUE|Пары "недопустимое ключевое слово значение"|*LpszAttributes* аргумент содержит синтаксическую ошибку.|  
|ODBC_ERROR_REQUEST_FAILED|*Запросить* сбой|Программа установки не удалось выполнить операцию, запрошенную *fRequest* аргумент. Вызов **ConfigDSN** не удалось.|  
|ODBC_ERROR_LOAD_LIBRARY_FAILED|Не удалось загрузить библиотеку установки драйвера или перевода|Не удалось загрузить библиотеку установки драйвера.|  
|ODBC_ERROR_OUT_OF_MEM|Недостаточно памяти|Программа установки не удалось выполнить функцию из-за нехватки памяти.|  
  
## <a name="comments"></a>Комментарии  
 **SQLConfigDataSource** использует значение *lpszDriver* для чтения полный путь к DLL-файлов установки драйвера из информации о системе. Он загружает библиотеки DLL и вызовы **ConfigDSN** с теми же аргументами, которые были переданы.  
  
 **SQLConfigDataSource** возвращает значение FALSE, если не удается найти или загрузить DLL-файлов установки или если пользователь отменил диалоговое окно. В противном случае оно возвращает состояние, полученное от **ConfigDSN**.  
  
 **SQLConfigDataSource** сопоставляет системный DSN *fRequest*s, чтобы на пользовательские имена DSN *fRequest*s (ODBC_ADD_SYS_DSN для ODBC_ADD_DSN, ODBC_CONFIG_SYS_DSN ODBC_CONFIG_DSN и ODBC_REMOVE_SYS_ DSN значение ODBC_REMOVE_DSN). Для различения пользователей и системных имен DSN, **SQLConfigDataSource** задает установщик режим конфигурации согласно следующей таблице. До возвращения, **SQLConfigDataSource** BOTHDSN восстанавливает режим конфигурации. **ConfigDSN** (реализован драйверы) должен вызывать **SQLWriteDSNToIni** и **SQLWritePrivateProfileString** для поддержки системный DSN. Дополнительные сведения см. в разделе [функция ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md).  
  
|*fRequest*|Режим настройки|  
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
|Добавление, изменение или удаление источника данных|[ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md) (в DLL-файлов установки)|  
|Удаление из системного имени источника данных|[SQLRemoveDSNFromIni](../../../odbc/reference/syntax/sqlremovedsnfromini-function.md)|  
|Добавление имени источника данных в сведения о системе|[SQLWriteDSNToIni](../../../odbc/reference/syntax/sqlwritedsntoini-function.md)|
