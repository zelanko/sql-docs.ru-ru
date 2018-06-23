---
title: SqlErrorLogFile, класс | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 2b83ae4a-c0d4-414c-b6e5-a41ec7c13159
caps.latest.revision: 11
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 5e23c4512f04370fa24b3eb4ff3b74a072f6a2e5
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36189491"
---
# <a name="sqlerrorlogfile-class"></a>SqlErrorLogFile, класс
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
|ArchiveNumber|Тип данных: `uint32`<br /><br /> Тип доступа: только для чтения<br /><br /> <br /><br /> Номер архива для файла журнала.|  
|InstanceName|Тип данных: `string`<br /><br /> Тип доступа: только для чтения<br /><br /> Квалификаторы: ключ<br /><br /> <br /><br /> Имя экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], на котором хранится файл журнала.|  
|Дата изменения|Тип данных: `datetime`<br /><br /> Тип доступа: только для чтения<br /><br /> <br /><br /> Дата последнего изменения файла журнала.|  
|LogFileSize|Тип данных: `uint32`<br /><br /> Тип доступа: только для чтения<br /><br /> <br /><br /> Размер файла журнала в байтах.|  
|Имя|Тип данных: `string`<br /><br /> Тип доступа: только для чтения<br /><br /> Квалификаторы: ключ<br /><br /> <br /><br /> Имя файла журнала.|  
  
## <a name="remarks"></a>Примечания  
  
|||  
|-|-|  
|MOF|Sqlmgmprovider xpsp2up.mof|  
|DLL-библиотеки|Sqlmgmprovider.dll|  
|Пространство имен|\root\Microsoft\SqlServer\ComputerManagement10|  
  
## <a name="example"></a>Пример  
 В этом примере извлекаются данных обо всех файлах журналов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в указанном экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Чтобы запустить пример, замените \< *имя_экземпляра*> с именем экземпляра, например, «экземпляр1».  
  
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
 Когда *InstanceName* указан в инструкции WQL, запрос вернет информацию для экземпляра по умолчанию. Например, следующая инструкция WQL вернет информацию обо всех файлах журнала в текущем экземпляре (MSSQLSERVER).  
  
```  
"SELECT * FROM SqlErrorLogFile"  
```  
  
## <a name="security"></a>безопасность  
 Для подключения к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] файла журнала посредством инструментария WMI, необходимо иметь следующие разрешения на локальных и удаленных компьютеров:  
  
-   Доступ на чтение к **Root\Microsoft\SqlServer\ComputerManagement10** пространство имен WMI. По умолчанию доступ для чтения задается для всех с помощью разрешения «Включить учетную запись».  
  
    > [!NOTE]  
    >  Сведения о проверке разрешений WMI см. в разделе «Безопасность» раздела [Просмотр автономных файлов журнала](../logs/view-offline-log-files.md).  
  
-   Разрешение для чтения на папку, содержащую журналы ошибок. По умолчанию ошибки журналы находятся по следующему пути (где \< *диска >* представляет диск, на котором установлена [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и \< *InstanceName*> — Имя экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]):  
  
     **\<Диск >: \Program Files\Microsoft SQL Server\MSSQL11** **.\< Имя_экземпляра > \MSSQL\Log**  
  
 При соединении с использованием брандмауэра убедитесь, что в брандмауэре задано исключение для WMI на удаленных целевых компьютерах. Дополнительные сведения см. в разделе [подключение к WMI, начиная с Windows Vista удаленно](http://go.microsoft.com/fwlink/?LinkId=178848).  
  
## <a name="see-also"></a>См. также  
 [SqlErrorLogEvent, класс](sqlerrorlogevent-class.md)   
 [Просмотр автономных файлов журнала](../logs/view-offline-log-files.md)  
  
  