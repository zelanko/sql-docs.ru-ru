---
title: SqlErrorLogFile, класс | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
ms.assetid: 2b83ae4a-c0d4-414c-b6e5-a41ec7c13159
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 2794e4f59b6c898b1fd956c0f9390ba9bbbd439e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62515479"
---
# <a name="sqlerrorlogfile-class"></a>SqlErrorLogFile, класс
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Предоставляет свойства для просмотра информации о файле журнала [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
class SQLErrorLogFile  
{  
   uint32ArchiveNumber;  
   stringInstanceName;  
   datetimeLastModified;  
   uint32LogFileSize;  
   stringName;  
  
};  
```  
  
## <a name="properties"></a>Свойства  
 SQLErrorLogFile, класс определяет следующие свойства.  
  
|||  
|-|-|  
|ArchiveNumber|Тип данных: **uint32**<br /><br /> Тип доступа: Только для чтения<br /><br /> <br /><br /> Номер архива для файла журнала.|  
|InstanceName|Тип данных: **строка**<br /><br /> Тип доступа: Только для чтения<br /><br /> Квалификаторы: Ключ<br /><br /> <br /><br /> Имя экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], на котором хранится файл журнала.|  
|Дата изменения|Тип данных: **даты и времени**<br /><br /> Тип доступа: Только для чтения<br /><br /> <br /><br /> Дата последнего изменения файла журнала.|  
|LogFileSize|Тип данных: **uint32**<br /><br /> Тип доступа: Только для чтения<br /><br /> <br /><br /> Размер файла журнала в байтах.|  
|Имя|Тип данных: **строка**<br /><br /> Тип доступа: Только для чтения<br /><br /> Квалификаторы: Ключ<br /><br /> <br /><br /> Имя файла журнала.|  
  
## <a name="remarks"></a>Примечания  
  
|||  
|-|-|  
|MOF|Sqlmgmprovider xpsp2up.mof|  
|DLL-библиотеки|Sqlmgmprovider.dll|  
|Пространство имен|\root\Microsoft\SqlServer\ComputerManagement10|  
  
## <a name="example"></a>Пример  
 В этом примере извлекаются данных обо всех файлах журналов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в указанном экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Чтобы запустить пример, замените \< *имя_экземпляра*> с именем экземпляра, например, «Instance1».  
  
```  
on error resume next  
set strComputer = "."  
set objWMIService = GetObject("winmgmts:\\.\root\Microsoft\SqlServer\ComputerManagement10")  
set LogFiles = objWmiService.ExecQuery("SELECT * FROM SqlErrorLogFile WHERE InstanceName = '<Instance_Name>'")  
  
For Each logFile in LogFiles  
  
WScript.Echo "Instance Name:  " & logFile.InstanceName & vbNewLine _  
    & "Log File Name:  " & logFile.Name & vbNewLine _  
    & "Archive Number: " & logFile.ArchiveNumber & vbNewLine _  
    & "Log File Size:  " & logFile.LogFileSize & " bytes" & vbNewLine _  
    & "Last Modified:  " & logFile.LastModified & vbNewLine _  
  
Next   
```  
  
## <a name="comments"></a>Комментарии  
 Когда *InstanceName* указан в инструкции WQL, запрос вернет сведения для экземпляра по умолчанию. Например, следующая инструкция WQL вернет информацию обо всех файлах журнала в текущем экземпляре (MSSQLSERVER).  
  
```  
"SELECT * FROM SqlErrorLogFile"  
```  
  
## <a name="security"></a>безопасность  
 Для подключения к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] файла журнала посредством инструментария WMI, необходимо иметь следующие разрешения как на локальных и удаленных компьютерах:  
  
-   Доступ на чтение к **Root\Microsoft\SqlServer\ComputerManagement10** пространство имен WMI. По умолчанию доступ для чтения задается для всех с помощью разрешения «Включить учетную запись».  
  
    > [!NOTE]  
    >  Сведения о том, как проверка разрешений WMI см. в разделе "Безопасность" раздела [Просмотр автономных файлов журнала](../../relational-databases/logs/view-offline-log-files.md).  
  
-   Разрешение для чтения на папку, содержащую журналы ошибок. По умолчанию ошибки журналы находятся по следующему пути (где \< *диска >* представляет диск, на котором установлен [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и \< *InstanceName*> — Имя экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]):  
  
     **\<Диск >: \Program Files\Microsoft SQL Server\MSSQL11** **.\< Имя_экземпляра > \MSSQL\Log**  
  
 При соединении с использованием брандмауэра убедитесь, что в брандмауэре задано исключение для WMI на удаленных целевых компьютерах. Дополнительные сведения см. в разделе [подключение к WMI Remotely Starting with Windows Vista](https://go.microsoft.com/fwlink/?LinkId=178848).  
  
## <a name="see-also"></a>См. также  
 [SqlErrorLogEvent, класс](../../relational-databases/wmi-provider-configuration-classes/sqlerrorlogevent-class.md)   
 [Просмотр автономных файлов журнала](../../relational-databases/logs/view-offline-log-files.md)  
  
  
