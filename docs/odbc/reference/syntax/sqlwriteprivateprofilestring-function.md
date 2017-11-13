---
title: "Функция SQLWritePrivateProfileString | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 3025fedee1c5528704c366fa04c5d7ff32e124ee
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="sqlwriteprivateprofilestring-function"></a>Функция SQLWritePrivateProfileString
**Соответствия**  
 Появился в версии: ODBC 2.0  
  
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
 [Вход] Указывает нулем строка, содержащая имя раздела, в который будут копироваться строки. Если раздел не существует, он создается. Имя раздела, не зависит от случая; Строка может быть любое сочетание букв верхнего и нижнего регистра.  
  
 *lpszEntry*  
 [Вход] Указывает нулем строка, содержащая имя ключа, связываемого со строкой. Если ключ не существует в указанном разделе, он создается. Если этот аргумент равен NULL, удаляется весь раздел, включая все записи в этом разделе.  
  
 *lpszString*  
 [Вход] Указывает символом null строку, чтобы записать в файл. Если этот аргумент равен NULL, ключ указывает *lpszEntry* аргумент удаляется.  
  
 *lpszFilename*  
 [Выход] Указывает строку, завершающуюся значением null, с именем файл инициализации.  
  
## <a name="returns"></a>Возвращает  
 Функция возвращает значение TRUE, если он прошел успешно, FALSE в случае неудачи.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLWritePrivateProfileString** возвращает значение FALSE, связанный с ним  *\*pfErrorCode* значение можно получить путем вызова **SQLInstallerError**. В следующей таблице перечислены  *\*pfErrorCode* значения, которые могут быть возвращены **SQLInstallerError** и описание каждого из них в контексте этой функции.  
  
|*\*pfErrorCode*|Ошибка|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Установщик Общие ошибки|Произошла ошибка для которого нет ошибок определенного установщика.|  
|ODBC_ERROR_REQUEST_FAILED|Не удалось выполнить запрос|Не удалось записать запрошенный системной информации.|  
|ODBC_ERROR_OUT_OF_MEM|Недостаточно памяти|Программе установки не удалось выполнить функцию из-за нехватки памяти.|  
  
## <a name="comments"></a>Комментарии  
 **SQLWritePrivateProfileString** предоставляется как простой способ драйверов портов и установки драйвера библиотек DLL из Microsoft® Windows® для Microsoft Windows или Windows 2000. Вызовы **WritePrivateProfileString** , записать строку профиля в файле Odbc.ini следует заменить на вызовы **SQLWritePrivateProfileString**. **SQLWritePrivateProfileString** вызывает функции в API-Интерфейсе Win32® Добавление подраздела Odbc.ini информация о системе с заданным именем и данные.  
  
 Режим настройки указывает, где Odbc.ini запись со списком значений источника данных — сведения о системе. Если имя источника данных DSN пользователя (переменной состояния — USERDSN_ONLY), функция записывает записи Odbc.ini в HKEY_CURRENT_USER. Если имя источника данных DSN системы (SYSTEMDSN_ONLY), функция записывает записи Odbc.ini в разделе HKEY_LOCAL_MACHINE. Если переменной состояния BOTHDSN, выполняется попытка HKEY_CURRENT_USER и используется в случае неудачи HKEY_LOCAL_MACHINE.  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Получение значения из сведений о системе|[SQLGetPrivateProfileString](../../../odbc/reference/syntax/sqlgetprivateprofilestring-function.md)|

