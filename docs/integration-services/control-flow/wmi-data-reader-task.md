---
title: Задача "Модуль чтения данных WMI" | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.wmidatareadertask.f1
- sql13.dts.designer.wmidatareadertask.general.f1
- sql13.dts.designer.wmidatareadertask.wmiquery.f1
helpviewer_keywords:
- WQL [Integration Services]
- WMI Data Reader task [Integration Services]
ms.assetid: dae57067-0275-4ac3-8f34-1b9d169f1112
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 3b7a527770e41870729c194bd9c7651b77cffd2d
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68890846"
---
# <a name="wmi-data-reader-task"></a>Задача «Модуль чтения данных WMI»

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


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
 В следующей таблице перечислены пользовательские записи в журнале для задачи «Модуль чтения данных WMI». Дополнительные сведения см. в разделе [Ведение журналов в службах Integration Services (SSIS)](../../integration-services/performance/integration-services-ssis-logging.md).  
  
|Запись журнала|Описание|  
|---------------|-----------------|  
|**WMIDataReaderGettingWMIData**|Указывает, что задача приступила к чтению данных инструментария WMI.|  
|**WMIDataReaderOperation**|Сообщает о WQL-запросе, выполняемом задачей.|  
  
## <a name="configuration-of-the-wmi-data-reader-task"></a>Настройка задачи «Модуль чтения данных WMI»  
 Свойства задаются программно или через конструктор служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] .  
  
 Дополнительные сведения о свойствах, которые можно задать в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] , см. в следующих разделах:  
  
-   [Страница «Выражения»](../../integration-services/expressions/expressions-page.md)  
  
 Сведения о задании этих свойств программными средствами см. в следующем разделе:  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.WmiDataReaderTask.WmiDataReaderTask>  
  
## <a name="related-tasks"></a>Связанные задачи  
 Дополнительные сведения об установке этих свойств в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] см. в следующем разделе:  
  
