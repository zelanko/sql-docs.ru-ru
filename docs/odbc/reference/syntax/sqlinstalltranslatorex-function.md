---
title: Функция SQLInstallTranslatorEx | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 57a2fb53226af9aeb6e546f6109a3e182ffc754f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65536556"
---
# <a name="sqlinstalltranslatorex-function"></a>Функция SQLInstallTranslatorEx
**Соответствие стандартам**  
 Представленные версии: ODBC 3.0  
  
 **Сводка**  
 **SQLInstallTranslatorEx** добавляет сведения о переводчика разделе Odbcinst.ini информация о системе (HKEY_LOCAL_MACHINE\SOFTWARE\ODBC\ODBCINST. INI\ODBC переводчиков раздел реестра).  
  
 Функциональные возможности **SQLInstallTranslatorEx** также может осуществляться с помощью [ODBCCONF. EXE](../../../odbc/odbcconf-exe.md).  
  
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
 *lpszTranslator*  
 [Вход] Этот элемент должен содержать список пар "ключевое слово значение", описывающий переводчик двумя двоичными нулями. Дополнительные сведения о синтаксисе пары значение ключевого слова см. в разделе [подразделы спецификаций преобразователей](../../../odbc/reference/install/translator-specification-subkeys.md).  
  
 **Translator** и **установки** ключевые слова, которые должны быть включены в *lpszTranslator* строка. Преобразование библиотеки DLL находится в списке **Translator** ключевое слово и установки translator, отмечены DLL **установки** ключевое слово. Каждая пара заканчивается байт NULL, и завершается по всему списку байт NULL. (То есть два байта NULL обозначения конца списка.) Формат *lpszTranslator* выглядит следующим образом:  
  
 \0Translator=*имя файла DLL translator*\0[Setup=*имя файла DLL программы установки*\0]\0  
  
 *lpszPathIn*  
 [Вход] Полный путь к которой должна быть установлена переводчик или является пустым указателем. Если *lpszPath* является пустым указателем, переводчику будет устанавливаться в системном каталоге.  
  
 *lpszPathOut*  
 [Выход] Путь к целевой каталог, где должен быть установлен переводчик. Если никогда не будет установлен переводчик, *lpszPathOut* совпадает со значением *lpszPathIn*. Если существует хотя бы с предыдущей версией переводчик, *lpszPathOut* — это путь перед установкой.  
  
 *cbPathOutMax*  
 [Вход] Длина *lpszPathOut.*  
  
 *pcbPathOut*  
 [Выход] Общее число байтов, доступных для возврата в *lpszPathOut*. Если количество байтов, доступных для возврата больше или равно *cbPathOutMax*, выходной путь в *lpszPathOut* усекается до *pcbPathOutMax* минус символ завершения NULL. *PcbPathOut* аргументом может быть пустым указателем.  
  
 *fRequest*  
 [Вход] Тип запроса. *fRequest* должен содержать один из следующих значений:  
  
 ODBC_INSTALL_INQUIRY: Запрос установки преобразователя.  
  
 ODBC_INSTALL_COMPLETE: Выполните запрос на установку.  
  
 *lpdwUsageCount*  
 [Выход] Счетчик использования преобразователь после вызова этой функции.  
  
 Приложения, не задавайте счетчик использования. ODBC будет поддерживать этот счетчик.  
  
## <a name="returns"></a>Возвращает  
 Функция возвращает значение TRUE при успешном выполнении, FALSE в случае неудачи.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLInstallTranslatorEx** возвращает значение FALSE, связанным  *\*pfErrorCode* значение можно получить, вызвав **SQLInstallerError**. В следующей таблице перечислены  *\*pfErrorCode* значения, которые могут быть возвращены **SQLInstallerError** и объясняется каждый из них в контексте этой функции.  
  
