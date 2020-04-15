---
title: ОДБККОН. EXE Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d771f01d292312f8a0f0060c16e3c348bf2e009e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307535"
---
# <a name="odbcconfexe"></a>ОДБККОН. Exe
ODBCCONF.exe — это командный инструмент, позволяющий настраивать драйверы ODBC и имена источников данных.  
  
> [!NOTE]  
>  ODBCCONF.exe будет удален в будущей версии компонентов доступа к данным Windows. Избегайте использования этой функции и планируйте изменить приложения, использующие эту функцию в настоящее время. Команды PowerShell можно использовать для управления драйверами и источниками данных. Для получения дополнительной информации об [Windows Data Access Components cmdlets](/powershell/module/wdac)этих командах PowerShell см.  
  
## <a name="syntax"></a>Синтаксис  
  
```console  
ODBCCONF [switches] action  
```  
  
## <a name="arguments"></a>Аргументы  
 *Переключатели*  
 Нулевые или более вариантов коммутатора. Список доступных коммутаторов можно найти в разделе Замечания, а затем в этой теме.  
  
 *Действий*  
 Одно действие для выполнения. Список доступных опций можно найти в разделе Замечания.  
  
## <a name="remarks"></a>Remarks  
 Доступны следующие переключатели:  
  
|Параметр|Описание|  
|------------|-----------------|  
|/A *- действие*|Укажите действие.<br /><br /> /A является необязательным, если указано только одно действие.|  
|/?|Использование дисплея для ODBCCONF. Exe.|  
|/C|Обработка продолжается, если действие выполняется неудачей.|  
|/E|Стереть файл ответа, указанный с /F, когда обработка закончена.|  
|/F|Используйте файл ответа, `odbcconf /F my.rsp`например .<br /><br /> my.rsp может выглядеть следующим образом:`REGSVR c:\my.dll`<br /><br /> /A не используется в файле ответа.|  
|/H|Использование дисплея (Справка). Этот переключатель такой же, как /?.|  
|режим L*mode* *filename*|Отправка вывода программы в файл в одном из трех режимов: нормальный (n), многословный (v) и отладка (d). Режим debug записывает DLL, загруженные odbcconf.exe.<br /><br /> Если вы укажете /L без режима, файл журнала будет пуст.<br /><br /> Например, **/Lv log.txt**.|  
|/R|Действие будет выполнено после перезагрузки.|  
|/S|Автоматический режим Не отображайте сообщения об ошибках.|  
  
 Доступны следующие варианты действий.  
  
|Действие|Описание|  
|------------|-----------------|  
|Конфигурация конфигурации кОНФИГКРЕВЕР *driver_name*|Загружает соответствующую установку драйвера DLL и вызывает функцию **ConfigDriver.**<br /><br /> Эквивалент [функции S'LConfigDriver.](../odbc/reference/syntax/sqlconfigdriver-function.md)<br /><br /> Пример:<br /><br /> /A КОНКЛИГВЕПРОМ "Имя водителя" "CPTimeout No60"<br /><br /> /A "КОНФИКСПРОИ" Имя водителя "ВодительODBCVer-03.80"|  
|&#124; *атрибуты* *&#124; имя* кОНГИДСН *driver_name* DSN|Добавляет или изменяет источник системных данных.<br /><br /> Эквивалент [функции S'LConfigDataSource](../odbc/reference/syntax/sqlconfigdatasource-function.md).<br /><br /> Пример:<br /><br /> /A (КОНФИГДСН "Сервер СЗЛ" "DSN'name &#124; Сервера""|  
|*driver_name* &#124; *атрибуты* *&#124;*|Добавляет или изменяет источник системных данных.<br /><br /> Эквивалент [функции S'LConfigDataSource](../odbc/reference/syntax/sqlconfigdatasource-function.md).<br /><br /> Пример:<br /><br /> /A (КОНФИКСССССДСН" "Сервер" "DSN'name &#124; Сервера""|  
|INSTALLDRIVER|Эквивалент [функции S'LInstallDriverDriverEx](../odbc/reference/syntax/sqlinstalldriverex-function.md).<br /><br /> Для получения информации о синтаксисе пар с [Driver Specification Subkeys](../odbc/reference/install/driver-specification-subkeys.md)ключевым и значением, передаваемых INSTALLDRIVER, см.<br /><br /> Пример:<br /><br /> /A "INSTALLDRIVER" Ваш водитель &#124; Драйвер:"Your.dll &#124; Setup'c: "Your.dll &#124; APILevel-2 &#124; ConnectFunctions-YYY &#124; DriverODBCVer-03.50 &#124; FileUsage-0 &#124; S'LLevel|  
|INSTALLTRANSLATOR *конфигурация переводчика »драйвер путь*|Добавляет информацию об переводчике в **HKEY_LOCAL_MACHINE-SOFTWARE-ODBC-ODBCINST. Ключ к реестру переводчиков ИНИЗБК.**<br /><br /> Эквивалент [функции S'LInstallTranslatorEx](../odbc/reference/syntax/sqlinstalltranslatorex-function.md).<br /><br /> Для получения информации о синтаксисе пар с [Translator Specification Subkeys](../odbc/reference/install/translator-specification-subkeys.md)ключевым и значением, передаваемых INSTALLDRIVER, см.<br /><br /> Пример:<br /><br /> /А "INSTALLTRANSLATOR" Мой переводчик &#124; Переводчик: "my.dll &#124; Setup'c: "my.dll"|  
|REGSVR *dll*|Регистрирует DLL.<br /><br /> Эквивалент regsvr32.exe.<br /><br /> Пример:<br /><br /> /А «РЕГСВР c:»my.dll|  
|SETFILEDSNDIR|При HKEY_LOCAL_MACHINE-ПРОГРАММНО-ОДБК-ОДБК. INI-ODBC Файл DSN-DefaultDSNDir не существует, setFILEDSNDIR действий создаст его и назначить его значение на HKEY_LOCAL_MACHINE»SOFTWARE-Microsoft-Microsoft-Windows-CurrentВерсия -CommonFilesDir, добавленный с "ODBC"Источники данных.<br /><br /> Значение по HKEY_LOCAL_MACHINE-SOFTWARE-ODBC. InI-ODBC File DSN-DefaultDSNDir определяет местоположение по умолчанию, используемое администратором источника данных ODBC при создании источника данных на основе файлов.<br /><br /> Пример:<br /><br /> /А "SETFILEDSNDIR"|  
  
## <a name="see-also"></a>См. также:  
 [Microsoft Open Database Connectivity (ODBC)](../odbc/microsoft-open-database-connectivity-odbc.md)
