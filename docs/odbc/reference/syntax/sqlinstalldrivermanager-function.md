---
title: Функция SQLInstallDriverManager | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLInstallDriverManager
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLInstallDriverManager
helpviewer_keywords:
- SQLInstallDriverManager function [ODBC]
ms.assetid: aebc439b-fffd-4d98-907a-0163f79aee8d
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1f1e3ac7f0a76c607fa07d6eb92d069d99ef5e0a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68076213"
---
# <a name="sqlinstalldrivermanager-function"></a>Функция SQLInstallDriverManager
**Соответствие стандартам**  
 Представленные версии: ODBC 1.0. Рекомендуется использовать в Windows XP с пакетом обновления 2, пакет обновления 1 для Windows Server 2003 и более поздних операционных системах  
  
 **Сводка**  
 **SQLInstallDriverManager** возвращает путь к целевой каталог для установки основных компонентов ODBC. Фактически, вызывающей программе необходимо скопировать файлы диспетчера драйверов в целевой каталог.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
  
BOOL SQLInstallDriverManager(  
     LPSTR    lpszPath,  
     WORD     cbPathMax,  
     WORD *   pcbPathOut);  
```  
  
## <a name="arguments"></a>Аргументы  
 *lpszPath*  
 [Выход] Путь к целевой каталог установки.  
  
 *cbPathMax*  
 [Вход] Длина *lpszPath*. Это должен быть по крайней мере _MAX_PATH байт.  
  
 *pcbPathOut*  
 [Выход] Общее число байтов (за исключением байтов конечное значение null) возвращаются в *lpszPath*. Если количество байтов, доступных для возврата больше или равно *cbPathMax*, путь в *lpszPath* усекается до *cbPathMax* минус конечное значение null символ. *PcbPathOut* аргументом может быть пустым указателем.  
  
## <a name="returns"></a>Возвращает  
 Функция возвращает значение TRUE при успешном выполнении, FALSE в случае неудачи.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLInstallDriverManager** возвращает значение FALSE, связанным  *\*pfErrorCode* значение можно получить, вызвав **SQLInstallerError**. В следующей таблице перечислены *\*pfErrorCode* значения, которые могут быть возвращены **SQLInstallerError** и объясняется каждый из них в контексте этой функции.  
  
|*\*pfErrorCode*|Ошибка|Описание|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Ошибки общие установщика|Произошла ошибка для которой нет ошибок определенных установщика.|  
|ODBC_ERROR_INVALID_BUFF_LEN|Недопустимый буфер длины|*LpszPath* аргумент не был достаточно велик, чтобы содержать выходной путь. Буфер содержит усеченное путь.<br /><br /> *CbPathMax* аргумент был меньше, чем _MAX_PATH.|  
|ODBC_ERROR_USAGE_UPDATE_FAILED|Не удалось увеличить или уменьшить счетчик использования компонента|Установщику не удалось увеличить счетчик использования компонента core ODBC.|  
|ODBC_ERROR_OUT_OF_MEM|Недостаточно памяти|Программа установки не удалось выполнить функцию из-за нехватки памяти.|  
  
## <a name="comments"></a>Комментарии  
 **SQLInstallDriverManager** вызывается для получения пути для основных компонентов ODBC и шага приращения использование компонентов подсчета в сведениях о системе. Если версия диспетчера драйверов уже существует, но счетчик использования компонент драйвера не существует, новое значение счетчика использования компонента имеет значение 2.  
  
 Программа установки несет ответственность за физически копирование основные файлы компонента и поддержка использования файла подсчитывает. Если файл core-компонент ранее не были установлены, программа установки необходимо скопировать файл и создать счетчик использования файла. Если файл был ранее установлен, программа установки просто увеличивает счетчик использования файла.  
  
 Если более старой версии диспетчера драйверов ранее был установлен программой установки приложения, основные компоненты следует удалить и переустановить, таким образом, счетчик использования основных компонентов допустимым. **SQLRemoveDriverManager** сначала должен вызываться для уменьшения счетчик использования компонента. **SQLInstallDriverManager** необходимо также вызвать следует выполнить приращение счетчика использования компонента. Программа установки необходимо заменить старые файлы компонента core новые файлы. Счетчики использования файла остается неизменным, и другие приложения, использующие более старые версии основные файлы компонента теперь будет использовать более новые версии файлов.  
  
 В новой установки основных компонентов ODBC, драйверов и преобразователей программа установки должен вызывать следующие функции в последовательности: **SQLInstallDriverManager**, **SQLInstallDriverEx**, **SQLConfigDriver** (с *fRequest* из ODBC_INSTALL_DRIVER), а затем  **SQLInstallTranslatorEx**. Отменить установку основных компонентов, драйверы и преобразователей программа установки должен вызывать следующие функции в последовательности: **SQLRemoveTranslator**, **SQLRemoveDriver**, а затем **SQLRemoveDriverManager**. Эти функции должен вызываться в этой последовательности. Выполняется обновление всех компонентов все функции удаления должен вызываться в последовательности и затем все функции установки должны вызываться в последовательности.  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Добавление, изменение или удаление драйвера.|[SQLConfigDriver](../../../odbc/reference/syntax/sqlconfigdriver-function.md)|  
|Установка драйвера|[SQLInstallDriverEx](../../../odbc/reference/syntax/sqlinstalldriverex-function.md)|  
|Установка переводчика|[SQLInstallTranslatorEx](../../../odbc/reference/syntax/sqlinstalltranslatorex-function.md)|  
|Удаление драйвера.|[SQLRemoveDriver](../../../odbc/reference/syntax/sqlremovedriver-function.md)|  
|Удаление диспетчера драйверов|[SQLRemoveDriverManager](../../../odbc/reference/syntax/sqlremovedrivermanager-function.md)|  
|Удаление переводчика|[SQLRemoveTranslator](../../../odbc/reference/syntax/sqlremovetranslator-function.md)|