|*\*pfErrorCode*|Ошибка|Описание|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Ошибки общие установщика|Произошла ошибка для которой нет ошибок определенных установщика.|  
|ODBC_ERROR_INVALID_BUFF_LEN|Недопустимый буфер длины|*LpszPathOut* аргумент не был достаточно велик, чтобы содержать выходной путь. Буфер содержит усеченное путь.<br /><br /> *CbPathOutMax* аргумент было равно 0 и *fRequest* аргумент был ODBC_INSTALL_COMPLETE.|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|Недопустимый тип запроса|*FRequest* аргумент не является одним из следующих:<br /><br /> ODBC_INSTALL_INQUIRY ODBC_INSTALL_COMPLETE|  
|ODBC_ERROR_INVALID_KEYWORD_VALUE|Пары "недопустимое ключевое слово значение"|*LpszTranslator* аргумент содержит синтаксическую ошибку.|  
|ODBC_ERROR_INVALID_PATH|Путь установки недопустимый|*LpszPathIn* аргумент содержит недопустимый путь.|  
|ODBC_ERROR_INVALID_PARAM_SEQUENCE|Недопустимый параметр последовательности|*LpszTranslator* аргумент не содержит список пар "ключевое слово значение".|  
|ODBC_ERROR_USAGE_UPDATE_FAILED|Не удалось увеличить или уменьшить загруженность компонент реестра|Установщику не удалось увеличить счетчик использования translator.|  
  
## <a name="comments"></a>Комментарии  
 **SQLInstallTranslatorEx** предоставляет механизм для установки просто translator. Эта функция фактически не копирует все файлы. Для копирования файлов translator отвечает вызывающей программе.  
  
 **SQLInstallTranslatorEx** увеличивает счетчик использования компонента установленных переводчик на 1. Если уже существует версия переводчик, но счетчик использования компонента переводчик не существует, новое значение счетчика использования компонента имеет значение 2.  
  
 Программа установки физически копирование файла перевода и поддержание счетчик использования файла. Если файл translator ранее не были установлены, программа установки необходимо скопировать файл или файлы и создать файл или файлы, счетчик использования. Если файл был ранее установлен, программа установки просто увеличивает счетчик использования файла.  
  
 Если более старой версии преобразователь был ранее установлен приложением, переводчик следует удалить и переустановить, таким образом, счетчик использования translator компонент допустимым. **SQLRemoveTranslator** должен вызываться для уменьшения счетчик использования компонента, а затем **SQLInstallTranslatorEx** должен вызываться следует выполнить приращение счетчика использования компонента. Программа установки необходимо заменить старый файл или файлы с новым файлом. Счетчик использования файла остается неизменным, и другие приложения, использующие более старые версии файла теперь будет использовать более новой версии.  
  
 Длина пути в *lpszPathOut* в **SQLInstallTranslatorEx** позволяет двухфазной установки, поэтому приложение может определить, какие *cbPathOutMax* следует быть вызовом **SQLInstallTranslatorEx** с *fRequest* ODBC_INSTALL_INQUIRY режима. Эта команда возвращает общее число байтов, доступных в *pcbPathOut* буфера. **SQLInstallTranslatorEx** затем может быть вызван с *fRequest* из ODBC_INSTALL_COMPLETE и *cbPathOutMax* аргументу присвоено значение в *pcbPathOut* буфера, а также знак завершения null.  
  
 Если вы решили не использовать двухэтапной модели для **SQLInstallTranslatorEx**, необходимо задать *cbPathOutMax*, который определяет объем хранилища для пути в целевой каталог, чтобы значение _MAX_PATH, как определен в Stdlib.h, чтобы предотвратить усечение.  
  
 Когда *fRequest* является ODBC_INSTALL_COMPLETE, **SQLInstallTranslatorEx** не допускает *lpszPathOut* значение NULL (или *cbPathOutMax* Чтобы иметь значение 0). Если *fRequest* является ODBC_INSTALL_COMPLETE, FALSE возвращается, если количество байтов, доступных для возврата больше или равно *cbPathOutMax*, в результате этого усечение происходит.  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Возвращение является параметром по умолчанию перевода|[ConfigTranslator](../../../odbc/reference/syntax/configtranslator-function.md)|  
|Выбрав переводчиков|[SQLGetTranslator](../../../odbc/reference/syntax/sqlgettranslator-function.md)|  
|Удаление переводчиков|[SQLRemoveTranslator](../../../odbc/reference/syntax/sqlremovetranslator-function.md)|
