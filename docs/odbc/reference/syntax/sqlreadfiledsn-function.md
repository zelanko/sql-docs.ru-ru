---
title: Функция SQLReadFileDSN | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLReadFileDSN
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLReadFileDSN
helpviewer_keywords:
- SQLReadFileDSN function [ODBC]
ms.assetid: ead464aa-cdc3-47dd-a0c0-997711205d31
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9a247b9916bd4b8bfe8704d7f374ef027043e2ae
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63262453"
---
# <a name="sqlreadfiledsn-function"></a>Функция SQLReadFileDSN
**Соответствие стандартам**  
 Представленные версии: ODBC 3.0  
  
 **Сводка**  
 **SQLReadFileDSN** считывает данные из файлового имени DSN.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
BOOL SQLReadFileDSN(  
     LPCSTR   lpszFileName,  
     LPCSTR   lpszAppName,  
     LPCSTR   lpszKeyName,  
     LPSTR    lpszString,  
     WORD     cbString,  
     WORD *   pcbString);  
```  
  
## <a name="arguments"></a>Аргументы  
 *lpszFileName*  
 [Вход] Указатель на буфер данных, содержащий имя файла .dsn. Расширение .dsn добавляется для всех имен файлов, у вас нет расширением .dsn. Значение в  *\*lpszFileName* должен быть строкой с завершающим нулем.  
  
 *lpszAppName*  
 [Вход] Указатель на буфер данных, содержащий имя приложения. Это «ODBC» в разделе ODBC статьи. Значение в  *\*lpszAppName* должен быть строкой с завершающим нулем.  
  
 *lpszKeyName*  
 [Вход] Указатель на буфер данных, содержащий имя ключа для чтения. См. в разделе «Комментарии» для зарезервированных ключевых слов. Значение в  *\*lpszAppName* должен быть строкой с завершающим нулем.  
  
 *lpszString*  
 [Выход] Указатель на буфер данных, содержащий строку, связанную с ключом для чтения.  
  
 Если  *\*lpszFileName* является допустимым .dsn именем файла, но *lpszAppName* аргумент является указателем null и *lpszKeyName* аргумент является пустым указателем, затем  *\*lpszString* содержит список допустимых приложений. Если  *\*lpszFileName* — это имя файла допустимым .dsn и  *\*lpszAppName* имеет допустимое имя приложения, но *lpszKeyName* аргумент равен null указатель, затем  *\*lpszString* содержит список допустимых зарезервированные ключевые слова в соответствующем разделе файла DSN, разделенные точками с запятой. Если  *\*lpszFileName* является допустимым .dsn именем файла, но  *\*lpszAppName* является указателем null и *lpszKeyName* аргумент является указателем null затем  *\*lpszString* содержит список разделов в файле имени DSN, разделенные точками с запятой.  
  
 *cbString*  
 [Вход] Длина  *\*lpszString* буфера.  
  
 *pcbString*  
 [Выход] Общее число байтов, доступных для возврата в  *\*lpszString*. Если количество байтов, доступных для возврата больше или равно *cbString*, выходную строку в  *\*lpszString* усекается до *cbString* минус символ, конечное значение null. *PcbString* аргументом может быть пустым указателем.  
  
## <a name="returns"></a>Возвращает  
 Функция возвращает значение TRUE при успешном выполнении, FALSE в случае неудачи.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLReadFileDSN** возвращает значение FALSE, связанным  *\*pfErrorCode* значение можно получить, вызвав **SQLInstallerError**. В следующей таблице перечислены  *\*pfErrorCode* значения, которые могут быть возвращены **SQLInstallerError** и объясняется каждый из них в контексте этой функции.  
  
|*\*pfErrorCode*|Ошибка|Описание|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Ошибки общие установщика|Произошла ошибка для которой нет ошибок определенных установщика.|  
|ODBC_ERROR_INVALID_BUFF_LEN|Недопустимый буфер длины|*LpszString* аргумент имел значение NULL.<br /><br /> *CbString* аргумент был меньше или равно 0.|  
|ODBC_ERROR_INVALID_PATH|Путь установки недопустимый|Путь к имени файла, указанного в *lpszFileName* предоставил недопустимый аргумент.|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|Недопустимый тип запроса|*LpszAppName* аргумент имел значение NULL, хотя *lpszKeyName* аргумент был допустимым.|  
|ODBC_ERROR_OUT_OF_MEM|Недостаточно памяти|Программа установки не удалось выполнить функцию из-за нехватки памяти.|  
|ODBC_ERROR_OUTPUT_STRING_TRUNCATED|Выходная строка усечена|Строка, возвращаемая в  *\*lpszString* был усечен, поскольку значение в *cbString* была меньше или равно значению  *\*pcbString*.|  
|ODBC_ERROR_REQUEST_FAILED|Не удалось выполнить запрос|Ключевое слово не существует в файле имени DSN.|  
  
## <a name="comments"></a>Комментарии  
 ODBC оставляет за собой имя раздела [ODBC], в котором хранятся сведения о соединении. Зарезервированные ключевые слова для этого раздела такие же, как зарезервированный для строки подключения в **SQLDriverConnect**. (Дополнительные сведения см. в разделе [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) описание функции.)  
  
 Приложения могут использовать эти зарезервированные ключевые слова, чтобы ознакомиться с разделом файлового имени DSN. Если приложения хочет найти строку соединения, связанный с Источником данных оно может вызвать **SQLReadFileDSN** для любого из зарезервированных ключевых слов строки подключения в разделе [ODBC]. Полная строка подключения переданный подключения DSN представляет собой сочетание все ключевые слова (зарезервированные и специфические для драйвера) в разделе [ODBC].  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Записи данных в файловый DSN|[SQLWriteFileDSN](../../../odbc/reference/syntax/sqlwritefiledsn-function.md)|
