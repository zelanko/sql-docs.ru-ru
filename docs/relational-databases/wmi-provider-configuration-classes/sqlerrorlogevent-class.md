---
title: SqlErrorLogEvent, класс
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- SqlErrorLogEvent class
- SqlErrorLogFile class
ms.assetid: bde6c467-38d0-4766-a7af-d6c9d6302b07
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: d2a07c87dea5be1a3d66c5e24996a120323d09ce
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85738456"
---
# <a name="sqlerrorlogevent-class"></a>SqlErrorLogEvent, класс
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]
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
 Класс SQLErrorLogEvent определяет следующие свойства.  
  
|||  
|-|-|  
|FileName|Тип данных: **строка**<br /><br /> Тип доступа: только для чтения<br /><br /> <br /><br /> Имя файла журнала ошибок.|  
|InstanceName|Тип данных: **строка**<br /><br /> Тип доступа: только для чтения<br /><br /> Квалификаторы: ключ<br /><br /> Имя экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], на котором хранится файл журнала.|  
|логдате|Тип данных: **DateTime**<br /><br /> Тип доступа: только для чтения<br /><br /> Квалификаторы: ключ<br /><br /> <br /><br /> Дата и время записи события в файл журнала.|  
|Сообщение|Тип данных: **строка**<br /><br /> Тип доступа: только для чтения<br /><br /> <br /><br /> Сообщение о событии.|  
|процессинфо|Тип данных: **строка**<br /><br /> Тип доступа: только для чтения<br /><br /> <br /><br /> Сведения об идентификаторе процесса сервера источника (SPID) события.|  
  
## <a name="remarks"></a>Примечания  
  
|||  
|-|-|  
|MOF|Sqlmgmproviderxpsp2up.mof|  
|DLL|Sqlmgmprovider.dll|  
|Пространство имен|\root\Microsoft\SqlServer\ComputerManagement10|  
  
## <a name="example"></a>Пример  
 В этом примере рассматривается извлечение значений для всех записанных событий в указанном файле журнала. Чтобы выполнить пример, замените \<*Instance_Name*> именем экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , например "instance1", и замените "File_Name" именем файла журнала ошибок, например "ErrorLog. 1".  
  
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
 Если имя *instanceName* или *filename* не указаны в инструкции WQL, запрос возвратит сведения для экземпляра по умолчанию и текущего [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] файла журнала. Например, следующая инструкция WQL вернет все события журнала из текущего файла журнала (ERRORLOG) в текущем экземпляре (MSSQLSERVER).  
  
```  
"SELECT * FROM SqlErrorLogEvent"  
```  
  
## <a name="security"></a>Безопасность  
 Для подключения к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] файлу журнала через инструментарий WMI необходимо иметь следующие разрешения на локальном и на удаленном компьютерах:  
  
-   Доступ на чтение к пространству имен WMI **Root\Microsoft\SqlServer\ComputerManagement10** . По умолчанию доступ для чтения задается для всех с помощью разрешения «Включить учетную запись».  
  
-   Разрешение для чтения на папку, содержащую журналы ошибок. По умолчанию журналы ошибок расположены по следующему пути (где \<*Drive> * обозначает диск, на котором установлен [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , а \<*InstanceName*> — имя экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ):  
  
     ** \<Drive> : \PROGRAM Files\Microsoft SQL Server\MSSQL13** **. \<InstanceName> \MSSQL\Log**  
  
 При соединении с использованием брандмауэра убедитесь, что в брандмауэре задано исключение для WMI на удаленных целевых компьютерах. Дополнительные сведения см. [в статье удаленное подключение к WMI, начиная с Windows Vista](https://go.microsoft.com/fwlink/?LinkId=178848).  
  
## <a name="see-also"></a>См. также  
 [Класс SqlErrorLogFile](../../relational-databases/wmi-provider-configuration-classes/sqlerrorlogfile-class.md)   
 [просматривать файлы журнала в режиме «вне сети»](../../relational-databases/logs/view-offline-log-files.md)  
  
  
