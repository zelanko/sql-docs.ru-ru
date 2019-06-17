---
title: Функция SQLWriteFileDSN | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLWriteFileDSN
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLWriteFileDSN
helpviewer_keywords:
- SQLWriteFileDSN [ODBC]
ms.assetid: 9e18f56f-1061-416b-83d4-ffeec42ab5a9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 58002ec0e8ceacae49f4d54be5d3406ea3014d59
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65536778"
---
# <a name="sqlwritefiledsn-function"></a>Функция SQLWriteFileDSN
**Соответствие стандартам**  
 Представленные версии: ODBC 3.0  
  
 **Сводка**  
 **SQLWriteFileDSN** записывает сведения о файлового имени DSN.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
  
BOOL SQLWriteFileDSN(  
     LPCSTR     lpszFileName,  
     LPCSTR     lpszAppName,  
     LPCSTR     lpszKeyName,  
     LPCSTR     lpszString);  
```  
  
## <a name="arguments"></a>Аргументы  
 *lpszFileName*  
 [Вход] Указатель на имя файла источника данных. Расширение DSN добавляется для всех имен файлов, у вас нет расширение DSN.  
  
 *lpszAppName*  
 [Вход] Указатель на имя приложения. Это «ODBC» в разделе ODBC статьи.  
  
 *lpszKeyName*  
 [Вход] Указатель на имя ключа для чтения. См. в разделе «Комментарии» для зарезервированных ключевых слов.  
  
 *lpszString*  
 [Выход] Указывает строку, связанную с ключом для записи. Максимальная длина строки, на которые указывает этот аргумент составляет 32 767 байтов.  
  
## <a name="returns"></a>Возвращает  
 Функция возвращает значение TRUE при успешном выполнении, FALSE в случае неудачи.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLWriteFileDSN** возвращает значение FALSE, связанным  *\*pfErrorCode* значение можно получить, вызвав **SQLInstallerError**. В следующей таблице перечислены  *\*pfErrorCode* значения, которые могут быть возвращены **SQLInstallerError** и объясняется каждый из них в контексте этой функции.  
  
|*\*pfErrorCode*|Ошибка|Описание|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Ошибки общие установщика|Произошла ошибка для которой нет ошибок определенных установщика.|  
|ODBC_ERROR_INVALID_PATH|Путь установки недопустимый|Путь к имени файла, указанного в *lpszFileName* предоставил недопустимый аргумент.|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|Недопустимый тип запроса|*LpszAppName*, *lpszKeyName*, или *lpszString* аргумент имел значение NULL.|  
  
## <a name="comments"></a>Комментарии  
 ODBC оставляет за собой имя раздела [ODBC], в котором хранятся сведения о соединении. Зарезервированные ключевые слова для этого раздела такие же, как зарезервированный для строки подключения в **SQLDriverConnect**. (Дополнительные сведения см. в разделе [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) описание функции.)  
  
 Приложения могут использовать эти зарезервированные ключевые слова, чтобы записывать сведения непосредственно файлового имени DSN. Если приложению требуется создать или изменить строку соединения, связанный с Источником данных, оно может вызвать **SQLWriteFileDSN** для любого из зарезервированных ключевых слов строки подключения в разделе [ODBC].  
  
 Если *lpszString* аргумент является указателем null, ключевое слово, на которые указывают *lpszKeyName* аргумент будут удалены из файла .dsn. Если *lpszString* и *lpszKeyName* аргументы являются оба пустыми указателями, раздел, на которые указывают *lpszAppName* аргумент будут удалены из файла .dsn.  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Считывание информации из файловых источников данных|[SQLReadFileDSN](../../../odbc/reference/syntax/sqlreadfiledsn-function.md)|
