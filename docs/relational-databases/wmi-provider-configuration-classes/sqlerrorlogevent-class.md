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
ms.openlocfilehash: f77b7a36e51d08aa3ae82b5d42e28b0173d750cb
ms.sourcegitcommit: baa40306cada09e480b4c5ddb44ee8524307a2ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/06/2019
ms.locfileid: "73659020"
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
 Класс SQLErrorLogEvent определяет следующие свойства.  
  
|||  
|-|-|  
|FileName|Тип данных: **строка**<br /><br /> Тип доступа: только для чтения<br /><br /> <br /><br /> Имя файла журнала ошибок.|  
|InstanceName|Тип данных: **строка**<br /><br /> Тип доступа: только для чтения<br /><br /> Квалификаторы: ключ<br /><br /> Имя экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], на котором хранится файл журнала.|  
|логдате|Тип данных: **DateTime**<br /><br /> Тип доступа: только для чтения<br /><br /> Квалификаторы: ключ<br /><br /> <br /><br /> Дата и время записи события в файл журнала.|  
|Message|Тип данных: **строка**<br /><br /> Тип доступа: только для чтения<br /><br /> <br /><br /> Сообщение о событии.|  
|процессинфо|Тип данных: **строка**<br /><br /> Тип доступа: только для чтения<br /><br /> <br /><br /> Сведения об идентификаторе процесса сервера источника (SPID) события.|  
  
## <a name="remarks"></a>Remarks  
  
|||  
|-|-|  
|MOF|Sqlmgmproviderxpsp2up.mof|  
|DLL-библиотеки|Sqlmgmprovider.dll|  
|Пространство имен|\root\Microsoft\SqlServer\ComputerManagement10|  
  
## <a name="example"></a>Пример  
 В этом примере рассматривается извлечение значений для всех записанных событий в указанном файле журнала. Чтобы выполнить пример, замените \<*Instance_Name*> именем экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], например "instance1", и замените "File_Name" именем файла журнала ошибок, например "ErrorLog. 1".  
  
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
 Если имя *instanceName* или *filename* не указаны в инструкции WQL, запрос возвратит сведения для экземпляра по умолчанию и текущего файла журнала [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Например, следующая инструкция WQL возвратит все события журнала из текущего файла журнала (ERRORLOG) в экземпляре по умолчанию (MSSQLSERVER).  
  
```  
"SELECT * FROM SqlErrorLogEvent"  
```  
  
## <a name="security"></a>Безопасность  
 Для подключения к файлу журнала [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью инструментария WMI необходимо иметь следующие разрешения на локальном и на удаленном компьютерах:  
  
-   Доступ на чтение к пространству имен WMI **Root\Microsoft\SqlServer\ComputerManagement10** . По умолчанию доступ для чтения задается для всех с помощью разрешения «Включить учетную запись».  
  
-   Разрешение для чтения на папку, содержащую журналы ошибок. По умолчанию журналы ошибок расположены по следующему пути (где \<*диск >* представляет диск, на котором установлена [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], а \<*instanceName*> — имя экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]):  
  
     **\<диск >: \Program FILES\MICROSOFT SQL Server\MSSQL13** **.\<InstanceName > \MSSQL\Log**  
  
 При соединении с использованием брандмауэра убедитесь, что в брандмауэре задано исключение для WMI на удаленных целевых компьютерах. Дополнительные сведения см. [в статье удаленное подключение к WMI, начиная с Windows Vista](https://go.microsoft.com/fwlink/?LinkId=178848).  
  
## <a name="see-also"></a>См. также статью  
   [класса SqlErrorLogFile](../../relational-databases/wmi-provider-configuration-classes/sqlerrorlogfile-class.md)  
 [Просмотр автономных файлов журнала](../../relational-databases/logs/view-offline-log-files.md)  
  
  
