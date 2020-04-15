---
title: Функция S'LWriteFiledSN Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e781f1be79e0079f33b3d0800c665f5f5e9fda4d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81286894"
---
# <a name="sqlwritefiledsn-function"></a>Функция SQLWriteFileDSN
**Соответствия**  
 Представлена версия: ODBC 3.0  
  
 **Сводка**  
 **СЗЛУКВИКПойДСН** записывает информацию в файл DSN.  
  
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
 (Вход) Указатель на название файла DSN. Расширение DSN прибавывается ко всем именам файлов, которые еще не имеют расширения DSN.  
  
 *lpszAppName*  
 (Вход) Указатель на название приложения. Это "ODBC" для раздела ODBC.  
  
 *lpszKeyName*  
 (Вход) Указатель на название ключа, который нужно прочитать. Смотрите "Комментарии" для зарезервированных ключевых слов.  
  
 *lpszString*  
 (Выход) Указано на строку, связанную с ключом, который будет написан. Максимальная длина строки, на которую указывает этот аргумент, составляет 32 767 байтов.  
  
## <a name="returns"></a>Результаты  
 Функция возвращает TRUE, если она успешна, FALSE, если она не удается.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **S'LWriteFileDSN** возвращает FALSE, связанное * \*значение pfErrorCode* можно получить, позвонив по **телефону S'LInstallerError.** В следующей таблице перечислены * \*значения pfErrorCode,* которые могут быть возвращены **S'LInstallerError,** и приведены в изъяны каждое из них в контексте этой функции.  
  
|*\*pfErrorCode*|Error|Описание|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Общая ошибка установки|Произошла ошибка, для которой не было конкретной ошибки установки.|  
|ODBC_ERROR_INVALID_PATH|Недействительный путь установки|Путь имени файла, указанный в аргументе *lpszFileName,* был недействительным.|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|Недействительный тип запроса|*lpszAppName*, *lpszKeyName*, или *lpszString* аргумент был NULL.|  
  
## <a name="comments"></a>Комментарии  
 ODBC оставляет за собой название раздела «ODBC», в котором можно хранить информацию о подключении. Зарезервированные ключевые слова для этого раздела такие же, как те, которые зарезервированы для строки подключения в **S'LDriverConnect.** (Для получения дополнительной [информации,](../../../odbc/reference/syntax/sqldriverconnect-function.md) см.  
  
 Приложения могут использовать эти зарезервированные ключевые слова для записи информации непосредственно в файл DSN. Если приложение хочет создать или изменить строку соединения DSN-less, связанную с файлом DSN, оно может вызвать **S'LWriteFileDSN** для любого из зарезервированных ключевых слов строки соединения в разделе «ODBC».  
  
 Если аргумент *lpszString* является нулевой указателем, ключевое слово, на которое указывает аргумент *lpszKeyName,* будет удалено из файла .dsn. Если аргументы *lpszString* и *lpszKeyName* являются нулевыми указателями, раздел, на который указывает аргумент *lpszAppName,* будет удален из файла .dsn.  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Чтение информации из файлов DSN|[СЗЛРедРедЕДСН](../../../odbc/reference/syntax/sqlreadfiledsn-function.md)|
