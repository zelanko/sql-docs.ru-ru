---
title: Задача "Модуль чтения данных WMI" | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.wmidatareadertask.f1
helpviewer_keywords:
- WQL [Integration Services]
- WMI Data Reader task [Integration Services]
ms.assetid: dae57067-0275-4ac3-8f34-1b9d169f1112
caps.latest.revision: 49
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: e31b3c63d1fab749aea96e0d55fd7a704301d26d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37308104"
---
# <a name="wmi-data-reader-task"></a>Задача «Модуль чтения данных WMI»
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
  
 В случае если источником или целевым объектом является файл, задача «Модуль чтения данных WMI» использует диспетчер подключения файлов для подключения к файлу. Дополнительные сведения см. в статье [Flat File Connection Manager](../connection-manager/file-connection-manager.md).  
  
 Задача «Модуль чтения данных WMI» использует диспетчер WMI-соединений для подключения к серверу, с которого происходит считывание данных WMI. Дополнительные сведения см. в статье [WMI Connection Manager](../connection-manager/wmi-connection-manager.md).  
  
## <a name="wql-query"></a>Запрос WQL  
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
  
## <a name="custom-logging-messages-available-on-the-wmi-data-reader-task"></a>Пользовательские сообщения для ведения журнала, доступные в задаче «Модуль чтения данных WMI»  
 В следующей таблице перечислены пользовательские записи в журнале для задачи «Модуль чтения данных WMI». Дополнительные сведения см. в разделах [Ведение журналов в службах Integration Services (SSIS)](../performance/integration-services-ssis-logging.md) и [Пользовательские сообщения для ведения журнала](../custom-messages-for-logging.md).  
  
|Запись журнала|Описание|  
|---------------|-----------------|  
|`WMIDataReaderGettingWMIData`|Указывает, что задача приступила к чтению данных инструментария WMI.|  
|`WMIDataReaderOperation`|Сообщает о WQL-запросе, выполняемом задачей.|  
  
## <a name="configuration-of-the-wmi-data-reader-task"></a>Настройка задачи «Модуль чтения данных WMI»  
 Свойства задаются программно или через конструктор служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] .  
  
 Дополнительные сведения о свойствах, которые можно задать в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] , см. в следующих разделах.  
  
-   [Редактор задач модуль чтения данных WMI &#40;страница параметров WMI&#41;](../wmi-data-reader-task-editor-wmi-options-page.md)  
  
-   [Страница "Выражения"](../expressions/expressions-page.md)  
  
 Сведения о задании этих свойств программными средствами см. в следующем разделе:  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.WmiDataReaderTask.WmiDataReaderTask>  
  
## <a name="related-tasks"></a>Related Tasks  
 Дополнительные сведения об установке этих свойств в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] см. в следующем разделе:  
  
-   [Задание свойств задач или контейнеров](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="see-also"></a>См. также  
 [Задачи служб Integration Services](integration-services-tasks.md)   
 [Поток управления](control-flow.md)  
  
  
