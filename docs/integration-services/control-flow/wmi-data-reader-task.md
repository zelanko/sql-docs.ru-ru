---
title: "Задача &#171;Модуль чтения данных WMI&#187; | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.wmidatareadertask.f1"
helpviewer_keywords: 
  - "WQL [службы Integration Services]"
  - "задача «Модуль чтения данных WMI» [службы Integration Services]"
ms.assetid: dae57067-0275-4ac3-8f34-1b9d169f1112
caps.latest.revision: 49
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 49
---
# Задача &#171;Модуль чтения данных WMI&#187;
  Задача «Модуль чтения данных WMI» использует для выполнения запросов язык WQL, который возвращает от инструментария WMI сведения о системе компьютера. Задача «Модуль чтения данных WMI» может быть использована в следующих целях.  
  
-   Выполнение запросов к журналам событий Windows на локальном или удаленном компьютере, а также запись полученных сведений в файл или переменную.  
  
-   Сбор сведений о наличии, состоянии и свойствах компонентов оборудования, а также дальнейшее использование этих сведений для определения необходимости запуска других задач в потоке управления.  
  
-   Составление списка приложений с указанием установленной версии.  
  
 Настроить задачу «Модуль чтения данных WMI» можно следующими способами.  
  
-   Указать, какой диспетчер соединений WMI необходимо использовать.  
  
-   Указать источник WQL-запроса. Запрос может храниться либо в свойствах задачи, либо в переменной или файле вне задачи.  
  
-   Указать формат результатов WQL-запроса. Задача поддерживает результаты в формате таблиц, пар имен значений и свойств или значений свойства.  
  
-   Указать целевой объект запроса. Целевым объектом запроса может являться переменная или файл.  
  
-   Указать способ обращения к целевому объекту запроса: перезапись, сохранение или добавление.  
  
 В случае если источником или целевым объектом является файл, задача «Модуль чтения данных WMI» использует диспетчер подключения файлов для подключения к файлу. Дополнительные сведения см. в статье [Flat File Connection Manager](../../integration-services/connection-manager/flat-file-connection-manager.md).  
  
 Задача «Модуль чтения данных WMI» использует диспетчер WMI-соединений для подключения к серверу, с которого происходит считывание данных WMI. Дополнительные сведения см. в статье [WMI Connection Manager](../../integration-services/connection-manager/wmi-connection-manager.md).  
  
## Запрос WQL  
 WQL — это разновидность языка SQL с выражениями, поддерживающими уведомления о событиях инструментария WMI и другие функции WMI. Дополнительные сведения о WQL см. в документации по инструментарию управления Windows в [библиотеке MSDN](http://go.microsoft.com/fwlink/?linkid=7022).  
  
> [!NOTE]  
>  Классы WMI отличаются в различных версиях операционной системы Windows.  
  
 Приведенный ниже пример WQL-запроса выводит записи событий в журнале приложений.  
  
```  
SELECT * FROM Win32_NTLogEvent WHERE LogFile = 'Application' AND (SourceName='SQLISService' OR SourceName='SQLISPackage') AND TimeGenerated > '20050117'  
```  
  
 Приведенный ниже пример WQL-запроса выводит сведения о логическом диске.  
  
```  
SELECT FreeSpace, DeviceId, Size, SystemName, Description FROM Win32_LlogicalDisk  
```  
  
 Приведенный ниже пример WQL-запроса выводит список исправлений QFE, произведенных в текущей операционной системе.  
  
```  
Select * FROM Win32_QuickFixEngineering  
```  
  
## Пользовательские сообщения для ведения журнала, доступные в задаче «Модуль чтения данных WMI»  
 В следующей таблице перечислены пользовательские записи в журнале для задачи «Модуль чтения данных WMI». Дополнительные сведения см. в разделах [Ведение журналов в службах Integration Services (SSIS)](../../integration-services/performance/integration-services-ssis-logging.md) и [Пользовательские сообщения для ведения журнала](../../integration-services/performance/custom-messages-for-logging.md).  
  
|Запись журнала|Description|  
|---------------|-----------------|  
|**WMIDataReaderGettingWMIData**|Указывает, что задача приступила к чтению данных инструментария WMI.|  
|**WMIDataReaderOperation**|Сообщает о WQL-запросе, выполняемом задачей.|  
  
## Настройка задачи «Модуль чтения данных WMI»  
 Свойства задаются программно или через конструктор служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] .  
  
 Дополнительные сведения о свойствах, которые можно задать в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] , см. в следующих разделах.  
  
-   [Редактор задачи "Модуль чтения данных WMI" (страница "Параметры инструментария WMI")](../../integration-services/control-flow/wmi-data-reader-task-editor-wmi-options-page.md)  
  
-   [Страница «Выражения»](../../integration-services/expressions/expressions-page.md)  
  
 Сведения о задании этих свойств программными средствами см. в следующем разделе:  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.WmiDataReaderTask.WmiDataReaderTask>  
  
## Связанные задачи  
 Дополнительные сведения об установке этих свойств в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] см. в следующем разделе:  
  
-   [Задание свойств задач или контейнеров](../Topic/Set%20the%20Properties%20of%20a%20Task%20or%20Container.md)  
  
## См. также  
 [Задачи служб Integration Services](../../integration-services/control-flow/integration-services-tasks.md)   
 [Поток управления](../../integration-services/control-flow/control-flow.md)  
  
  