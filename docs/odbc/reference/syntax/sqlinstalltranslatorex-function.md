---
title: "Функция SQLInstallTranslatorEx | Документы Microsoft"
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
- SQLInstallTranslatorEx
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLInstallTranslatorEx
helpviewer_keywords:
- SQLInstallTranslatorEx function [ODBC]
ms.assetid: a0630602-53c1-4db0-98ce-70d160aedf8d
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 241cb92786626bfc4674426c67f099f4349a6cb4
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="sqlinstalltranslatorex-function"></a>Функция SQLInstallTranslatorEx
**Соответствия**  
 Появился в версии: ODBC 3.0  
  
 **Сводка**  
 **SQLInstallTranslatorEx** добавляет сведения о трансляции Odbcinst.ini часть сведений о системе (HKEY_LOCAL_MACHINE\SOFTWARE\ODBC\ODBCINST. INI\ODBC трансляторы раздел реестра).  
  
 Функциональные возможности **SQLInstallTranslatorEx** можно получить с помощью [ODBCCONF. EXE](../../../odbc/odbcconf-exe.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
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
 [Вход] Этот элемент должен содержать двойной завершающий список пар ключевое слово значение, описывающее преобразователь. Дополнительные сведения о синтаксисе пары ключ значение см. в разделе [подразделов спецификации переводчик](../../../odbc/reference/install/translator-specification-subkeys.md).  
  
 **Переводчик** и **установки** ключевые слова должны быть включены в *lpszTranslator* строка. Перевод отмечены DLL **переводчик** ключевое слово и настройки транслятора отмечены DLL **установки** ключевое слово. Каждая пара заканчивается байт NULL, и завершается весь список байт NULL. (То есть два байта NULL пометить конец списка). Формат *lpszTranslator* выглядит следующим образом:  
  
 \0Translator=*имя файла DLL переводчик*\0[Setup=*имя файла DLL установки*\0]\0  
  
 *lpszPathIn*  
 [Вход] Полный путь к которой должна быть установлена транслятор или является пустым указателем. Если *lpszPath* является указателем null трансляторы будут установлены в системном каталоге.  
  
 *lpszPathOut*  
 [Выход] Путь к целевой каталог для установки преобразователь. Если транслятор никогда не установлены, *lpszPathOut* совпадает со значением *lpszPathIn*. Если существует перед установкой транслятор, *lpszPathOut* путь к предыдущей установки.  
  
 *cbPathOutMax*  
 [Вход] Длина *lpszPathOut.*  
  
 *pcbPathOut*  
 [Выход] Общее число байтов, доступных для возврата в *lpszPathOut*. Если количество байтов, доступных для возврата больше или равно *cbPathOutMax*, выходной путь в *lpszPathOut* усекается до *pcbPathOutMax* минус знак завершения NULL. *PcbPathOut* аргумент может быть пустой указатель.  
  
 *fRequest*  
 [Вход] Тип запроса. *fRequest* должен содержать один из следующих значений:  
  
 ODBC_INSTALL_INQUIRY: Запрос по установленным преобразователя.  
  
 ODBC_INSTALL_COMPLETE: Завершите запрос на установку.  
  
 *lpdwUsageCount*  
 [Выход] Загруженность переводчик после вызова этой функции.  
  
 Приложение не может установить счетчик использования. ODBC поддерживает это число.  
  
## <a name="returns"></a>Возвращает  
 Функция возвращает значение TRUE, если он прошел успешно, FALSE в случае неудачи.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLInstallTranslatorEx** возвращает значение FALSE, связанный с ним * \*pfErrorCode* значение можно получить путем вызова **SQLInstallerError**. В следующей таблице перечислены * \*pfErrorCode* значения, которые могут быть возвращены **SQLInstallerError** и описание каждого из них в контексте этой функции.  
  
|*\*pfErrorCode*|Ошибка|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Установщик Общие ошибки|Произошла ошибка для которого нет ошибок определенного установщика.|  
|ODBC_ERROR_INVALID_BUFF_LEN|Недопустимый буфер длины|*LpszPathOut* аргумент не может быть достаточно большим, чтобы содержать выходной путь. Буфер содержит путь к усечению.<br /><br /> *CbPathOutMax* аргумент было равно 0 и *fRequest* аргумент был ODBC_INSTALL_COMPLETE.|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|Недопустимый тип запроса|*FRequest* аргумент не является одним из следующих:<br /><br /> ODBC_INSTALL_INQUIRY ODBC_INSTALL_COMPLETE|  
|ODBC_ERROR_INVALID_KEYWORD_VALUE|Пары "недопустимое ключевое слово значение"|*LpszTranslator* аргумент содержит синтаксическую ошибку.|  
|ODBC_ERROR_INVALID_PATH|Путь установки недопустимый|*LpszPathIn* аргумент содержит неправильный путь.|  
|ODBC_ERROR_INVALID_PARAM_SEQUENCE|Недопустимый параметр последовательности|*LpszTranslator* аргумент не содержит список пар «ключевое слово значение».|  
|ODBC_ERROR_USAGE_UPDATE_FAILED|Не удалось увеличить или уменьшить загруженность компонент реестра|Установщику не удалось увеличить счетчик использования преобразователя.|  
  
## <a name="comments"></a>Комментарии  
 **SQLInstallTranslatorEx** предоставляет механизм для установки только преобразователь. Эта функция фактически не копирует все файлы. Для копирования файлов переводчик отвечает вызывающей программе.  
  
 **SQLInstallTranslatorEx** увеличивает счетчик использования компонента установленных переводчик на 1. Если уже существует версия транслятор, но счетчик использования компонента преобразователь не существует, новое значение счетчика использования компонента имеет значение 2.  
  
 Программа установки отвечает за физически копирования файла преобразователь и обслуживания счетчик использования файла. Если файл переводчик ранее не была установлена, программа установки необходимо скопировать файл или файлы и создать файл или файлы, счетчик использования. Если файл был ранее установлен, программа установки просто увеличивает счетчик использования файла.  
  
 Если более старой версии преобразователь был ранее установлен приложением, преобразователь следует удалить и переустановить, таким образом, счетчик использования компонента переводчик допустимым. **SQLRemoveTranslator** должен вызываться для уменьшения числа использования компонента, а затем **SQLInstallTranslatorEx** должен вызываться увеличивается счетчик использования компонента. Программа установки необходимо заменить старый файл или файлы с новым файлом. Счетчик использования файл остается без изменений и других приложений, которые используются более старые версии файла теперь будет использовать более новую версию.  
  
 Длина пути в *lpszPathOut* в **SQLInstallTranslatorEx** позволяет процессом двухфазной установки, поэтому приложение может определить, что *cbPathOutMax* следует быть вызовом **SQLInstallTranslatorEx** с *fRequest* ODBC_INSTALL_INQUIRY режима. Возвращает общее количество байтов, доступных в *pcbPathOut* буфера. **SQLInstallTranslatorEx** затем может быть вызван с *fRequest* из ODBC_INSTALL_COMPLETE и *cbPathOutMax* аргументу присвоено значение в *pcbPathOut* буфера, а также знак завершения null.  
  
 Если вы решили не использовать двухфазной модель для **SQLInstallTranslatorEx**, необходимо задать *cbPathOutMax*, который определяет размер хранилища для пути целевой каталог, чтобы значение _MAX_PATH, как определен в Stdlib.h, чтобы не допустить усечения.  
  
 Когда *fRequest* — ODBC_INSTALL_COMPLETE, **SQLInstallTranslatorEx** не допускает *lpszPathOut* равным NULL (или *cbPathOutMax* значение 0). Если *fRequest* является ODBC_INSTALL_COMPLETE, FALSE возвращается, если количество байтов, доступных для возврата больше или равно *cbPathOutMax*, в результате происходит усечение.  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Возвращает параметр преобразования по умолчанию|[ConfigTranslator](../../../odbc/reference/syntax/configtranslator-function.md)|  
|При выборе трансляторы|[SQLGetTranslator](../../../odbc/reference/syntax/sqlgettranslator-function.md)|  
|Удаление трансляторы|[SQLRemoveTranslator](../../../odbc/reference/syntax/sqlremovetranslator-function.md)|
