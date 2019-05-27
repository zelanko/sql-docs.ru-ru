---
title: Редактор задачи Отслеживание событий WMI (страница «Параметры WMI») | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.wmieventwatcher.wmiquery.f1
helpviewer_keywords:
- WMI Event Watcher Task Editor
ms.assetid: 525f3de7-a021-4e52-9939-3a83c88f131a
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 52ca90b38975c8db762ec0937b265a91b03c5cb2
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66054381"
---
# <a name="wmi-event-watcher-task-editor-wmi-options-page"></a>Редактор задачи «Отслеживание событий WMI» (страница «Параметры WMI»)
  Страница **Параметры инструментария WMI** диалогового окна **Редактор задачи "Отслеживание событий WMI"** используется для указания источника запроса на языке запросов инструментария управления Windows (WQL) и вариантов реакции задачи "Отслеживание событий WMI" на события инструментария Microsoft Windows (WMI).  
  
 Дополнительные сведения об этой задаче см. в разделе [WMI Event Watcher Task](control-flow/wmi-event-watcher-task.md). Дополнительные сведения о языке запросов WQL см. в разделе документации по инструментарию управления Windows [Запросы с использованием языка запросов WQL](https://go.microsoft.com/fwlink/?LinkId=79045)в библиотеке MSDN.  
  
## <a name="static-options"></a>Статические параметры  
 **WMIConnectionName**  
 Выберите диспетчер подключений WMI в списке или щелкните \<**Создать WMI-соединение…**>, чтобы создать диспетчер подключений.  
  
 **См. также:** подробные сведения о [диспетчере WMI-соединений](connection-manager/wmi-connection-manager.md) и о [редакторе диспетчера WMI-соединений](../../2014/integration-services/wmi-connection-manager-editor.md).  
  
 **WQLQuerySourceType**  
 Выберите тип источника для WQL-запроса, выполняемого данной задачей. Это свойство имеет параметры, указанные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**Прямой ввод**|Задайте источник запроса WQL. При выборе этого значения отображается динамический параметр **WQLQuerySource**.|  
|**Соединение с файлом**|Выберите файл, содержащий запрос WQL. При выборе этого значения отображается динамический параметр **WQLQuerySource**.|  
|**Переменная**|Задайте источник переменной, определяющей запрос WQL. При выборе этого значения отображается динамический параметр **WQLQuerySource**.|  
  
 **ActionAtEvent**  
 Укажите, будет ли WMI-событие занесено в журнал, и будет ли оно инициировать действие служб [!INCLUDE[ssIS](../includes/ssis-md.md)] или будет только занесено в журнал.  
  
 **AfterEvent**  
 Укажите, будет ли задача завершена успешно или неудачно после получения ею WMI-события или она будет продолжать ожидать повторного возникновения события.  
  
 **ActionAtTimeout**  
 Укажите, запишет ли задача в журнал истечение времени ожидания WMI-запроса, и инициирует ли в ответ событие служб [!INCLUDE[ssIS](../includes/ssis-md.md)] или только запишет в журнал истечение времени ожидания.  
  
 **AfterTimeout**  
 Укажите, будет ли задача выполнена успешно или неудачно в ответ на истечение времени ожидания или она будет продолжать ожидать возникновения повторного истечения времени ожидания.  
  
 **NumberOfEvents**  
 Укажите количество событий для ожидания.  
  
 **Timeout**  
 Укажите количество секунд ожидания возникновения события. Значение 0 означает отсутствие времени ожидания.  
  
## <a name="wqlquerysource-dynamic-options"></a>Динамические параметры WQLQuerySource  
  
### <a name="wqlquerysource--direct-input"></a>WQLQuerySource = Прямой ввод  
 **WQLQuerySource**  
 Введите запрос или нажмите кнопку с многоточием "(…)" и введите запрос, используя диалоговое окно **Запрос WQL**.  
  
### <a name="wqlquerysource--file-connection"></a>WQLQuerySource = Соединение с файлом  
 **WQLQuerySource**  
 Выберите диспетчер подключений файлов в списке или щелкните \<**Создать соединение...**>, чтобы создать его.  
  
 **См. также:** подробные сведения о [диспетчере файловых подключений](connection-manager/file-connection-manager.md) и о [редакторе диспетчера файловых подключений](../../2014/integration-services/file-connection-manager-editor.md).  
  
### <a name="wqlquerysource--variable"></a>WQLQuerySource = Переменная  
 **WQLQuerySource**  
 Выберите переменную в списке или щелкните \<**Создать переменную...**>, чтобы создать ее.  
  
 **См. также:** подробные сведения о [переменных в службах Integration Services &#40;SSIS&#41;](integration-services-ssis-variables.md) и о [добавлении переменной](../../2014/integration-services/add-variable.md).  
  
## <a name="see-also"></a>См. также  
 [Справочник по сообщениям об ошибках служб Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Редактор задачи "Отслеживание событий WMI" (страница "Общие")](general-page-of-integration-services-designers-options.md)   
 [Страница «Выражения»](expressions/expressions-page.md)   
 [Задача «Модуль чтения данных WMI»](control-flow/wmi-data-reader-task.md)  
  
  
