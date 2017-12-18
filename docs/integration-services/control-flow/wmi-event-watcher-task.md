---
title: "Задача \"Отслеживание событий WMI\" | Документы Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: control-flow
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.wmieventwatchertask.f1
- sql13.dts.designer.wmieventwatcher.general.f1
- sql13.dts.designer.wmieventwatcher.wmiquery.f1
helpviewer_keywords:
- WQL [Integration Services]
- WMI Event Watcher task [Integration Services]
ms.assetid: b5bb52e9-a77e-41e1-93f9-d4c3bc6b2c9a
caps.latest.revision: "53"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5fcd6a9dedff32597209c837d4aa5d9471ff6d37
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="wmi-event-watcher-task"></a>Задача «Отслеживание событий WMI»
  Задача «Отслеживание событий WMI» осуществляет наблюдение за событием инструментария управления Windows (WMI) при помощи запроса на языке запросов к инструментарию управления (WQL), определяющего нужные события. Задачу «Отслеживание событий WMI» можно использовать в следующих целях:  
  
-   ожидание уведомления о добавлении файлов в папку и запуск обработки файла;  
  
-   выполнение пакета, удаляющего файлы, когда объем доступной памяти на сервере падает ниже заданного значения;  
  
-   отслеживание установки приложения и последующий запуск пакета, использующего это приложение.  
  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] содержат задачу, считывающую данные WMI.  
  
 Дополнительные сведения об этой задаче см. в следующем разделе:  
  
-   [Задача «Модуль чтения данных WMI»](../../integration-services/control-flow/wmi-data-reader-task.md)  
  
## <a name="wql-queries"></a>WQL-запрос  
 WQL — это разновидность языка SQL с выражениями, поддерживающими уведомления о событиях инструментария WMI и другие функции WMI. Дополнительные сведения о WQL см. в документации по инструментарию управления Windows в [библиотеке MSDN](http://go.microsoft.com/fwlink/?linkid=62553).  
  
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
 В следующей таблице перечислены пользовательские записи в журнале для задачи «Отслеживание событий WMI». Дополнительные сведения см. в разделе [Ведение журналов в службах Integration Services (SSIS)](../../integration-services/performance/integration-services-ssis-logging.md).  
  
|Запись журнала|Description|  
|---------------|-----------------|  
|**WMIEventWatcherEventOccurred**|Указывает, что произошло событие, отслеживаемое задачей.|  
|**WMIEventWatcherTimedout**|Указывает, что время ожидания выполнения задачи истекло.|  
|**WMIEventWatcherWatchingForWMIEvents**|Указывает, что задача приступила к выполнению WQL-запроса. Эта запись содержит запрос.|  
  
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
  
 Если источником является файл, задача «Отслеживание событий инструментария WMI» использует диспетчер подключения файлов для подключения к файлу. Дополнительные сведения см. в статье [Flat File Connection Manager](../../integration-services/connection-manager/flat-file-connection-manager.md).  
  
 Задача «Отслеживание событий инструментария WMI» использует диспетчер WMI-соединение для подключения к серверу, с которого она считывает данные WMI. Дополнительные сведения см. в статье [WMI Connection Manager](../../integration-services/connection-manager/wmi-connection-manager.md).  
  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../includes/ssis-md.md)] или программными средствами.  
  
 Дополнительные сведения о свойствах, которые можно задать в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] , см. в следующем разделе:  
  
-   [Страница «Выражения»](../../integration-services/expressions/expressions-page.md)  
  
 Дополнительные сведения об установке этих свойств в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] см. в следующем разделе:  
  
