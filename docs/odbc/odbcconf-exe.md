---
title: ODBCCONF. EXE-ФАЙЛА | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- odbcconf.exe
ms.assetid: 3bf2be83-61f9-4183-836b-85204ac7116a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 33688a46be5e5e33aa940f3553c98db5091b159d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47765462"
---
# <a name="odbcconfexe"></a>ODBCCONF. EXE-ФАЙЛА
ODBCCONF.exe является средством командной строки, которое позволяет настроить ODBC драйверы и имена источников данных.  
  
> [!NOTE]  
>  ODBCCONF.exe будет поддерживаться в будущих версиях Windows Data Access Components. Избегайте использования этой функции и запланируйте изменение приложений, которые сейчас ее используют. Можно использовать команды PowerShell для управления драйверами и источников данных. Дополнительные сведения об этих командах PowerShell см. в разделе [командлеты компонентов доступа к данным Windows](https://technet.microsoft.com/library/hh771019.aspx).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
ODBCCONF [switches] action  
```  
  
## <a name="arguments"></a>Аргументы  
 *Коммутаторы*  
 Ноль или более параметров. Список доступных параметров см. в разделе "Примечания" Далее в этом разделе.  
  
 *action*  
 Одно действие для выполнения. Список доступных параметров см. в разделе "Примечания".  
  
## <a name="remarks"></a>Примечания  
 Доступны следующие параметры:  
  
|Параметр|Описание|  
|------------|-----------------|  
|/A {*действие*}|Укажите действие.<br /><br /> /A является необязательным, если только одно действие.|  
|/?|Отображает использование для ODBCCONF. EXE-ФАЙЛА.|  
|/C|Обработка продолжается, если действие завершилось ошибкой.|  
|/E|Стереть файл ответа, заданный параметром /F, после завершения обработки.|  
|/F|Использовать файл ответов, таких как `odbcconf /F my.rsp`.<br /><br /> My.rsp может выглядеть следующим образом: `REGSVR c:\my.dll`<br /><br /> /A не используется в файле ответов.|  
|/H|Отобразить использование (Справка). Этот параметр является таким же, как /?.|  
|/ L [*режим*] *имя файла*|Отправить выходные данные программы в файл в одном из трех режимов: обычный (n), verbose (v) и отладки (d). Отладка записей режима библиотеки DLL, загружаемых с odbcconf.exe.<br /><br /> При указании/l без режима файла журнала будет пустым.<br /><br /> Например **log.txt регистрируются**.|  
|/R|Действие выполняется после перезагрузки.|  
|/S|Режим без вывода сообщений. Не отображать сообщения об ошибках.|  
  
 Доступны следующие действия:  
  
|Действие|Описание|  
|------------|-----------------|  
|CONFIGDRIVER *имя_драйвера ** params конфигурации драйвера*|Загружает DLL-файлов установки соответствующего драйвера и вызовы **ConfigDriver** функции.<br /><br /> Эквивалентно [функция SQLConfigDriver](../odbc/reference/syntax/sqlconfigdriver-function.md).<br /><br /> Пример:<br /><br /> /A {CONFIGDRIVER «Имя драйвера» «CPTimeout = 60»}<br /><br /> /A {CONFIGDRIVER «Имя драйвера» «DriverODBCVer = 03.80»}|  
|CONFIGDSN *имя_драйвера* DSN =*имя* &#124; *атрибуты*|Добавляет или изменяет системный источник данных.<br /><br /> Эквивалентно [функция SQLConfigDataSource](../odbc/reference/syntax/sqlconfigdatasource-function.md).<br /><br /> Пример:<br /><br /> /A {CONFIGDSN «SQL Server» «DSN = имя &#124; Server = srv»}|  
|CONFIGSYSDSN *имя_драйвера* DSN =*имя* &#124; *атрибуты*|Добавляет или изменяет системный источник данных.<br /><br /> Эквивалентно [функция SQLConfigDataSource](../odbc/reference/syntax/sqlconfigdatasource-function.md).<br /><br /> Пример:<br /><br /> /A {CONFIGSYSDSN «SQL Server» «DSN = имя &#124; Server = srv»}|  
|INSTALLDRIVER|Эквивалентно [функция SQLInstallDriverEx](../odbc/reference/syntax/sqlinstalldriverex-function.md).<br /><br /> Сведения о синтаксисе пары ключевое_слово значение, передаваемое INSTALLDRIVER см. в разделе [подразделы спецификаций драйверов](../odbc/reference/install/driver-specification-subkeys.md).<br /><br /> Пример:<br /><br /> /A {INSTALLDRIVER «драйвер &#124; Driver=c:\your.dll &#124; Setup=c:\your.dll &#124; APILevel = 2 &#124; ConnectFunctions = YYY &#124; DriverODBCVer = 03.50 &#124; FileUsage = 0 &#124; SQLLevel = 1»}|  
|INSTALLTRANSLATOR *translator конфигурации ** пути драйвера*|Добавляет сведения о translator, чтобы **HKEY_LOCAL_MACHINE\SOFTWARE\ODBC\ODBCINST. Переводчики INI\ODBC** раздел реестра.<br /><br /> Эквивалентно [функция SQLInstallTranslatorEx](../odbc/reference/syntax/sqlinstalltranslatorex-function.md).<br /><br /> Сведения о синтаксисе пары ключевое_слово значение, передаваемое INSTALLDRIVER см. в разделе [подразделы спецификаций преобразователей](../odbc/reference/install/translator-specification-subkeys.md).<br /><br /> Пример:<br /><br /> /A {INSTALLTRANSLATOR «Мои Translator &#124; Translator=c:\my.dll &#124; Setup=c:\my.dll»}|  
|REGSVR *dll*|Регистрирует библиотеки DLL.<br /><br /> Эквивалент regsvr32.exe.<br /><br /> Пример:<br /><br /> /A {REGSVR c:\my.dll}|  
|SETFILEDSNDIR|Когда HKEY_LOCAL_MACHINE\SOFTWARE\ODBC\ODBC. DSN\DefaultDSNDir INI\ODBC файл не существует, действие SETFILEDSNDIR создаст его и присвойте ей значение в HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\CommonFilesDir, дополненный \ODBC\Data источников.<br /><br /> Значение по HKEY_LOCAL_MACHINE\SOFTWARE\ODBC\ODBC. Файл DSN\DefaultDSNDir INI\ODBC указывает расположение по умолчанию, администратор источников данных ODBC при создании источника данных на основе файла.<br /><br /> Пример:<br /><br /> /A {SETFILEDSNDIR}|  
  
## <a name="see-also"></a>См. также  
 [Microsoft Open Database Connectivity (ODBC)](../odbc/microsoft-open-database-connectivity-odbc.md)
