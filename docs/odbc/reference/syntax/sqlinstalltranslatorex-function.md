---
title: Функция S'LInstallTranslatorEx (англ.) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLInstallTranslatorEx
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLInstallTranslatorEx
helpviewer_keywords:
- SQLInstallTranslatorEx function [ODBC]
ms.assetid: a0630602-53c1-4db0-98ce-70d160aedf8d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5cf52c26bf9e4a26f13a27a0e763fbaa30bd18ec
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302095"
---
# <a name="sqlinstalltranslatorex-function"></a>Функция SQLInstallTranslatorEx
**Соответствия**  
 Представлена версия: ODBC 3.0  
  
 **Сводка**  
 **S'LInstallTranslatorEx** добавляет информацию о переводчике в раздел Odbcinst.ini системной информации (HKEY_LOCAL_MACHINE-SOFTWARE-ODBC-ODBCINST. Ключ к реестру переводчиков ИНИЗБК).  
  
 Функциональность **S'LInstallTranslatorEx** также может быть доступна с [ODBCCONF. EXE](../../../odbc/odbcconf-exe.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
  
BOOL SQLInstallTranslatorEx(  
     LPCSTR    lpszTranslator,  
     LPCSTR    lpszPathIn,  
     LPSTR     lpszPathOut,  
     WORD      cbPathOutMax,  
     WORD *    pcbPathOut,  
     WORD      fRequest,  
     LPDWORD   lpdwUsageCount);  