-   [Задание свойств задач или контейнеров](https://msdn.microsoft.com/library/52d47ca4-fb8c-493d-8b2b-48bb269f859b)  
  
## <a name="wmi-data-reader-task-editor-general-page"></a>Редактор задачи «Модуль чтения данных WMI» (страница «Общие»)
  Страница **Общие** диалогового окна **Редактор задачи «Модуль чтения данных WMI»** позволяет дать имя и описание задаче «Модуль чтения данных WMI».  
  
  Дополнительные сведения о языке запросов WQL см. в разделе документации по инструментарию управления Windows [Запросы с использованием языка запросов WQL](/windows/win32/wmisdk/querying-with-wql)в библиотеке MSDN.  
  
### <a name="options"></a>Параметры  
 **Название**  
 Задайте уникальное имя задаче «Модуль чтения данных WMI». Это имя используется в качестве метки для значка задачи.  
  
> [!NOTE]  
>  Имена задач в пределах пакета должны быть уникальными.  
  
 **Описание**  
 Введите описание задачи «Модуль чтения данных WMI».  
  
## <a name="wmi-data-reader-task-editor-wmi-options-page"></a>Редактор задачи «Модуль чтения данных WMI» (страница «Параметры инструментария WMI»)
  Страница **Параметры инструментария WMI** в диалоговом окне **Редактор задачи "Модуль чтения данных WMI"** используется для указания источника запроса WQL (Windows Management Instrumentation Query Language) и назначения результатов запроса.  
  
 Дополнительные сведения о языке запросов WQL см. в разделе документации по инструментарию управления Windows [Запросы с использованием языка запросов WQL](/windows/win32/wmisdk/querying-with-wql)в библиотеке MSDN.  
  
### <a name="static-options"></a>Статические параметры  
 **WMIConnectionName**  
 Выберите диспетчер подключений WMI в списке или щелкните \<**Создать WMI-соединение…** >, чтобы создать диспетчер подключений.  
  
 **См. также:** подробные сведения о [диспетчере WMI-соединений](../../integration-services/connection-manager/wmi-connection-manager.md) и о [редакторе диспетчера WMI-соединений](../../integration-services/connection-manager/wmi-connection-manager-editor.md).  
  
 **WQLQuerySourceType**  
 Выберите тип источника для WQL-запроса, выполняемого данной задачей. Это свойство имеет параметры, указанные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**Прямой ввод**|Задайте источник запроса WQL. При выборе этого значения отображается динамический параметр **WQLQuerySourceType**.|  
|**Соединение с файлом**|Выберите файл, содержащий запрос WQL. При выборе этого значения отображается динамический параметр **WQLQuerySourceType**.|  
|**Переменная**|Задайте источник переменной, определяющей запрос WQL. При выборе этого значения отображается динамический параметр **WQLQuerySourceType**.|  
  
 **OutputType**  
 Укажите тип выходных данных: таблица данных, значение свойства или имя и значение свойства.  
  
 **OverwriteDestination**  
 Указывает, следует ли сохранить, перезаписать или добавить данные в целевом файле или переменной.  
  
 **DestinationType**  
 Выберите тип назначения запроса WQL, выполняемого данной задачей. Это свойство имеет параметры, указанные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**Соединение с файлом**|Выберите файл, в котором будут храниться результаты запроса WQL. При выборе этого значения отображается динамический параметр **DestinationType**.|  
|**Переменная**|Задайте переменную, в которой будут храниться результаты запроса WQL. При выборе этого значения отображается динамический параметр **DestinationType**.|  
  
### <a name="wqlquerysourcetype-dynamic-options"></a>Динамические параметры WQLQuerySourceType  
  
#### <a name="wqlquerysourcetype--direct-input"></a>WQLQuerySourceType = Прямой ввод  
 **WQLQuerySource**  
 Введите запрос или нажмите кнопку многоточия (…) и введите запрос, используя диалоговое окно **Запрос WQL**.  
  
#### <a name="wqlquerysourcetype--file-connection"></a>WQLQuerySourceType = Соединение с файлом  
 **WQLQuerySource**  
 Выберите диспетчер подключений файлов в списке или щелкните \<**Создать соединение...** >, чтобы создать его.  
  
 **См. также:** подробные сведения о [диспетчере файловых подключений](../../integration-services/connection-manager/file-connection-manager.md) и о [редакторе диспетчера файловых подключений](../../integration-services/connection-manager/file-connection-manager-editor.md).  
  
#### <a name="wqlquerysourcetype--variable"></a>WQLQuerySourceType = Переменная  
 **WQLQuerySource**  
 Выберите переменную в списке или щелкните \<**Создать переменную...** >, чтобы создать ее.  
  
 **См. также:** подробные сведения о [переменных в службах Integration Services &#40;SSIS&#41;](../../integration-services/integration-services-ssis-variables.md) и о [добавлении переменной](https://msdn.microsoft.com/library/d09b5d31-433f-4f7c-8c68-9df3a97785d5).  
  
### <a name="destinationtype-dynamic-options"></a>Динамические параметры DestinationType  
  
#### <a name="destinationtype--file-connection"></a>DestinationType = Соединение с файлом  
 **Назначение**  
 Выберите диспетчер подключений файлов в списке или щелкните \<**Создать соединение...** >, чтобы создать его.  
  
 **См. также:** подробные сведения о [диспетчере файловых подключений](../../integration-services/connection-manager/file-connection-manager.md) и о [редакторе диспетчера файловых подключений](../../integration-services/connection-manager/file-connection-manager-editor.md).  
  
#### <a name="destinationtype--variable"></a>DestinationType = Переменная  
 **Назначение**  
 Выберите переменную в списке или щелкните \<**Создать переменную...** >, чтобы создать ее.  
  
 **См. также:** подробные сведения о [переменных в службах Integration Services &#40;SSIS&#41;](../../integration-services/integration-services-ssis-variables.md) и о [добавлении переменной](https://msdn.microsoft.com/library/d09b5d31-433f-4f7c-8c68-9df3a97785d5).  
  
## <a name="see-also"></a>См. также:  
 [Задачи служб Integration Services](../../integration-services/control-flow/integration-services-tasks.md)   
 [Поток управления](../../integration-services/control-flow/control-flow.md)  
  
  
