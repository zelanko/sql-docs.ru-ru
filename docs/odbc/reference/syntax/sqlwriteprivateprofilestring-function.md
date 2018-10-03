---
title: Функция SQLWritePrivateProfileString | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLWritePrivateProfileString
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLWritePrivateProfileString
helpviewer_keywords:
- SQLWritePrivateProfileString [ODBC]
ms.assetid: 526f36a4-92ed-4874-9725-82d27c0b86f9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: aeff68aaa4e4901820054a9bf3079efc7d74cebc
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47818852"
---
# <a name="sqlwriteprivateprofilestring-function"></a>Функция SQLWritePrivateProfileString
**Соответствие стандартам**  
 Версия была введена: ODBC 2.0  
  
 **Сводка**  
 **SQLWritePrivateProfileString** записывает имя и данные в подраздел Odbc.ini информация о системе.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
BOOL SQLWritePrivateProfileString(  
     LPCSTR     lpszSection,  
     LPCSTR     lpszEntry,  
     LPCSTR     lpszString,  
     LPCSTR     lpszFilename);  
```  
  
## <a name="arguments"></a>Аргументы  
 *lpszSection*  
 [Вход] Указатель на заканчивающуюся нулем строку, содержащую имя раздела, в которую копируются строки. Если раздел не существует, он создается. Имя раздела не зависит от случая; Строка может быть любое сочетание прописных и строчных букв.  
  
 *lpszEntry*  
 [Вход] Указывает нулем строка, содержащая имя ключа, связываемого со строкой. Если ключ не существует в указанном разделе, он создается. Если этот аргумент равен NULL, удаляется весь раздел, включая все записи в разделе.  
  
 *lpszString*  
 [Вход] Указатель на заканчивающуюся нулем строку, записываемых в файл. Если этот аргумент равен NULL, ключ указывает *lpszEntry* аргумент удаляется.  
  
 *lpszFilename*  
 [Выход] Указатель на заканчивающуюся нулем строку, имя файла инициализации.  
  
## <a name="returns"></a>Возвращает  
 Функция возвращает значение TRUE при успешном выполнении, FALSE в случае неудачи.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLWritePrivateProfileString** возвращает значение FALSE, связанным  *\*pfErrorCode* значение можно получить, вызвав **SQLInstallerError**. В следующей таблице перечислены  *\*pfErrorCode* значения, которые могут быть возвращены **SQLInstallerError** и объясняется каждый из них в контексте этой функции.  
  
|*\*pfErrorCode*|Ошибка|Описание|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Ошибки общие установщика|Произошла ошибка для которой нет ошибок определенных установщика.|  
|ODBC_ERROR_REQUEST_FAILED|Не удалось выполнить запрос|Не удалось записать запрошенный системную информацию.|  
|ODBC_ERROR_OUT_OF_MEM|Недостаточно памяти|Программа установки не удалось выполнить функцию из-за нехватки памяти.|  
  
## <a name="comments"></a>Комментарии  
 **SQLWritePrivateProfileString** предоставляется как простой способ порт драйверы и настройки драйвера библиотеки DLL из Microsoft® Windows® для Microsoft Windows и Windows 2000. Вызовы **WritePrivateProfileString** , записать строку профиля в файле Odbc.ini следует заменить вызовы **SQLWritePrivateProfileString**. **SQLWritePrivateProfileString** вызывает функции в Win32® API для добавления в подраздел Odbc.ini информация о системе с заданным именем и данных.  
  
 Режим настройки указывает, где операция Odbc.ini, список значений имени DSN в сведениях о системе. Если имя DSN пользовательское имя DSN (переменной состояния — USERDSN_ONLY), эта функция записывает записи Odbc.ini в HKEY_CURRENT_USER. Если имя DSN DSN системы (SYSTEMDSN_ONLY), эта функция записывает записи Odbc.ini в HKEY_LOCAL_MACHINE. Если переменной состояния BOTHDSN, следующая HKEY_CURRENT_USER и в случае неудачи HKEY_LOCAL_MACHINE используется.  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Получение значения из сведений о системе|[SQLGetPrivateProfileString](../../../odbc/reference/syntax/sqlgetprivateprofilestring-function.md)|
