---
title: Задача "Модуль чтения данных WMI" | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.wmidatareadertask.f1
helpviewer_keywords:
- WQL [Integration Services]
- WMI Data Reader task [Integration Services]
ms.assetid: dae57067-0275-4ac3-8f34-1b9d169f1112
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 12340ae2ba13bf6219cf9940a56eeaa8b995f3e8
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62829497"
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
 WQL — это разновидность языка SQL с выражениями, поддерживающими уведомления о событиях инструментария WMI и другие функции WMI. Дополнительные сведения о WQL см. в документации по инструментарию управления Windows в [библиотеке MSDN](https://go.microsoft.com/fwlink/?linkid=7022).  
  
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
  
-   [Редактор задачи "Модуль чтения данных WMI" (страница "Параметры инструментария WMI")](../wmi-data-reader-task-editor-wmi-options-page.md)  
  
-   [Страница «Выражения»](../expressions/expressions-page.md)  
  
 Сведения о задании этих свойств программными средствами см. в следующем разделе:  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.WmiDataReaderTask.WmiDataReaderTask>  
  
## <a name="related-tasks"></a>Связанные задачи  
 Дополнительные сведения об установке этих свойств в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] см. в следующем разделе:  
  
-   [Задание свойств задач или контейнеров](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="see-also"></a>См. также  
 [Задачи служб Integration Services](integration-services-tasks.md)   
 [Поток управления](control-flow.md)  
  
  
