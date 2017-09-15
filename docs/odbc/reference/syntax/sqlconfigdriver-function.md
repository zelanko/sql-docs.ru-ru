---
title: "Функция SQLConfigDriver | Документы Microsoft"
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
- SQLConfigDriver
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLConfigDriver
helpviewer_keywords:
- SQLConfigDriver function [ODBC]
ms.assetid: 4f681961-ac9f-4d88-b065-5258ba112642
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9dd30a466fefda6f8b100fdd9595e9ab65e4d85f
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="sqlconfigdriver-function"></a>Функция SQLConfigDriver
**Соответствия**  
 Версии появился: ODBC 2.5  
  
 **Сводка**  
 **SQLConfigDriver** загружает DLL-файлов установки соответствующего драйвера и вызовы **ConfigDriver** функции.  
  
 Функциональные возможности **SQLConfigDriver** можно получить с помощью [ODBCCONF. EXE](../../../odbc/odbcconf-exe.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
BOOL SQLConfigDriver(  
     HWND     hwndParent,  
     WORD     fRequest,  
     LPCSTR   lpszDriver,  
     LPCSTR   lpszArgs,  
     LPSTR    lpszMsg,  
     WORD     cbMsgMax,  
     WORD *   pcbMsgOut);  
```  
  
## <a name="arguments"></a>Аргументы  
 *hwndParent*  
 [Вход] Дескриптор родительского окна. Функция не будет отображать все диалоговые окна, если маркер имеет значение null.  
  
 *fRequest*  
 [Вход] Тип запроса. *fRequest* должен содержать один из следующих значений:  
  
 ODBC_CONFIG_DRIVER: Изменяет драйвер использует время ожидания пула подключений.  
  
 ODBC_INSTALL_DRIVER: Устанавливает новый драйвер.  
  
 ODBC_REMOVE_DRIVER: Удаляет существующего драйвера.  
  
 Этот параметр также может быть специфические для драйвера, в этом случае *fRequest* для первого параметра должно начинаться с ODBC_CONFIG_DRIVER_MAX + 1. *FRequest* для любой дополнительный параметр также необходимо запускать с значение больше ODBC_CONFIG_DRIVER_MAX + 1.  
  
 *lpszDriver*  
 [Вход] Имя драйвера, зарегистрированным в сведениях о системе.  
  
 *lpszArgs*  
 [Вход] Строка, содержащая аргументы для конкретного драйвера нулем *fRequest*.  
  
 *lpszMsg*  
 [Выход] Нулем строка, содержащая выходного сообщения из установки драйвера.  
  
 *cbMsgMax*  
 [Вход] Длина *lpszMsg.*  
  
 *pcbMsgOut*  
 [Выход] Общее число байтов, доступных для возврата в *lpszMsg*. Если количество байтов, доступных для возврата больше или равно *cbMsgMax*, выходное сообщение в *lpszMsg* усекается до *cbMsgMax* минус конечное значение null символ. *PcbMsgOut* аргумент может быть пустой указатель.  
  
## <a name="returns"></a>Возвращает  
 Функция возвращает значение TRUE, если он прошел успешно, FALSE в случае неудачи.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLConfigDriver** возвращает значение FALSE, связанный с ним * \*pfErrorCode* значение можно получить путем вызова **SQLInstallerError**. В следующей таблице перечислены * \*pfErrorCode* значения, которые могут быть возвращены **SQLInstallerError** и описание каждого из них в контексте этой функции.  
  
|*\*pfErrorCode*|Ошибка|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Установщик Общие ошибки|Произошла ошибка для которого нет ошибок определенного установщика.|  
|ODBC_ERROR_INVALID_BUFF_LEN|Недопустимый буфер длины|*LpszMsg* недопустимый аргумент.|  
|ODBC_ERROR_INVALID_HWND|Недопустимый дескриптор окна|*HwndParent* недопустимый аргумент.|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|Недопустимый тип запроса|*FRequest* аргумент не является одним из следующих:<br /><br /> ODBC_INSTALL_DRIVER ODBC_REMOVE_DRIVER<br /><br /> *FRequest* аргумент был параметр драйвера, который был меньше или равно ODBC_CONFIG_DRIVER_MAX.|  
|ODBC_ERROR_INVALID_NAME|Недопустимое имя драйвера или преобразователь|*LpszDriver* недопустимый аргумент. Он не найден в реестре.|  
|ODBC_ERROR_INVALID_KEYWORD_VALUE|Пары "недопустимое ключевое слово значение"|*LpszArgs* аргумент содержит синтаксическую ошибку.|  
|ODBC_ERROR_REQUEST_FAILED|*Запрос* сбой|Программе установки не удалось выполнить операцию, запрошенную *fRequest* аргумент. Вызов **ConfigDriver** сбой.|  
|ODBC_ERROR_LOAD_LIBRARY_FAILED|Не удалось загрузить библиотеку установки драйвера или преобразователь|Не удается загрузить библиотеку установки драйвера.|  
|ODBC_ERROR_OUT_OF_MEM|Недостаточно памяти|Программе установки не удалось выполнить функцию из-за нехватки памяти.|  
  
## <a name="comments"></a>Комментарии  
 **SQLConfigDriver** позволяет приложению вызывать драйвер **ConfigDriver** сопоставление без необходимости знать имя и загрузить DLL-файлов установки драйвера. Программа установки вызывает эту функцию после установки драйвера, установленного DLL. Вызывающая программа следует иметь в виду, что эта функция не могут быть доступны для всех драйверов. В этом случае вызывающая программа должна продолжать работу без ошибок.  
  
## <a name="driver-specific-options"></a>Параметры драйвера  
 Приложение может запросить драйвера возможностям, предоставляемым драйвером с помощью *fRequest* аргумент. *FRequest* для первого параметра будут ODBC_CONFIG_DRIVER_MAX + 1, а дополнительные параметры увеличивается на 1 с этого значения. Все аргументы, необходимую драйверу для этой функции должно быть задано в строку, завершающуюся символом null, переданные в *lpszArgs* аргумент. Драйверы, добавляя такие функциональные возможности, необходимо поддерживать таблицу параметров, зависящих от драйвера. Параметры должны быть полностью описаны в документации по драйверу. Программисты, использующие параметры драйвера следует иметь в виду, что такое использование сделает приложения менее безопасная.  
  
## <a name="setting-connection-pooling-timeout"></a>Установка времени ожидания пула подключений  
 При задании конфигурации драйвера, можно задать свойства времени ожидания пула подключений. **SQLConfigDriver** вызывается с *fRequest* из ODBC_CONFIG_DRIVER и *lpszArgs* значение **CPTimeout**. **CPTimeout** определяет период времени, соединение может оставаться в пуле соединений без использования. После истечения времени ожидания, соединение закрывается и удален из пула. Время ожидания по умолчанию составляет 60 секунд.  
  
 Когда **SQLConfigDriver** вызывается с *fRequest* значение ODBC_INSTALL_DRIVER или ODBC_REMOVE_DRIVER, диспетчер драйверов загружает DLL-файлов установки соответствующего драйвера и вызовы ** ConfigDriver** функции. Когда **SQLConfigDriver** вызывается с *fRequest* из ODBC_CONFIG_DRIVER, вся обработка выполняется установщика ODBC, чтобы для загрузки DLL-файлов установки драйвера нет.  
  
## <a name="messages"></a>Сообщения  
 Подпрограмма установки драйвера можно отправить текстовое сообщение приложению в нули в *lpszMsg* буфера. Сообщение будет усечен до *cbMsgMax* минус символу конечное значение null по **ConfigDriver** функционировать, если оно больше или равно *cbMsgMax* символов.  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Добавление, изменение или удаление драйвера|[ConfigDriver](../../../odbc/reference/syntax/configdriver-function.md)(в DLL-файлов установки)|  
|Удаление источника данных по умолчанию|[SQLRemoveDefaultDataSource](../../../odbc/reference/syntax/sqlremovedefaultdatasource-function.md)|