-   [Задание свойств задач или контейнеров](http://msdn.microsoft.com/library/52d47ca4-fb8c-493d-8b2b-48bb269f859b)  
  
## <a name="programmatic-configuration-of-the-wmi-event-watcher-task"></a>Настройка задачи «Отслеживание событий WMI» с помощью программных средств  
 Дополнительные сведения об установке этих свойств программными средствами см. в следующем разделе.  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.WmiEventWatcherTask.WmiEventWatcherTask>  
  
## <a name="wmi-event-watcher-task-editor-general-page"></a>Редактор задачи «Отслеживание событий WMI» (страница «Общие»)
  Используйте страницу **Общие** диалогового окна **Редактор задачи «Отслеживание событий WMI»** для ввода имени и описания задачи «Отслеживание событий WMI».  
  
 Дополнительные сведения о языке запросов WQL см. в разделе документации по инструментарию управления Windows [Запросы с использованием языка запросов WQL](http://go.microsoft.com/fwlink/?LinkId=79045)в библиотеке MSDN.  
  
### <a name="options"></a>Параметры  
 **Название**  
 Введите уникальное имя для задачи «Отслеживание событий WMI». Это имя используется в качестве метки для значка задачи.  
  
> [!NOTE]  
>  Имена задач в пределах пакета должны быть уникальными.  
  
 **Description**  
 Введите описание для задачи «Отслеживание событий WMI».  
  
## <a name="wmi-event-watcher-task-editor-wmi-options-page"></a>Редактор задачи «Отслеживание событий WMI» (страница «Параметры WMI»)
  Страница **Параметры инструментария WMI** диалогового окна **Редактор задачи "Отслеживание событий WMI"** используется для указания источника запроса на языке запросов инструментария управления Windows (WQL) и вариантов реакции задачи "Отслеживание событий WMI" на события инструментария Microsoft Windows (WMI).  
  
 Дополнительные сведения о языке запросов WQL см. в разделе документации по инструментарию управления Windows [Запросы с использованием языка запросов WQL](http://go.microsoft.com/fwlink/?LinkId=79045)в библиотеке MSDN.  
  
### <a name="static-options"></a>Статические параметры  
 **WMIConnectionName**  
 Выберите диспетчер подключений WMI в списке или щелкните \<**Создать WMI-соединение…**>, чтобы создать его.  
  
 **См. также** [Диспетчер WMI-соединений](../../integration-services/connection-manager/wmi-connection-manager.md), [Редактор диспетчера WMI-сеансов](../../integration-services/connection-manager/wmi-connection-manager-editor.md)  
  
 **WQLQuerySourceType**  
 Выберите тип источника для WQL-запроса, выполняемого данной задачей. Это свойство имеет параметры, указанные в следующей таблице.  
  
|Значение|Description|  
|-----------|-----------------|  
|**Прямой ввод**|Задайте источник запроса WQL. При выборе этого значения отображается динамический параметр **WQLQuerySource**.|  
|**Соединение с файлом**|Выберите файл, содержащий запрос WQL. При выборе этого значения отображается динамический параметр **WQLQuerySource**.|  
|**Переменная**|Задайте источник переменной, определяющей запрос WQL. При выборе этого значения отображается динамический параметр **WQLQuerySource**.|  
  
 **ActionAtEvent**  
 Укажите, будет ли WMI-событие занесено в журнал, и будет ли оно инициировать действие служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] или будет только занесено в журнал.  
  
 **AfterEvent**  
 Укажите, будет ли задача завершена успешно или неудачно после получения ею WMI-события или она будет продолжать ожидать повторного возникновения события.  
  
 **ActionAtTimeout**  
 Укажите, запишет ли задача в журнал истечение времени ожидания WMI-запроса, и инициирует ли в ответ событие служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] или только запишет в журнал истечение времени ожидания.  
  
 **AfterTimeout**  
 Укажите, будет ли задача выполнена успешно или неудачно в ответ на истечение времени ожидания или она будет продолжать ожидать возникновения повторного истечения времени ожидания.  
  
 **NumberOfEvents**  
 Укажите количество событий для ожидания.  
  
 **Timeout**  
 Укажите количество секунд ожидания возникновения события. Значение 0 означает отсутствие времени ожидания.  
  
### <a name="wqlquerysource-dynamic-options"></a>Динамические параметры WQLQuerySource  
  
#### <a name="wqlquerysource--direct-input"></a>WQLQuerySource = Прямой ввод  
 **WQLQuerySource**  
 Введите запрос или нажмите кнопку с многоточием "(…)" и введите запрос, используя диалоговое окно **Запрос WQL** .  
  
#### <a name="wqlquerysource--file-connection"></a>WQLQuerySource = Соединение с файлом  
 **WQLQuerySource**  
 Выберите диспетчер подключений файлов в списке или щелкните \<**Создать соединение...**>, чтобы создать его.  
  
 **См. также:** [File Connection Manager](../../integration-services/connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../integration-services/connection-manager/file-connection-manager-editor.md)  
  
#### <a name="wqlquerysource--variable"></a>WQLQuerySource = Переменная  
 **WQLQuerySource**  
 Выберите переменную в списке или щелкните \<**Создать переменную...**>, чтобы создать ее.  
  
 **См. также:** [Переменные в службах Integration Services (SSIS)](../../integration-services/integration-services-ssis-variables.md), [Добавление переменной](http://msdn.microsoft.com/library/d09b5d31-433f-4f7c-8c68-9df3a97785d5)  
  
