---
title: Редактор задачи "модуль чтения данных WMI" (страница "параметры WMI") | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.wmidatareadertask.wmiquery.f1
helpviewer_keywords:
- WMI Data Reader Task Editor
ms.assetid: 4b8d4716-882d-41b0-b77e-e0e2741a2cd5
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 8367f0ae57df5333808e4dfde25c5676a3bcf1d4
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66054360"
---
# <a name="wmi-data-reader-task-editor-wmi-options-page"></a>Редактор задачи «Модуль чтения данных WMI» (страница «Параметры инструментария WMI»)
  Страница **Параметры инструментария WMI** в диалоговом окне **Редактор задачи "Модуль чтения данных WMI"** используется для указания источника запроса WQL (Windows Management Instrumentation Query Language) и назначения результатов запроса.  
  
 Дополнительные сведения об этой задаче см. в разделе [WMI Data Reader Task](control-flow/wmi-data-reader-task.md). Дополнительные сведения о языке запросов WQL см. в разделе документации по инструментарию управления Windows [Запросы с использованием языка запросов WQL](https://go.microsoft.com/fwlink/?LinkId=79045)в библиотеке MSDN.  
  
## <a name="static-options"></a>Статические параметры  
 **WMIConnectionName**  
 Выберите диспетчер WMI-соединений из списка или нажмите кнопку \< **Создать WMI-подключение...**>, чтобы создать новый диспетчер соединений.  
  
 **См. также** [Диспетчер WMI-соединений](connection-manager/wmi-connection-manager.md), [Редактор диспетчера WMI-сеансов](../../2014/integration-services/wmi-connection-manager-editor.md)  
  
 **WQLQuerySourceType**  
 Выберите тип источника для WQL-запроса, выполняемого данной задачей. Это свойство имеет параметры, указанные в следующей таблице.  
  
|Применение|Описание|  
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
  
|Применение|Описание|  
|-----------|-----------------|  
|**Соединение с файлом**|Выберите файл, в котором будут храниться результаты запроса WQL. При выборе этого значения отображается динамический параметр **DestinationType**.|  
|**Переменная**|Задайте переменную, в которой будут храниться результаты запроса WQL. При выборе этого значения отображается динамический параметр **DestinationType**.|  
  
## <a name="wqlquerysourcetype-dynamic-options"></a>Динамические параметры WQLQuerySourceType  
  
### <a name="wqlquerysourcetype--direct-input"></a>WQLQuerySourceType = Прямой ввод  
 **WQLQuerySource**  
 Укажите запрос или нажмите кнопку с многоточием (...) и введите запрос в диалоговом окне **WQL-запрос** .  
  
### <a name="wqlquerysourcetype--file-connection"></a>WQLQuerySourceType = Соединение с файлом  
 **WQLQuerySource**  
 Выберите Диспетчер подключения файлов в списке или нажмите кнопку \< **создать соединение...**>, чтобы создать новый диспетчер соединений.  
  
 **См. также:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)  
  
### <a name="wqlquerysourcetype--variable"></a>WQLQuerySourceType = Переменная  
 **WQLQuerySource**  
 Выберите переменную из списка или нажмите кнопку \< **создать переменную...**>, чтобы создать новую переменную.  
  
 **См. также:** [Integration Services &#40;переменные&#41; SSIS](integration-services-ssis-variables.md), [Добавить переменную](../../2014/integration-services/add-variable.md)  
  
## <a name="destinationtype-dynamic-options"></a>Динамические параметры DestinationType  
  
### <a name="destinationtype--file-connection"></a>DestinationType = Соединение с файлом  
 **Назначение**  
 Выберите Диспетчер подключения файлов в списке или нажмите кнопку \< **создать соединение...**>, чтобы создать новый диспетчер соединений.  
  
 **См. также:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)  
  
### <a name="destinationtype--variable"></a>DestinationType = Переменная  
 **Назначение**  
 Выберите переменную из списка или нажмите кнопку \< **создать переменную...**>, чтобы создать новую переменную.  
  
 **См. также:** [Integration Services &#40;переменные&#41; SSIS](integration-services-ssis-variables.md), [Добавить переменную](../../2014/integration-services/add-variable.md)  
  
## <a name="see-also"></a>См. также  
 [Справочник по ошибкам и сообщениям Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Редактор задачи "модуль чтения данных WMI" &#40;страница "Общие"&#41;](general-page-of-integration-services-designers-options.md)   
 [Страница "выражения"](expressions/expressions-page.md)   
 [Задача «Отслеживание событий WMI»](control-flow/wmi-event-watcher-task.md)  
  
  
