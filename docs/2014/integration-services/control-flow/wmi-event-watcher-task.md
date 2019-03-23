---
title: Задача "Отслеживание событий WMI" | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.wmieventwatchertask.f1
helpviewer_keywords:
- WQL [Integration Services]
- WMI Event Watcher task [Integration Services]
ms.assetid: b5bb52e9-a77e-41e1-93f9-d4c3bc6b2c9a
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 4add98b6c085d52238a528c313008bc688ae6e54
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2019
ms.locfileid: "58385456"
---
# <a name="wmi-event-watcher-task"></a>Задача «Отслеживание событий WMI»
  Задача «Отслеживание событий WMI» осуществляет наблюдение за событием инструментария управления Windows (WMI) при помощи запроса на языке запросов к инструментарию управления (WQL), определяющего нужные события. Задачу «Отслеживание событий WMI» можно использовать в следующих целях:  
  
-   ожидание уведомления о добавлении файлов в папку и запуск обработки файла;  
  
-   выполнение пакета, удаляющего файлы, когда объем доступной памяти на сервере падает ниже заданного значения;  
  
-   отслеживание установки приложения и последующий запуск пакета, использующего это приложение.  
  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] содержат задачу, считывающую данные WMI.  
  
 Дополнительные сведения об этой задаче см. в следующем разделе:  
  
-   [Задача «Модуль чтения данных WMI»](wmi-data-reader-task.md)  
  
## <a name="wql-queries"></a>WQL-запрос  
 WQL — это разновидность языка SQL с выражениями, поддерживающими уведомления о событиях инструментария WMI и другие функции WMI. Дополнительные сведения о WQL см. в документации по инструментарию управления Windows в [библиотеке MSDN](https://go.microsoft.com/fwlink/?linkid=62553).  
  
> [!NOTE]  
>  Классы WMI отличаются в различных версиях операционной системы Windows.  
  
 В следующем запросе отслеживается уведомление об использовании более 40 процентов мощности ЦП.  
  
```  
SELECT * from __InstanceModificationEvent WITHIN 2 WHERE TargetInstance ISA 'Win32_Processor' and TargetInstance.LoadPercentage > 40  
```  
  
 В следующем запросе отслеживается уведомление о добавлении файла в папку.  
  
```  
SELECT * FROM __InstanceCreationEvent WITHIN 10 WHERE TargetInstance ISA "CIM_DirectoryContainsFile" and TargetInstance.GroupComponent= "Win32_Directory.Name=\"c:\\\\WMIFileWatcher\""   
```  
  
## <a name="custom-logging-messages-available-on-the-wmi-event-watcher-task"></a>Пользовательские сообщения для ведения журнала, доступные в задаче «Отслеживание событий WMI»  
 В следующей таблице перечислены пользовательские записи в журнале для задачи «Отслеживание событий WMI». Дополнительные сведения см. в разделах [Ведение журналов в службах Integration Services (SSIS)](../performance/integration-services-ssis-logging.md) и [Пользовательские сообщения для ведения журнала](../custom-messages-for-logging.md).  
  
|Запись журнала|Описание|  
|---------------|-----------------|  
|`WMIEventWatcherEventOccurred`|Указывает, что произошло событие, отслеживаемое задачей.|  
|`WMIEventWatcherTimedout`|Указывает, что время ожидания выполнения задачи истекло.|  
|`WMIEventWatcherWatchingForWMIEvents`|Указывает, что задача приступила к выполнению WQL-запроса. Эта запись содержит запрос.|  
  
## <a name="configuration-of-the-wmi-event-watcher-task"></a>Настройка задачи «Отслеживание событий WMI»  
 Настроить задачу «Модуль чтения данных WMI» можно следующими способами.  
  
-   Указать, какой диспетчер соединений WMI необходимо использовать.  
  
-   Указать источник WQL-запроса. По отношению к задаче источник может быть внешним (переменной или файлом), или же запрос может быть сохранен как свойство задачи.  
  
-   Укажите, какое действие должно быть выполнено задачей по событию инструментария WMI. Можно вести журнал уведомлений о событии и состоянии после события или инициировать пользовательские события служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , которые предоставляют данные, связанные с событием WMI, уведомлением и состоянием после события.  
  
-   Определите реакцию задачи на события. В зависимости от события задача может быть настроена на выполнение или сбой, либо на дальнейшее отслеживание событий.  
  
-   Укажите, какое действие должно быть предпринято задачей по истечении времени ожидания запроса WMI. Можно вести журнал истечения времени ожидания и состояния после него или инициировать пользовательское событие служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , указывающее, что время ожидания события инструментария WMI истекло, а также записывающее состояние ожидания в журнал.  
  
-   Определите реакцию задачи на истечение срока ожидания. Задача может быть настроена на выполнение или сбой, либо на дальнейшее отслеживание событий.  
  
-   Укажите, сколько раз задача должна отслеживать событие.  
  
-   Укажите время ожидания.  
  
 Если источником является файл, задача «Отслеживание событий инструментария WMI» использует диспетчер подключения файлов для подключения к файлу. Дополнительные сведения см. в статье [Flat File Connection Manager](../connection-manager/file-connection-manager.md).  
  
 Задача «Отслеживание событий инструментария WMI» использует диспетчер WMI-соединение для подключения к серверу, с которого она считывает данные WMI. Дополнительные сведения см. в статье [WMI Connection Manager](../connection-manager/wmi-connection-manager.md).  
  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../includes/ssis-md.md)] или программными средствами.  
  
 Дополнительные сведения о свойствах, которые можно задать в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] , см. в следующих разделах:  
  
-   [Редактор задачи "Отслеживание событий WMI" (страница "Общие")](../general-page-of-integration-services-designers-options.md)  
  
-   [Редактор задачи "Отслеживание событий WMI" (страница "Параметры WMI")](../wmi-event-watcher-task-editor-wmi-options-page.md)  
  
-   [Страница «Выражения»](../expressions/expressions-page.md)  
  
 Дополнительные сведения об установке этих свойств в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] см. в следующем разделе:  
  
-   [Задание свойств задач или контейнеров](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="programmatic-configuration-of-the-wmi-event-watcher-task"></a>Настройка задачи «Отслеживание событий WMI» с помощью программных средств  
 Дополнительные сведения об установке этих свойств программными средствами см. в следующем разделе.  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.WmiEventWatcherTask.WmiEventWatcherTask>  
  
  
