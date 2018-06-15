---
title: ODBCCONF. EXE | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- odbcconf.exe
ms.assetid: 3bf2be83-61f9-4183-836b-85204ac7116a
caps.latest.revision: 23
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8f7a6e48f6a7a17c8ea3decd79d765fb176080e6
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32914309"
---
# <a name="odbcconfexe"></a>ODBCCONF. EXE-ФАЙЛА
ODBCCONF.exe является средством командной строки, которое позволяет настроить ODBC драйверы и имена источников данных.  
  
> [!NOTE]  
>  ODBCCONF.exe будет удален в будущей версии компонентов доступа к данным Windows. Избегайте использования этого компонента и запланируйте изменение приложений, которые сейчас ее используют. Можно использовать команды PowerShell для управления драйверами и источников данных. Дополнительные сведения об этих командах PowerShell см. в разделе [командлеты компонентов доступа к данным Windows](https://technet.microsoft.com/library/hh771019.aspx).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
ODBCCONF [switches] action  
```  
  
## <a name="arguments"></a>Аргументы  
 *Переключатели*  
 Ноль или более параметров. Список доступных параметров см. раздел «Примечания» далее в этом разделе.  
  
 *action*  
 Одно действие для выполнения. Список доступных параметров см. в разделе «Примечания».  
  
## <a name="remarks"></a>Замечания  
 Доступны следующие параметры:  
  
|Параметр|Описание|  
|------------|-----------------|  
|/A {*действия*}|Укажите действие.<br /><br /> /A является необязательным, если задан параметр only одно действие.|  
|/?|Отображает использование для ODBCCONF. EXE-ФАЙЛА.|  
|/C|Обработка продолжается, если действие завершилось ошибкой.|  
|/E|Удаление файла ответов, указанный в параметре /F после завершения обработки.|  
|/F|Использовать файл ответов, таких как `odbcconf /F my.rsp`.<br /><br /> My.rsp может выглядеть следующим образом: `REGSVR c:\my.dll`<br /><br /> /A не используется в файле ответов.|  
|/H|Отображение использования (Справка). Этот параметр является таким же, как /?.|  
|-L [*режим*] *имя файла*|Выходные данные программы отправить файл в одном из трех режимов: обычный (n), подробный (v) и отладки (d). Отладка записей режима библиотек DLL, загружаемых с odbcconf.exe.<br /><br /> При указании /L без режима файл журнала будет пустым.<br /><br /> Например **log.txt регистрируются**.|  
|/R|Действие будет выполнено после перезагрузки.|  
|/S|Режим без вывода сообщений. Не отображать сообщения об ошибках.|  
  
 Доступны следующие действия:  
  
|Действие|Описание|  
|------------|-----------------|  
|CONFIGDRIVER *имя_драйвера ** params конфигурации драйвера*|Загружает DLL-файлов установки соответствующего драйвера и вызовы **ConfigDriver** функции.<br /><br /> Эквивалентно [SQLConfigDriver функция](../odbc/reference/syntax/sqlconfigdriver-function.md).<br /><br /> Например:<br /><br /> /A {CONFIGDRIVER «Имя драйвера» «CPTimeout = 60»}<br /><br /> /A {CONFIGDRIVER «Имя драйвера» «DriverODBCVer = 03.80»}|  
|CONFIGDSN *имя_драйвера* DSN =*имя* &#124; *атрибуты*|Добавляет или изменяет системный источник данных.<br /><br /> Эквивалентно [функция SQLConfigDataSource](../odbc/reference/syntax/sqlconfigdatasource-function.md).<br /><br /> Например:<br /><br /> /A {CONFIGDSN «SQL Server» «DSN = имя &#124; Server = srv»}|  
|CONFIGSYSDSN *имя_драйвера* DSN =*имя* &#124; *атрибуты*|Добавляет или изменяет системный источник данных.<br /><br /> Эквивалентно [функция SQLConfigDataSource](../odbc/reference/syntax/sqlconfigdatasource-function.md).<br /><br /> Например:<br /><br /> /A {CONFIGSYSDSN «SQL Server» «DSN = имя &#124; Server = srv»}|  
|INSTALLDRIVER|Эквивалентно [SQLInstallDriverEx функция](../odbc/reference/syntax/sqlinstalldriverex-function.md).<br /><br /> Сведения о синтаксисе пары значение ключевого слова, передаваемый INSTALLDRIVER см. в разделе [драйвер спецификации подразделов](../odbc/reference/install/driver-specification-subkeys.md).<br /><br /> Например:<br /><br /> /A {INSTALLDRIVER «драйвер &#124; Driver=c:\your.dll &#124; Setup=c:\your.dll &#124; APILevel = 2 &#124; ConnectFunctions = YYY &#124; DriverODBCVer = 03.50 &#124; FileUsage = 0 &#124; SQLLevel = 1»}|  
|INSTALLTRANSLATOR *конфигурации переводчик ** путь к драйверу*|Добавляет сведения о транслятора для **HKEY_LOCAL_MACHINE\SOFTWARE\ODBC\ODBCINST. Трансляторы INI\ODBC** раздел реестра.<br /><br /> Эквивалентно [SQLInstallTranslatorEx функция](../odbc/reference/syntax/sqlinstalltranslatorex-function.md).<br /><br /> Сведения о синтаксисе пары значение ключевого слова, передаваемый INSTALLDRIVER см. в разделе [подразделов спецификации переводчик](../odbc/reference/install/translator-specification-subkeys.md).<br /><br /> Например:<br /><br /> /A {INSTALLTRANSLATOR «My переводчик &#124; Translator=c:\my.dll &#124; Setup=c:\my.dll»}|  
|REGSVR *dll*|Регистрирует библиотеку DLL.<br /><br /> Эквивалентно regsvr32.exe.<br /><br /> Например:<br /><br /> /A {REGSVR c:\my.dll}|  
|SETFILEDSNDIR|Когда HKEY_LOCAL_MACHINE\SOFTWARE\ODBC\ODBC. DSN\DefaultDSNDir INI\ODBC файл не существует, действие SETFILEDSNDIR создаст его и присвойте ей значение в HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\CommonFilesDir, дополненная \ODBC\Data источников.<br /><br /> Значение по HKEY_LOCAL_MACHINE\SOFTWARE\ODBC\ODBC. Файл DSN\DefaultDSNDir INI\ODBC указывает расположение по умолчанию, администратор источников данных ODBC при создании источника данных на основе файлов.<br /><br /> Например:<br /><br /> /A {SETFILEDSNDIR}|  
  
## <a name="see-also"></a>См. также  
 [Microsoft Open Database Connectivity (ODBC)](../odbc/microsoft-open-database-connectivity-odbc.md)
