---
title: "Функция SQLReadFileDSN | Документы Microsoft"
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
apiname: SQLReadFileDSN
apilocation: sqlsrv32.dll
apitype: dllExport
f1_keywords: SQLReadFileDSN
helpviewer_keywords: SQLReadFileDSN function [ODBC]
ms.assetid: ead464aa-cdc3-47dd-a0c0-997711205d31
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 58e67106bfa4923725570fdd72ea53433a6b8cf3
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="sqlreadfiledsn-function"></a>Функция SQLReadFileDSN
**Соответствия**  
 Появился в версии: ODBC 3.0  
  
 **Сводка**  
 **SQLReadFileDSN** считывает данные из файлового DSN.  
  
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
 [Вход] Указатель на буфер данных, содержащая имя DSN с файла. Расширение DSN с добавляется ко всем именам файлов, которые уже имеют расширение DSN с. Значение в  *\*lpszFileName* должно быть строкой с завершающим нулем.  
  
 *lpszAppName*  
 [Вход] Указатель на буфер данных, содержащее имя приложения. Это «ODBC» для раздела ODBC. Значение в  *\*lpszAppName* должно быть строкой с завершающим нулем.  
  
 *lpszKeyName*  
 [Вход] Указатель на буфер данных, содержащая имя ключа для чтения. Зарезервированные ключевые слова в разделе «Комментарии». Значение в  *\*lpszAppName* должно быть строкой с завершающим нулем.  
  
 *lpszString*  
 [Выход] Указатель на буфер данных, содержащий строку, связанное с ключом для чтения.  
  
 Если  *\*lpszFileName* является допустимым DSN с именем файла, но *lpszAppName* аргумент является указателем null и *lpszKeyName* аргумент является указателем null, затем  *\*lpszString* содержит список допустимых приложений. Если  *\*lpszFileName* является допустимым DSN с именем файла и  *\*lpszAppName* имеет допустимое имя приложения, но *lpszKeyName* аргумент имеет значение null указатель, затем  *\*lpszString* содержит список допустимых зарезервированных ключевых слов в соответствующем разделе файла источника данных, разделенные точками с запятой. Если  *\*lpszFileName* является допустимым DSN с именем файла, но  *\*lpszAppName* является указателем null и *lpszKeyName* аргумент является указателем null затем  *\*lpszString* содержит список разделов в файле источника данных, разделенные точками с запятой.  
  
 *cbString*  
 [Вход] Длина  *\*lpszString* буфера.  
  
 *pcbString*  
 [Выход] Общее число байтов, доступных для возврата в  *\*lpszString*. Если количество байтов, доступных для возврата больше или равно *cbString*, в выходной строке  *\*lpszString* усекается до *cbString* минус знак завершения null. *PcbString* аргумент может быть пустой указатель.  
  
## <a name="returns"></a>Возвращает  
 Функция возвращает значение TRUE, если он прошел успешно, FALSE в случае неудачи.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLReadFileDSN** возвращает значение FALSE, связанный с ним  *\*pfErrorCode* значение можно получить путем вызова **SQLInstallerError**. В следующей таблице перечислены  *\*pfErrorCode* значения, которые могут быть возвращены **SQLInstallerError** и описание каждого из них в контексте этой функции.  
  
|*\*pfErrorCode*|Ошибка|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Установщик Общие ошибки|Произошла ошибка для которого нет ошибок определенного установщика.|  
|ODBC_ERROR_INVALID_BUFF_LEN|Недопустимый буфер длины|*LpszString* аргумент имеет значение NULL.<br /><br /> *CbString* аргумент был меньше или равно 0.|  
|ODBC_ERROR_INVALID_PATH|Путь установки недопустимый|Путь к имени файла, указанного в *lpszFileName* недопустимый аргумент.|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|Недопустимый тип запроса|*LpszAppName* аргумент имеет значение NULL, а *lpszKeyName* аргумент был недопустимым.|  
|ODBC_ERROR_OUT_OF_MEM|Недостаточно памяти|Программе установки не удалось выполнить функцию из-за нехватки памяти.|  
|ODBC_ERROR_OUTPUT_STRING_TRUNCATED|Выходная строка усечена|Строка, возвращенная в  *\*lpszString* был усечен, поскольку значение в *cbString* была меньше или равно значению в  *\*pcbString*.|  
|ODBC_ERROR_REQUEST_FAILED|Не удалось выполнить запрос|Ключевое слово не существует в файле источника данных.|  
  
## <a name="comments"></a>Комментарии  
 ODBC оставляет за собой [ODBC] Имя раздела, в котором хранятся сведения о соединении. Зарезервированные ключевые слова для этого раздела совпадают с зарезервированным для строки подключения в **SQLDriverConnect**. (Дополнительные сведения см. в разделе [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) описание функции.)  
  
 Приложения могут использовать эти зарезервированные ключевые слова для чтения информации в файловый DSN. Если приложения хочет определить строку соединения, связанную с Источником данных, он может вызвать **SQLReadFileDSN** для любого из зарезервированных ключевых слов строки подключения в разделе [ODBC]. Полная строка подключения переданный соединения представляет собой сочетание все ключевые слова (зарезервированные и относящиеся к драйверу) в разделе [ODBC].  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Записи данных в файловый DSN|[SQLWriteFileDSN](../../../odbc/reference/syntax/sqlwritefiledsn-function.md)|