```  
  
## <a name="arguments"></a>Аргументы  
 *lpszПереводчик*  
 (Вход) Это должно содержать вдвойне нулевой-прекратить список ключевых слов значение пар, описывающих переводчика. Для получения дополнительной информации о синесте пары с ключевыми словами, [см.](../../../odbc/reference/install/translator-specification-subkeys.md)  
  
 Ключевые слова **Переводчика** и **Настройки** должны быть включены в строку *lpszTranslator.* Перевод DLL указан с ключевым словом **Переводчика,** а настройка dLL переводчика указана с ключевым словом **Setup.** Каждая пара завершается с помощью null байта, и весь список прекращается с null байтом. (То есть, два null байта пометить конец списка.) Формат *lpszTranslator* заключается в следующем:  
  
 «0Переводчик»*Переводчик-DLL-filename*(установка)*setup-DLL-filename*  
  
 *lpszPathIn*  
 (Вход) Полный путь, где переводчик должен быть установлен или нулевой указатель. Если *lpszPath* является нулевой указателем, переводчики будут установлены в каталоге системы.  
  
 *lpszPathOut*  
 (Выход) Путь целевого каталога, где должен быть установлен переводчик. Если переводчик никогда не был установлен, *lpszPathOut* такой же, как *lpszPathIn*. Если существует предыдущая установка переводчика, *lpszPathOut* — это путь предыдущей установки.  
  
 *cbPathOutMax*  
 (Вход) Длина *lpszPathOut.*  
  
 *pcbPathOut*  
 (Выход) Общее количество байтов, доступных для возвращения в *lpszPathOut*. Если количество байтов, доступных для возврата, больше или равно *cbPathOutMax,* выходной путь в *lpszPathOut* усечен до *pcbPathOutMax* минус символ нулевого прекращения. Аргумент *pcbPathOut* может быть нулевым указателем.  
  
 *fЗапрос*  
 (Вход) Тип запроса. *fЗапрос* должен содержать одно из следующих значений:  
  
 ODBC_INSTALL_INQUIRY: Узнайте о том, где может быть установлен переводчик.  
  
 ODBC_INSTALL_COMPLETE: Заполните запрос на установку.  
  
 *lpdwUsageCount*  
 (Выход) Количество использования переводчика после вызова этой функции.  
  
 Приложения не должны устанавливать количество использования. ODBC будет поддерживать этот счет.  
  
## <a name="returns"></a>Результаты  
 Функция возвращает TRUE, если она успешна, FALSE, если она не удается.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **S'LInstallTranslatorEx** возвращает FALSE, связанное * \*значение pfErrorCode* можно получить, позвонив по **телефону S'LInstallerError.** В следующей таблице перечислены * \*значения pfErrorCode,* которые могут быть возвращены **S'LInstallerError,** и приведены в изъяны каждое из них в контексте этой функции.  
  
|*\*pfErrorCode*|Error|Описание|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Общая ошибка установки|Произошла ошибка, для которой не было конкретной ошибки установки.|  
|ODBC_ERROR_INVALID_BUFF_LEN|Недействительная длина буфера|Аргумент *lpszPathOut* не был достаточно большим, чтобы содержать путь вывода. Буфер содержит усеченный путь.<br /><br /> Аргумент *cbPathOutMax* был 0, и аргумент *fRequest* был ODBC_INSTALL_COMPLETE.|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|Недействительный тип запроса|Аргумент *fRequest* не был одним из следующих:<br /><br /> ODBC_INSTALL_INQUIRY ODBC_INSTALL_COMPLETE|  
|ODBC_ERROR_INVALID_KEYWORD_VALUE|Недействительные пары значения ключевых слов|Аргумент *lpszTranslator* содержал ошибку синтаксиса.|  
|ODBC_ERROR_INVALID_PATH|Недействительный путь установки|Аргумент *lpszPathIn* содержал недействительный путь.|  
|ODBC_ERROR_INVALID_PARAM_SEQUENCE|Недействительная последовательность параметров|Аргумент *lpszTranslator* не содержал список пар значения ключевых слов.|  
|ODBC_ERROR_USAGE_UPDATE_FAILED|Не уреженное или decrement количество использования компонентов реестра|Установщик не смог приравнить количество использования переводчика.|  
  
## <a name="comments"></a>Комментарии  
 **S'LInstallTranslatorEx** предоставляет механизм для установки только переводчика. Эта функция на самом деле не копирует файлы. Программа вызова отвечает за копирование файлов переводчика.  
  
 **S'LInstallTranslatorTranslatorEx** приращает количество использования компонентов для установленного переводчика на 1. Если версия переводчика уже существует, но количество использования компонентов для переводчика не существует, значение нового значения количества использования компонентов устанавливается на 2.  
  
 Программа настройки приложения отвечает за физическое копирование файла переводчика и поддержание количества использования файла. Если файл переводчика ранее не был установлен, программа настройки приложения должна скопировать файл или файлы и создать количество файлов или файлов. Если файл был ранее установлен, программа настройки просто наращает количество использования файла.  
  
 Если старая версия переводчика была ранее установлена приложением, переводчик должен быть неустановлен, а затем переустановлен, так что количество использования компонента переводчика является действительным. Следует призвать **S'LRemoveTranslator** для decrement количества использования компонентов, а затем следует призвать **S'LInstallTranslatorEx** для приращения количества использования компонентов. Программа настройки приложения должна заменить старый файл или файлы новым файлом. Количество использования файлов останется прежним, и другие приложения, использовавстарый файл старой версии, теперь будут использовать новую версию.  
  
 Длина пути в *lpszPathOut* в **S'LInstallTranslatorEx** позволяет осуществлять двухэтапный процесс установки, поэтому приложение может определить, каким должен быть *cbPathOutMax,* позвонив в режим *fRequest* of ODBC_INSTALL_INQUIRY. **SQLInstallTranslatorEx** Это позволит вернуть общее количество байтов, доступных в буфере *pcbPathOut.* **S'LInstallTranslatorEx** можно тогда назвать *с fЗапрос* ODBC_INSTALL_COMPLETE и *cbPathOutMax* аргумент, установленный на значение в буфере *pcbPathOut,* а также нулевой прекращения характер.  
  
 Если вы решили не использовать двухфазную модель для **S'LInstallTranslatorEx,** необходимо установить *cbPathOutMax*, который определяет размер хранилища для пути целевого каталога, к значению _MAX_PATH, как это определено в Stdlib.h, чтобы предотвратить усечение.  
  
 Когда *fRequest* ODBC_INSTALL_COMPLETE, **S'LInstallTranslatorEx** не позволяет *lpszPathOut* быть NULL (или *cbPathOutMax* быть 0). Если *fRequest* является ODBC_INSTALL_COMPLETE, FALSE возвращается, когда количество байтов, доступных для возврата, больше или равно *cbPathOutMax*, в результате чего происходит усечение.  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Возвращение варианта перевода по умолчанию|[ConfigTranslator](../../../odbc/reference/syntax/configtranslator-function.md)|  
|Выбор переводчиков|[СЗЛГетПереводчик](../../../odbc/reference/syntax/sqlgettranslator-function.md)|  
|Удаление переводчиков|[СЗЛУдалитьПереводчик](../../../odbc/reference/syntax/sqlremovetranslator-function.md)|
