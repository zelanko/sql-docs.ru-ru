---
title: Функция SQLConfigDataSource | Документы Microsoft
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
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 247062e552b02d273e8480ac8bf9765ca17c0317
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sqlconfigdatasource-function"></a>SQLConfigDataSource, функция
**Соответствия**  
 Версии появился: ODBC 1.0  
  
 **Сводка**  
 **SQLConfigDataSource** добавляет, изменяет или удаляет источников данных.  
  
 Функциональные возможности **SQLConfigDataSource** можно получить с помощью [ODBCCONF. EXE](../../../odbc/odbcconf-exe.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
BOOL SQLConfigDataSource(  
     HWND     hwndParent,  
     WORD     fRequest,  
     LPCSTR   lpszDriver,  
     LPCSTR   lpszAttributes);  
```  
  
## <a name="arguments"></a>Аргументы  
 *hwndParent*  
 [Вход] Дескриптор родительского окна. Функция не будет отображать все диалоговые окна, если маркер имеет значение null.  
  
 *fRequest*  
 [Вход] Тип запроса. *FRequest* аргумент должен иметь один из следующих значений:  
  
 ODBC_ADD_DSN: Добавление нового источника данных.  
  
 ODBC_CONFIG_DSN: Настройка (изменить) существующего источника данных.  
  
 Значение ODBC_REMOVE_DSN: Удаление существующего источника данных.  
  
 ODBC_ADD_SYS_DSN: Добавление нового системного источника данных.  
  
 ODBC_CONFIG_SYS_DSN: Изменение существующего системного источника данных.  
  
 ODBC_REMOVE_SYS_DSN: Удаление существующего системного источника данных.  
  
 ODBC_REMOVE_DEFAULT_DSN: Удалите раздел спецификации источника данных по умолчанию из сведений о системе. (Она также удаляет раздел по умолчанию драйвер спецификации из Odbcinst.ini запись сведений о системе. Это *fRequest* выполняет ту же функцию, как устаревшие **SQLRemoveDefaultDataSource** функции.) Если этот параметр указан, все другие параметры в вызове **SQLConfigDataSource** должны иметь значения NULL, если они не равны NULL, они будут пропущены.  
  
 *lpszDriver*  
 [Вход] Описание драйвера (обычно имя СУБД связанные) пользователям вместо имени физического драйвера.  
  
 *lpszAttributes*  
 [Вход] Двойной завершающий список атрибутов в форме пар «ключевое слово значение». Дополнительные сведения см. в разделе [ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md).  
  
## <a name="returns"></a>Возвращает  
 Функция возвращает значение TRUE, если он прошел успешно, FALSE в случае неудачи. Если не существует запись сведений о системе при вызове этой функцией, функция возвращает значение FALSE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLConfigDataSource** возвращает значение FALSE, связанный с ним  *\*pfErrorCode* значение можно получить путем вызова **SQLInstallerError**. В следующей таблице перечислены  *\*pfErrorCode* значения, которые могут быть возвращены **SQLInstallerError** и описание каждого из них в контексте этой функции.  
  
|*\*pfErrorCode*|Ошибка|Описание|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Установщик Общие ошибки|Произошла ошибка для которого нет ошибок определенного установщика.|  
|ODBC_ERROR_INVALID_HWND|Недопустимый дескриптор окна|*HwndParent* аргумент имеет недопустимый или NULL.|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|Недопустимый тип запроса|*FRequest* аргумент не является одним из следующих:<br /><br /> ODBC_ADD_DSN ODBC_CONFIG_DSN ЗНАЧЕНИЕ ODBC_REMOVE_DSN ODBC_ADD_SYS_DSN ODBC_CONFIG_SYS_DSN ODBC_REMOVE_SYS_DSN ODBC_REMOVE_DEFAULT_DSN|  
|ODBC_ERROR_INVALID_NAME|Недопустимое имя драйвера или преобразователь|*LpszDriver* недопустимый аргумент. Он не найден в реестре.|  
|ODBC_ERROR_INVALID_KEYWORD_VALUE|Пары "недопустимое ключевое слово значение"|*LpszAttributes* аргумент содержит синтаксическую ошибку.|  
|ODBC_ERROR_REQUEST_FAILED|*Запрос* сбой|Программе установки не удалось выполнить операцию, запрошенную *fRequest* аргумент. Вызов **ConfigDSN** сбой.|  
|ODBC_ERROR_LOAD_LIBRARY_FAILED|Не удалось загрузить библиотеку установки драйвера или преобразователь|Не удается загрузить библиотеку установки драйвера.|  
|ODBC_ERROR_OUT_OF_MEM|Недостаточно памяти|Программе установки не удалось выполнить функцию из-за нехватки памяти.|  
  
## <a name="comments"></a>Комментарии  
 **SQLConfigDataSource** использует значение *lpszDriver* для чтения полный путь к DLL-файлов установки драйвера из сведений о системе. Он загружает библиотеку DLL и вызовы **ConfigDSN** с теми же аргументами, которые были переданы.  
  
 **SQLConfigDataSource** возвращает FALSE, если не удается найти или загрузить DLL-файлов установки или если пользователь отменяет диалоговым окном. В противном случае он возвращает состояние, полученное от **ConfigDSN**.  
  
 **SQLConfigDataSource** сопоставляет системный DSN *fRequest*s, чтобы пользовательский DSN *fRequest*s (ODBC_ADD_SYS_DSN для ODBC_ADD_DSN, ODBC_CONFIG_SYS_DSN ODBC_CONFIG_DSN и ODBC_REMOVE_SYS_ DSN значение ODBC_REMOVE_DSN). Чтобы различать пользователей и системных имен DSN **SQLConfigDataSource** задает установщик, режим конфигурации согласно следующей таблице. Перед возвратом, **SQLConfigDataSource** восстанавливает режим конфигурации BOTHDSN. **ConfigDSN** (реализован с помощью драйверов) должен вызывать **SQLWriteDSNToIni** и **SQLWritePrivateProfileString** для поддержки системный DSN. Дополнительные сведения см. в разделе [ConfigDSN функция](../../../odbc/reference/syntax/configdsn-function.md).  
  
|*fRequest*|Режим конфигурации|  
|----------------|------------------------|  
|ODBC_ADD_DSN|USERDSN_ONLY|  
|ODBC_CONFIG_DSN|USERDSN_ONLY|  
|ЗНАЧЕНИЕ ODBC_REMOVE_DSN|USERDSN_ONLY|  
|ODBC_ADD_SYS_DSN|SYSTEMDSN_ONLY|  
|ODBC_CONFIG_SYS_DSN|SYSTEMDSN_ONLY|  
|ODBC_REMOVE_SYS_DSN|SYSTEMDSN_ONLY|  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Добавление, изменение или удаление источника данных|[ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md) (в DLL-файлов установки)|  
|Удаление из системного имени источника данных|[SQLRemoveDSNFromIni](../../../odbc/reference/syntax/sqlremovedsnfromini-function.md)|  
|Добавление имени источника данных для сведений о системе|[SQLWriteDSNToIni](../../../odbc/reference/syntax/sqlwritedsntoini-function.md)|
