---
title: "Функция SQLInstallDriverManager | Документы Microsoft"
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
- SQLInstallDriverManager
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLInstallDriverManager
helpviewer_keywords:
- SQLInstallDriverManager function [ODBC]
ms.assetid: aebc439b-fffd-4d98-907a-0163f79aee8d
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 6bc56b9045ae3f9a53b410ef0546d539e3c25ee8
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="sqlinstalldrivermanager-function"></a>Функция SQLInstallDriverManager
**Соответствия**  
 Версии впервые введенная версии: ODBC 1.0: не рекомендуется на пакет обновления 2 для Windows XP, Windows Server 2003 с пакетом обновления 1 и более поздних операционных системах  
  
 **Сводка**  
 **SQLInstallDriverManager** возвращает путь конечной папки для установки основных компонентов ODBC. Фактически вызывающей программе необходимо скопировать файлы диспетчера драйверов в конечный каталог.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
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
 [Выход] Общее число байтов (за исключением байтов конечное значение null) возвращается в *lpszPath*. Если количество байтов, доступных для возврата больше или равно *cbPathMax*, путь в *lpszPath* усекается до *cbPathMax* минус конечное значение null символ. *PcbPathOut* аргумент может быть пустой указатель.  
  
## <a name="returns"></a>Возвращает  
 Функция возвращает значение TRUE, если он прошел успешно, FALSE в случае неудачи.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLInstallDriverManager** возвращает значение FALSE, связанный с ним * \*pfErrorCode* значение можно получить путем вызова **SQLInstallerError**. В следующей таблице перечислены * \*pfErrorCode* значения, которые могут быть возвращены **SQLInstallerError** и описание каждого из них в контексте этой функции.  
  
|*\*pfErrorCode*|Ошибка|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Установщик Общие ошибки|Произошла ошибка для которого нет ошибок определенного установщика.|  
|ODBC_ERROR_INVALID_BUFF_LEN|Недопустимый буфер длины|*LpszPath* аргумент не может быть достаточно большим, чтобы содержать выходной путь. Буфер содержит путь к усечению.<br /><br /> *CbPathMax* аргумент был меньше, чем _MAX_PATH.|  
|ODBC_ERROR_USAGE_UPDATE_FAILED|Не удалось увеличить или уменьшить загруженность в компонент|Установщику не удалось увеличить счетчик использования компонента основных компонентов ODBC.|  
|ODBC_ERROR_OUT_OF_MEM|Недостаточно памяти|Программе установки не удалось выполнить функцию из-за нехватки памяти.|  
  
## <a name="comments"></a>Комментарии  
 **SQLInstallDriverManager** вызывается для получения пути для основных компонентов ODBC и увеличивать использование компонентов количество сведений о системе. Если версия диспетчера драйверов уже существует, но драйвер счетчик использования компонента не существует, новое значение счетчика использования компонента имеет значение 2.  
  
 Программа установки отвечает физически копирования файлов компонентов ядра и подсчитывает обслуживание использования файла. Если файл компонента ядра ранее не была установлена, программа установки необходимо скопировать файл и создать счетчик использования файла. Если файл был ранее установлен, программа установки просто увеличивает счетчик использования файла.  
  
 Если более старые версии диспетчера драйверов уже установлена, программа установки приложения, основные компоненты следует удалить и переустановить, таким образом, счетчик использования основных компонентов допустимым. **SQLRemoveDriverManager** сначала должен вызываться для уменьшения числа использования компонента. **SQLInstallDriverManager** должен быть вызван, затем, чтобы увеличить счетчик использования компонента. Программа установки необходимо заменить старый основные файлы компонента новые файлы. Счетчики использования файл остается без изменений, и другие приложения, которые используются более старые версии основные файлы компонента теперь будет использовать более новые версии файлов.  
  
 В установку основных компонентов ODBC, драйверов и переводчикам, программа установки следует вызывать следующие функции в последовательности: **SQLInstallDriverManager**, **SQLInstallDriverEx**, **SQLConfigDriver** (с *fRequest* из ODBC_INSTALL_DRIVER), а затем **SQLInstallTranslatorEx**. Удаление основных компонентов, драйверов и переводчикам, программа установки должен вызывать следующие функции в последовательности: **SQLRemoveTranslator**, **SQLRemoveDriver**, а затем **SQLRemoveDriverManager**. Эти функции должны вызываться в этой последовательности. При обновлении всех компонентов все функции удаления должен быть вызван в последовательности и затем все функции установки должен быть вызван в последовательности.  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Добавление, изменение или удаление драйвера|[SQLConfigDriver](../../../odbc/reference/syntax/sqlconfigdriver-function.md)|  
|Установка драйвера|[SQLInstallDriverEx](../../../odbc/reference/syntax/sqlinstalldriverex-function.md)|  
|Установка переводчика|[SQLInstallTranslatorEx](../../../odbc/reference/syntax/sqlinstalltranslatorex-function.md)|  
|Удаление драйвера|[SQLRemoveDriver](../../../odbc/reference/syntax/sqlremovedriver-function.md)|  
|Удаление диспетчера драйверов|[SQLRemoveDriverManager](../../../odbc/reference/syntax/sqlremovedrivermanager-function.md)|  
|Удаление переводчика|[SQLRemoveTranslator](../../../odbc/reference/syntax/sqlremovetranslator-function.md)|

