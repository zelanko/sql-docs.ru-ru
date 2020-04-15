---
title: Функция S'LReadFiledSN Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3abda956ee7682c9ac49270e8bf69fb039641790
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303955"
---
# <a name="sqlreadfiledsn-function"></a>Функция SQLReadFileDSN
**Соответствия**  
 Представлена версия: ODBC 3.0  
  
 **Сводка**  
 **СЗЛРидЕДиДСН** считывает информацию из файла DSN.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
  
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
 (Вход) Указатель на буфер данных, содержащий имя файла .dsn. Расширение .dsn прибавывается ко всем именам файлов, которые еще не имеют расширения .dsn. Значение в * \*lpszFileName* должно быть строкой с нулевым завершением.  
  
 *lpszAppName*  
 (Вход) Указатель на буфер данных, содержащий имя приложения. Это "ODBC" для раздела ODBC. Значение в * \*lpszAppName* должно быть нулевой строки.  
  
 *lpszKeyName*  
 (Вход) Указатель на буфер данных, содержащий имя ключа для чтения. Смотрите "Комментарии" для зарезервированных ключевых слов. Значение в * \*lpszAppName* должно быть нулевой строки.  
  
 *lpszString*  
 (Выход) Указатель на буфер данных, содержащий строку, связанную с ключом для чтения.  
  
 Если * \*lpszFileName* является действительным именем файла .dsn, но аргумент *lpszAppName* является нулевой указателем, а аргумент *lpszKeyName* является нулевой указателем, то * \*lpszString* содержит список действительных приложений. Если * \*lpszFileName* является действительным имени файла .dsn и * \*lpszAppName* является действительным именем приложения, но *lpszKeyName* аргумент нулевой указатель, то * \*lpszString* содержит список действительных зарезервированных ключевых слов в соответствующем разделе файла DSN, делимитированный полуколоннами. Если * \*lpszFileName* является действительным именем файла .dsn, но * \*lpszAppName* является нулевой указатель и *lpszKeyName* аргумент нулевой указатель, то * \*lpszString* содержит список разделов в файле DSN, делимитированных запятых.  
  
 *cbString*  
 (Вход) Длина буфера * \*lpszString.*  
  
 *pcbString*  
 (Выход) Общее количество байтов, доступных для возвращения в * \*lpszString*. Если количество байтов, доступных для возврата, больше или равно *cbString,* строка вывода в * \*lpszString* усечена до *cbString* минус символ нулевого прекращения. Аргумент *pcbString* может быть нулевым указателем.  
  
## <a name="returns"></a>Результаты  
 Функция возвращает TRUE, если она успешна, FALSE, если она не удается.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **S'LReadFileDSN** возвращает FALSE, связанное * \*значение pfErrorCode* можно получить, позвонив по **телефону S'LInstallerError.** В следующей таблице перечислены * \*значения pfErrorCode,* которые могут быть возвращены **S'LInstallerError,** и приведены в изъяны каждое из них в контексте этой функции.  
  
|*\*pfErrorCode*|Error|Описание|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Общая ошибка установки|Произошла ошибка, для которой не было конкретной ошибки установки.|  
|ODBC_ERROR_INVALID_BUFF_LEN|Недействительная длина буфера|*LpszString* аргумент был NULL.<br /><br /> Аргумент *cbString* был меньше или равен 0.|  
|ODBC_ERROR_INVALID_PATH|Недействительный путь установки|Путь имени файла, указанный в аргументе *lpszFileName,* был недействительным.|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|Недействительный тип запроса|Аргумент *lpszAppName* был NULL, в то время как аргумент *lpszKeyName* был действительным.|  
|ODBC_ERROR_OUT_OF_MEM|Недостаточно памяти|Установщик не мог выполнить функцию из-за отсутствия памяти.|  
|ODBC_ERROR_OUTPUT_STRING_TRUNCATED|Выходная строка усечена|Строка, возвращенная в * \*lpszString,* была усечена, потому что значение в *cbString* было меньше или равно значению в * \*pcbString.*|  
|ODBC_ERROR_REQUEST_FAILED|Не удалось выполнить запрос|Ключевое слово не существует в файле DSN.|  
  
## <a name="comments"></a>Комментарии  
 ODBC оставляет за собой название раздела «ODBC», в котором можно хранить информацию о подключении. Зарезервированные ключевые слова для этого раздела такие же, как те, которые зарезервированы для строки подключения в **S'LDriverConnect.** (Для получения дополнительной [информации,](../../../odbc/reference/syntax/sqldriverconnect-function.md) см.  
  
 Приложения могут использовать эти зарезервированные ключевые слова для чтения информации в файле DSN. Если приложения хотят узнать строку соединения DSN-less, связанную с файлом DSN, она может вызвать **S'LReadFileDSN** для любого из зарезервированных ключевых слов строки соединения в разделе «ODBC». Строка полного соединения, пройденного в соединении DSN-less, представляет собой комбинацию всех ключевых слов (зарезервированных и конкретных драйверов) в разделе «ODBC».  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Запись информации в файл DSN|[СЗЛСрайтФилдсн](../../../odbc/reference/syntax/sqlwritefiledsn-function.md)|
