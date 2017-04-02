---
title: "Редактор задачи &#171;Модуль чтения данных WMI&#187; (страница &#171;Параметры инструментария WMI&#187;) | Microsoft Docs"
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
  - "sql13.dts.designer.wmidatareadertask.wmiquery.f1"
helpviewer_keywords: 
  - "редактор задачи «Модуль чтения данных WMI»"
ms.assetid: 4b8d4716-882d-41b0-b77e-e0e2741a2cd5
caps.latest.revision: 40
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 40
---
# Редактор задачи &#171;Модуль чтения данных WMI&#187; (страница &#171;Параметры инструментария WMI&#187;)
  Страница **Параметры инструментария WMI** в диалоговом окне **Редактор задачи "Модуль чтения данных WMI"** используется для указания источника запроса WQL (Windows Management Instrumentation Query Language) и назначения результатов запроса.  
  
 Дополнительные сведения об этой задаче см. в разделе [WMI Data Reader Task](../../integration-services/control-flow/wmi-data-reader-task.md). Дополнительные сведения о языке запросов WQL см. в разделе документации по инструментарию управления Windows [Запросы с использованием языка запросов WQL](http://go.microsoft.com/fwlink/?LinkId=79045) в библиотеке MSDN.  
  
## Статические параметры  
 **WMIConnectionName**  
 Выберите диспетчер подключений WMI из списка или щелкните \<**Создать WMI-соединение...**>, чтобы создать его.  
  
 **См. также**: [Диспетчер WMI-соединений](../../integration-services/connection-manager/wmi-connection-manager.md), [Редактор диспетчера WMI-сеансов](../../integration-services/connection-manager/wmi-connection-manager-editor.md)  
  
 **WQLQuerySourceType**  
 Выберите тип источника для WQL-запроса, выполняемого данной задачей. Это свойство имеет параметры, указанные в следующей таблице.  
  
|Значение|Description|  
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
  
|Значение|Description|  
|-----------|-----------------|  
|**Соединение с файлом**|Выберите файл, в котором будут храниться результаты запроса WQL. При выборе этого значения отображается динамический параметр **DestinationType**.|  
|**Переменная**|Задайте переменную, в которой будут храниться результаты запроса WQL. При выборе этого значения отображается динамический параметр **DestinationType**.|  
  
## Динамические параметры WQLQuerySourceType  
  
### WQLQuerySourceType = Прямой ввод  
 **WQLQuerySource**  
 Введите запрос или нажмите кнопку многоточия (…) и введите запрос, используя диалоговое окно **Запрос WQL**.  
  
### WQLQuerySourceType = Соединение с файлом  
 **WQLQuerySource**  
 Выберите диспетчер подключений файлов из списка или щелкните \<**Создать соединение...**>, чтобы создать его.  
  
 **См. также:** [File Connection Manager](../../integration-services/connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../integration-services/connection-manager/file-connection-manager-editor.md)  
  
### WQLQuerySourceType = Переменная  
 **WQLQuerySource**  
 Выберите переменную из списка или нажмите кнопку \<**Создать переменную...**>, чтобы создать ее.  
  
 **См. также:** [Переменные в службах Integration Services (SSIS)](../../integration-services/integration-services-ssis-variables.md), [Добавление переменной](../Topic/Add%20Variable.md)  
  
## Динамические параметры DestinationType  
  
### DestinationType = Соединение с файлом  
 **Назначение**  
 Выберите диспетчер подключений файлов из списка или щелкните \<**Создать соединение...**>, чтобы создать его.  
  
 **См. также:** [File Connection Manager](../../integration-services/connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../integration-services/connection-manager/file-connection-manager-editor.md)  
  
### DestinationType = Переменная  
 **Назначение**  
 Выберите переменную из списка или нажмите кнопку \<**Создать переменную...**>, чтобы создать ее.  
  
 **См. также:** [Переменные в службах Integration Services (SSIS)](../../integration-services/integration-services-ssis-variables.md), [Добавление переменной](../Topic/Add%20Variable.md)  
  
## См. также  
 [Справочник по сообщениям об ошибках служб Integration Services](../../integration-services/integration-services-error-and-message-reference.md)   
 [Редактор задачи "Модуль чтения данных WMI" (страница "Общие")](../../integration-services/control-flow/wmi-data-reader-task-editor-general-page.md)   
 [Страница «Выражения»](../../integration-services/expressions/expressions-page.md)   
 [Задача «Отслеживание событий WMI»](../../integration-services/control-flow/wmi-event-watcher-task.md)  
  
  