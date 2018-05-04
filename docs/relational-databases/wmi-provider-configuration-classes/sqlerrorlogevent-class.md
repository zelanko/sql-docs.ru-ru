---
title: SqlErrorLogEvent, класс | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: wmi
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SqlErrorLogEvent class
- SqlErrorLogFile class
ms.assetid: bde6c467-38d0-4766-a7af-d6c9d6302b07
caps.latest.revision: 14
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 77ffaff3db702d94d5010d27627685b1d5e88473
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sqlerrorlogevent-class"></a>SqlErrorLogEvent, класс
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Предоставляет свойства для просмотра события в указанном файле журнала [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
class SQLErrorLogEvent   
{  
   stringFileName;  
   stringInstanceName;  
   datetimeLogDate;  
   stringMessage;  
   stringProcessInfo;  
};  
```  
  
## <a name="properties"></a>Свойства  
 SQLErrorLogEvent, класс определяет следующие свойства.  
  
|||  
|-|-|  
|FileName|Тип данных: **строка**<br /><br /> Тип доступа: только для чтения<br /><br /> <br /><br /> Имя файла журнала ошибок.|  
|InstanceName|Тип данных: **строка**<br /><br /> Тип доступа: только для чтения<br /><br /> Квалификаторы: ключ<br /><br /> Имя экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], на котором хранится файл журнала.|  
|LogDate|Тип данных: **даты и времени**<br /><br /> Тип доступа: только для чтения<br /><br /> Квалификаторы: ключ<br /><br /> <br /><br /> Дата и время записи события в файл журнала.|  
|Сообщение|Тип данных: **строка**<br /><br /> Тип доступа: только для чтения<br /><br /> <br /><br /> Сообщение о событии.|  
|ProcessInfo|Тип данных: **строка**<br /><br /> Тип доступа: только для чтения<br /><br /> <br /><br /> Сведения об идентификаторе процесса сервера источника (SPID) события.|  
  
## <a name="remarks"></a>Замечания  
  
|||  
|-|-|  
|MOF|Sqlmgmproviderxpsp2up.mof|  
|DLL-библиотеки|Sqlmgmprovider.dll|  
|Пространство имен|\root\Microsoft\SqlServer\ComputerManagement10|  
  
## <a name="example"></a>Пример  
 В этом примере рассматривается извлечение значений для всех записанных событий в указанном файле журнала. Чтобы запустить пример, замените \< *имя_экземпляра*> с именем экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], например «Экземпляр1», а «имя_файла» с именем файла журнала ошибок, например «ErrorLog.1».  
  
```  
on error resume next  
strComputer = "."  
Set objWMIService = GetObject("winmgmts:" _  
    & "{impersonationLevel=impersonate}!\\" _  
    & strComputer & "\root\MICROSOFT\SqlServer\ComputerManagement10")  
set logEvents = objWmiService.ExecQuery("SELECT * FROM SqlErrorLogEvent WHERE InstanceName = '<Instance_Name>' AND FileName = 'File_Name'")  
  
For Each logEvent in logEvents  
WScript.Echo "Instance Name: " & logEvent.InstanceName & vbNewLine _  
    & "Log Date: " & logEvent.LogDate & vbNewLine _  
    & "Log File Name: " & logEvent.FileName & vbNewLine _  
    & "Process Info: " & logEvent.ProcessInfo & vbNewLine _  
    & "Message: " & logEvent.Message & vbNewLine _  
  
Next  
```  
  
## <a name="comments"></a>Комментарии  
 Когда *InstanceName* или *FileName* не указаны в инструкции WQL, запрос вернет информацию для экземпляра по умолчанию и текущий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] файла журнала. Например следующая инструкция WQL вернет все события журнала из текущего файла журнала (ERRORLOG) на экземпляре по умолчанию (MSSQLSERVER).  
  
```  
"SELECT * FROM SqlErrorLogEvent"  
```  
  
## <a name="security"></a>безопасность  
 Для подключения к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] файла журнала посредством инструментария WMI, необходимо иметь следующие разрешения на локальных и удаленных компьютеров:  
  
-   Доступ на чтение к **Root\Microsoft\SqlServer\ComputerManagement10** пространство имен WMI. По умолчанию доступ для чтения задается для всех с помощью разрешения «Включить учетную запись».  
  
-   Разрешение для чтения на папку, содержащую журналы ошибок. По умолчанию ошибки журналы находятся по следующему пути (где \< *диска >* представляет диск, на котором установлена [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и \< *InstanceName*> — Имя экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]):  
  
     **\<Диск >: \Program Files\Microsoft SQL Server\MSSQL13** **.\< Имя_экземпляра > \MSSQL\Log**  
  
 При соединении с использованием брандмауэра убедитесь, что в брандмауэре задано исключение для WMI на удаленных целевых компьютерах. Дополнительные сведения см. в разделе [подключение к WMI, начиная с Windows Vista удаленно](http://go.microsoft.com/fwlink/?LinkId=178848).  
  
## <a name="see-also"></a>См. также  
 [SqlErrorLogFile, класс](../../relational-databases/wmi-provider-configuration-classes/sqlerrorlogfile-class.md)   
 [Просмотр автономных файлов журнала](../../relational-databases/logs/view-offline-log-files.md)  
  
  
