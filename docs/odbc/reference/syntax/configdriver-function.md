---
title: "Функция ConfigDriver | Документы Microsoft"
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
- ConfigDriver
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- ConfigDriver
helpviewer_keywords:
- ConfigDriver [ODBC]
ms.assetid: 9473f48f-bcae-4784-89c1-7839bad4ed13
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 037d4ffcbe7d81c6e4a9c1a524f5f4977621f277
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="configdriver-function"></a>Функция ConfigDriver
**Соответствия**  
 Версии появился: ODBC 2.5  
  
 **Сводка**  
 **ConfigDriver** позволяет программы установки для выполнения установки и удаления без необходимости программу для вызова функции **ConfigDSN**. Эта функция будет выполнять драйвера функции, такие как создание сведений о системе, относящиеся к драйверу и преобразований DSN во время установки, а также Очистка изменения сведения системы во время удаления. Эта функция предоставляется с DLL-файлов установки драйверов или отдельный DLL-файлов установки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
BOOL ConfigDriver(  
      HWND    hwndParent,  
      WORD    fRequest,  
      LPCSTR  lpszDriver,  
      LPCSTR  lpszArgs,  
      LPSTR   lpszMsg,  
      WORD    cbMsgMax,  
      WORD *  pcbMsgOut);  
```  
  
## <a name="arguments"></a>Аргументы  
 *hwndParent*  
 [Вход] Дескриптор родительского окна. Функция не будет отображать все диалоговые окна, если маркер имеет значение null.  
  
 *fRequest*  
 [Вход] Тип запроса. *FRequest* аргумент должен иметь один из следующих значений:  
  
 ODBC_INSTALL_DRIVER: Установки нового драйвера.  
  
 ODBC_REMOVE_DRIVER: Удалите драйвер.  
  
 Этот параметр также может быть специфические для драйвера, в этом случае *fRequest* аргументом для первого параметра должно начинаться с ODBC_CONFIG_DRIVER_MAX + 1. *FRequest* аргумент для любой дополнительный параметр также необходимо запускать с значение больше ODBC_CONFIG_DRIVER_MAX + 1.  
  
 *lpszDriver*  
 [Вход] Имя драйвера, внесенные в раздел реестра Odbcinst.ini информация о системе.  
  
 *lpszArgs*  
 [Вход] Нулем строка, содержащая аргументы для конкретного драйвера *fRequest*.  
  
 *lpszMsg*  
 [Выход] Нулем строка, содержащая выходного сообщения из установки драйвера.  
  
 *cbMsgMax*  
 [Вход] Длина *lpszMsg*.  
  
 *pcbMsgOut*  
 [Выход] Общее число байтов, доступных для возврата в *lpszMsg*.  
  
 Если количество байтов, доступных для возврата больше или равно *cbMsgMax*, выходное сообщение в *lpszMsg* усекается до *cbMsgMax* минус конечное значение null символ. *PcbMsgOut* аргумент может быть пустой указатель.  
  
## <a name="returns"></a>Возвращает  
 Функция возвращает значение TRUE, если он прошел успешно, FALSE в случае неудачи.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **ConfigDriver** возвращает значение FALSE, связанный с ним * \*pfErrorCode* значение передается буфера установщика ошибок с помощью вызова **SQLPostInstallerError** его можно получить, вызвав **SQLInstallerError**. В следующей таблице перечислены * \*pfErrorCode* значения, которые могут быть возвращены **SQLInstallerError** и описание каждого из них в контексте этой функции.  
  
|*\*pfErrorCode*|Ошибка|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_INVALID_HWND|Недопустимый дескриптор окна|*HwndParent* недопустимый аргумент.|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|Недопустимый тип запроса|*FRequest* аргумент не является одним из следующих:<br /><br /> ODBC_INSTALL_DRIVER ODBC_REMOVE_DRIVER<br /><br /> Параметр драйвера была меньше или равно ODBC_CONFIG_DRIVER_MAX.|  
|ODBC_ERROR_INVALID_NAME|Недопустимое имя драйвера или преобразователь|*LpszDriver* недопустимый аргумент. Он не найден в реестре.|  
|ODBC_ERROR_REQUEST_FAILED|*Запрос* сбой|Не удалось выполнить операцию, запрошенную *fRequest* аргумент.|  
|ODBC_ERROR_DRIVER_SPECIFIC|Ошибка драйвера или преобразователь|Ошибка драйвера, для которого нет определенных ошибок установщика ODBC. *SzError* аргумента в вызове **SQLPostInstallerError** функция должна содержать сообщении об ошибке драйвера.|  
  
## <a name="comments"></a>Комментарии  
  
### <a name="driver-specific-options"></a>Параметры драйвера  
 Приложение может запросить драйвера возможностям, предоставляемым драйвером с помощью *fRequest* аргумент. *FRequest* для первого параметра будут ODBC_CONFIG_DRIVER_MAX плюс 1, а дополнительные параметры увеличивается на 1 с этого значения. Все аргументы, необходимую драйверу для этой функции должно быть задано в строку, завершающуюся символом null, переданные в *lpszArgs* аргумент. Драйверы, добавляя такие функциональные возможности, необходимо поддерживать таблицу параметров, зависящих от драйвера. Параметры должны быть полностью описаны в документации по драйверу. Программисты, использующие параметры драйвера следует иметь в виду, что это сделает приложения менее безопасная.  
  
### <a name="messages"></a>Сообщения  
 Подпрограмма установки драйвера можно отправить текстовое сообщение приложению, завершающуюся значением null в виде строки *lpszMsg* буфера. Сообщение будет усечен до *cbMsgMax* минус символу конечное значение null по **ConfigDriver** функционировать, если оно больше или равно *cbMsgMax* символов.

