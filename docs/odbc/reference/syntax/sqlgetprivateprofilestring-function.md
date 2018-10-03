---
title: Функция SQLGetPrivateProfileString | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLGetPrivateProfileString
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetPrivateProfileString
helpviewer_keywords:
- SQLGetPrivateProfileString function [ODBC]
ms.assetid: b72ca065-4d67-48df-baac-e18379a8320a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e9790305690b83e5e5a39e8f645a419c8ddd098b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47640637"
---
# <a name="sqlgetprivateprofilestring-function"></a>Функция SQLGetPrivateProfileString
**Соответствие стандартам**  
 Версия была введена: ODBC 2.0  
  
 **Сводка**  
 **SQLGetPrivateProfileString** возвращает список имен значений или данных, соответствующее значению, информация о системе.  
  
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
 [Вход] Указатель на заканчивающуюся нулем строку, указывающую на раздел, содержащий имя ключа. Если этот аргумент равен NULL, функция копирует все имена разделов в файле предоставленный буфер.  
  
 *lpszEntry*  
 [Вход] Указатель на заканчивающуюся нулем строку, содержащую имя ключа, соответствующий строковый которой требуется извлечь. Если этот аргумент равен NULL, все основные имена в разделе, указанном параметром *lpszSection* аргумент копируются в буфер, определяемое *RetBuffer* аргумент.  
  
 *lpszDefault*  
 [Вход] Указатель на заканчивающуюся нулем строку, которая указывает значение по умолчанию для указанного ключа в том случае, если ключ не найден в файле настройки. Этот аргумент не может иметь значение NULL.  
  
 *RetBuffer*  
 [Выход] Указатель буфера, который получает полученные строки.  
  
 *cbRetBuffer*  
 [Вход] Указывает размер в символах, буфера, на которые указывают *RetBuffer* аргумент.  
  
 *lpszFilename*  
 [Вход] Указатель на заканчивающуюся нулем строку, имя файла инициализации. Если этот аргумент не содержит полный путь к файлу, выполняется поиск каталога по умолчанию.  
  
## <a name="returns"></a>Возвращает  
 **SQLGetPrivateProfileString** возвращает целочисленное значение, указывающее число считанных символов.  
  
## <a name="diagnostics"></a>Диагностика  
 При вызове **SQLGetPrivateProfileString** завершается ошибкой, связанным  *\*pfErrorCode* значение можно получить, вызвав **SQLInstallerError**. В следующей таблице перечислены  *\*pfErrorCode* значения, которые могут быть возвращены **SQLInstallerError** и объясняется каждый из них в контексте этой функции.  
  
|*\*pfErrorCode*|Ошибка|Описание|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Ошибки общие установщика|Произошла ошибка для которой нет ошибок определенных установщика.|  
|ODBC_ERROR_OUT_OF_MEM|Недостаточно памяти|Программа установки не удалось выполнить функцию из-за нехватки памяти.|  
  
## <a name="comments"></a>Комментарии  
 **SQLGetPrivateProfileString** предоставляется как простой способ порт драйверы и настройки драйвера библиотеки DLL из Microsoft® Windows® для Microsoft Windows и Windows 2000. Вызовы **GetPrivateProfileString** вызовы, извлечение, следует заменить строку профиля в файле Odbc.ini **SQLGetPrivateProfileString**. **SQLGetPrivateProfileString** вызывает функции в Win32® API для получения запрошенного имена значений или данных, соответствующее значению подраздела Odbc.ini информация о системе.  
  
 Режим конфигурации (как задается **SQLSetConfigMode**) указывает, где запись Odbc.ini, список значений имени DSN в сведениях о системе. Если имя DSN пользовательское имя DSN (режим конфигурации — USERDSN_ONLY), функция считывает из файла Odbc.ini записи в HKEY_CURRENT_USER. Если имя DSN DSN системы (SYSTEMDSN_ONLY), функция считывает из записи Odbc.ini в HKEY_LOCAL_MACHINE. Если используется режим конфигурации BOTHDSN, следующая HKEY_CURRENT_USER и в случае неудачи HKEY_LOCAL_MACHINE используется.  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Запись значения сведения о системе|[SQLWritePrivateProfileString](../../../odbc/reference/syntax/sqlwriteprivateprofilestring-function.md)|
