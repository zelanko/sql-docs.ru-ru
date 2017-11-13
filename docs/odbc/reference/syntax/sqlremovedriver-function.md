---
title: "Функция SQLRemoveDriver | Документы Microsoft"
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
- SQLRemoveDriver
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLRemoveDriver
helpviewer_keywords:
- SQLRemoveDriver function [ODBC]
ms.assetid: 9a3b4f8b-982b-44b9-ade6-754ff026dc90
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d191f3ce9d30d241c4d4d37d9961a590ae33817b
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="sqlremovedriver-function"></a>Функция SQLRemoveDriver
**Соответствия**  
 Появился в версии: ODBC 3.0  
  
 **Сводка**  
 **SQLRemoveDriver** изменяет или удаляет сведения о драйвере из файла Odbcinst.ini запись сведений о системе.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
BOOL SQLRemoveDriver(  
     LPCSTR   lpszDriver,  
     BOOL     fRemoveDSN,  
     LPDWORD  lpdwUsageCount);  
```  
  
## <a name="arguments"></a>Аргументы  
 *lpszDriver*  
 [Вход] Имя драйвера, внесенные в раздел реестра Odbcinst.ini информация о системе.  
  
 *fRemoveDSN*  
 [Вход] Допустимыми значениями являются:  
  
 Значение TRUE: Удаление источников данных, связанные с драйвером, указанный в *lpszDriver*. FALSE: Не удаляйте источников данных, связанные с драйвером, указанный в *lpszDriver*.  
  
 *lpdwUsageCount*  
 [Выход] Счетчик использования драйвера после вызова этой функции.  
  
## <a name="returns"></a>Возвращает  
 Функция возвращает значение TRUE, если он прошел успешно, FALSE в случае неудачи. Если не существует запись сведений о системе при вызове этой функцией, функция возвращает значение FALSE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLRemoveDriver** возвращает значение FALSE, связанный с ним  *\*pfErrorCode* значение можно получить путем вызова **SQLInstallerError**. В следующей таблице перечислены  *\*pfErrorCode* значения, которые могут быть возвращены **SQLInstallerError** и описание каждого из них в контексте этой функции.  
  
|*\*pfErrorCode*|Ошибка|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Установщик Общие ошибки|Произошла ошибка для которого нет ошибок определенного установщика.|  
|ODBC_ERROR_COMPONENT_NOT_FOUND|Компонент не найден в реестре|Программа установки не удалось удалить сведения о драйвере, поскольку не существует в реестре или не найден в реестре.|  
|ODBC_ERROR_INVALID_NAME|Недопустимое имя драйвера или преобразователь|*LpszDriver* недопустимый аргумент.|  
|ODBC_ERROR_USAGE_UPDATE_FAILED|Не удалось увеличить или уменьшить загруженность в компонент|Программа установки не удалось уменьшить значение счетчика использования драйвера.|  
|ODBC_ERROR_REQUEST_FAILED|Не удалось выполнить запрос|*FRemoveDSN* аргумент имеет значение TRUE; тем не менее, не удалось удалить один или несколько источников данных. Вызов **SQLConfigDriver** с запросом ODBC_REMOVE_DRIVER сбой.|  
|ODBC_ERROR_OUT_OF_MEM|Недостаточно памяти|Программе установки не удалось выполнить функцию из-за нехватки памяти.|  
  
## <a name="comments"></a>Комментарии  
 **SQLRemoveDriver** дополняет [SQLInstallDriverEx](../../../odbc/reference/syntax/sqlinstalldriverex-function.md) функции и обновления использование компонентов количество сведений о системе. Эта функция должна вызываться только из программы установки приложения.  
  
 **SQLRemoveDriver** будет уменьшить значение счетчика использования компонента на 1. Если счетчик использования компонента становится равным 0, произойдет следующее:  
  
1.  **SQLConfigDriver** функцию с параметром ODBC_REMOVE_DRIVER будет вызываться. Если *fRemoveDSN* параметр имеет значение TRUE, **ConfigDSN** вызовов функций **SQLRemoveDSNFromIni** для удаления всех источников данных, связанные с драйвером, указанный в *lpszDriver.* Если *fRemoveDSN* параметр имеет значение FALSE, источники данных не будут удалены.  
  
2.  Будет удален драйвер запись сведений о системе. Запись драйвер находится в следующем расположении сведения системы, под именем драйвера:  
  
     `HKEY_LOCAL_MACHINE`  
  
     `SOFTWARE`  
  
     `ODBC`  
  
     `Odbcinst.ini`  
  
 **SQLRemoveDriver** фактически не удалять файлы. Вызывающая программа отвечает за удаление файлов и обслуживание счетчик использования файла. Только после достижения счетчик использования компонента и число файлов использования ноль — это файл, в физически удаляются. Можно удалить некоторые файлы, в компоненте и другие не удален, в зависимости от того, используются ли файлы другим приложениям, которые увеличивается на единицу счетчик использования файла.  
  
 **SQLRemoveDriver** также вызывается как часть процесса обновления. Если приложение обнаруживает, что он должен выполнить обновление, и ранее установил драйвера, драйвер следует удалить и переустановить. **SQLRemoveDriver** сначала должен вызываться для уменьшения числа использования компонента, а затем **SQLInstallDriverEx** должен вызываться увеличивается счетчик использования компонента. Программа установки необходимо заменить старые файлы новых файлов. Счетчик использования файл остается без изменений и других приложений, использующих более старые версии файлов теперь будут использовать новую версию.  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Добавление, изменение или удаление драйвера|[ConfigDriver](../../../odbc/reference/syntax/configdriver-function.md) (в DLL-файлов установки)|  
|Добавление, изменение или удаление драйвера|[SQLConfigDriver](../../../odbc/reference/syntax/sqlconfigdriver-function.md)|  
|Установка драйвера|[SQLInstallDriverEx](../../../odbc/reference/syntax/sqlinstalldriverex-function.md)|

