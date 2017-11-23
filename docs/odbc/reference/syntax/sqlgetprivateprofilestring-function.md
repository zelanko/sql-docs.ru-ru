---
title: "Функция SQLGetPrivateProfileString | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLGetPrivateProfileString
apilocation: sqlsrv32.dll
apitype: dllExport
f1_keywords: SQLGetPrivateProfileString
helpviewer_keywords: SQLGetPrivateProfileString function [ODBC]
ms.assetid: b72ca065-4d67-48df-baac-e18379a8320a
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 06819c4be2b75efe13ba762a282ce425a26f691a
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="sqlgetprivateprofilestring-function"></a>Функция SQLGetPrivateProfileString
**Соответствия**  
 Появился в версии: ODBC 2.0  
  
 **Сводка**  
 **SQLGetPrivateProfileString** возвращает список имен значений или данных, соответствующий значению информация о системе.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
int SQLGetPrivateProfileString(  
     LPCSTR   lpszSection,  
     LPCSTR   lpszEntry,  
     LPCSTR   lpszDefault,  
     LPCSTR   RetBuffer,  
     INT      cbRetBuffer,  
     LPCSTR   lpszFilename);  
```  
  
## <a name="arguments"></a>Аргументы  
 *lpszSection*  
 [Вход] Указывает нулем строка, указывающая раздел, содержащий имя ключа. Если этот аргумент равен NULL, функция копирует все имена разделов в файле предоставленного буфера.  
  
 *lpszEntry*  
 [Вход] Указывает нулем строка, содержащая имя ключа, в которой требуется получить которых связанной строки. Если этот аргумент равен NULL, все основные имена в разделе, указанном параметром *lpszSection* аргумент копируются в буфер, определяемое *RetBuffer* аргумент.  
  
 *lpszDefault*  
 [Вход] Указывает строку, завершающуюся значением null, указывающее значение по умолчанию для указанного ключа, если ключ не найден в файле настройки. Этот аргумент не может быть NULL.  
  
 *RetBuffer*  
 [Выход] Указывает для буфера, принимающего полученные строки.  
  
 *cbRetBuffer*  
 [Вход] Указывает размер в символах, буфера, на который указывает *RetBuffer* аргумент.  
  
 *lpszFilename*  
 [Вход] Указывает строку, завершающуюся значением null, с именем файл инициализации. Если этот аргумент не содержит полный путь к файлу, в каталог по умолчанию выполняется поиск.  
  
## <a name="returns"></a>Возвращает  
 **SQLGetPrivateProfileString** возвращает целочисленное значение, указывающее число считанных символов.  
  
## <a name="diagnostics"></a>Диагностика  
 При вызове **SQLGetPrivateProfileString** происходит сбой, связанный с ним  *\*pfErrorCode* значение можно получить путем вызова **SQLInstallerError**. В следующей таблице перечислены  *\*pfErrorCode* значения, которые могут быть возвращены **SQLInstallerError** и описание каждого из них в контексте этой функции.  
  
|*\*pfErrorCode*|Ошибка|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Установщик Общие ошибки|Произошла ошибка для которого нет ошибок определенного установщика.|  
|ODBC_ERROR_OUT_OF_MEM|Недостаточно памяти|Программе установки не удалось выполнить функцию из-за нехватки памяти.|  
  
## <a name="comments"></a>Комментарии  
 **SQLGetPrivateProfileString** предоставляется как простой способ драйверов портов и установки драйвера библиотек DLL из Microsoft® Windows® для Microsoft Windows или Windows 2000. Вызовы **GetPrivateProfileString** вызовы которые извлекают, следует заменить строку профиля в файле Odbc.ini **SQLGetPrivateProfileString**. **SQLGetPrivateProfileString** вызывает функции в API-Интерфейсе Win32® для извлечения запрошенного имена значений или данных, соответствующий значению подраздела Odbc.ini информация о системе.  
  
 Режим конфигурации (как задано в **SQLSetConfigMode**) указывает, где в сведениях о системе Odbc.ini запись со списком значений источника данных. Если имя источника данных DSN пользователя (режим конфигурации — USERDSN_ONLY), функция считывает из записи Odbc.ini в HKEY_CURRENT_USER. Если имя источника данных DSN системы (SYSTEMDSN_ONLY), функция считывает из записи Odbc.ini в HKEY_LOCAL_MACHINE. Если режим конфигурации BOTHDSN, выполняется попытка HKEY_CURRENT_USER и используется в случае неудачи HKEY_LOCAL_MACHINE.  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Запись значения сведения о системе|[SQLWritePrivateProfileString](../../../odbc/reference/syntax/sqlwriteprivateprofilestring-function.md)|
