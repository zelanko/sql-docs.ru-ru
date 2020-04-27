---
title: Редактор задачи «наблюдатель событий WMI» (страница «параметры WMI») | Документация Майкрософт
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
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66054381"
---
# <a name="wmi-event-watcher-task-editor-wmi-options-page"></a>Редактор задачи «Отслеживание событий WMI» (страница «Параметры WMI»)
  Страница **Параметры инструментария WMI** диалогового окна **Редактор задачи "Отслеживание событий WMI"** используется для указания источника запроса на языке запросов инструментария управления Windows (WQL) и вариантов реакции задачи "Отслеживание событий WMI" на события инструментария Microsoft Windows (WMI).  
  
 Дополнительные сведения об этой задаче см. в разделе [WMI Event Watcher Task](control-flow/wmi-event-watcher-task.md). Дополнительные сведения о языке запросов WQL см. в разделе документации по инструментарию управления Windows [Запросы с использованием языка запросов WQL](https://go.microsoft.com/fwlink/?LinkId=79045)в библиотеке MSDN.  
  
## <a name="static-options"></a>Статические параметры  
 **WMIConnectionName**  
 Выберите диспетчер WMI-соединений из списка или нажмите кнопку \< **Создать WMI-подключение...**>, чтобы создать новый диспетчер соединений.  
  
 **См. также** [Диспетчер WMI-соединений](connection-manager/wmi-connection-manager.md), [Редактор диспетчера WMI-сеансов](../../2014/integration-services/wmi-connection-manager-editor.md)  
  
 **WQLQuerySourceType**  
 Выберите тип источника для WQL-запроса, выполняемого данной задачей. Это свойство имеет параметры, указанные в следующей таблице.  
  
|Применение|Описание|  
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
 Укажите запрос или нажмите кнопку с многоточием (...) и введите запрос в диалоговом окне **WQL-запрос** .  
  
### <a name="wqlquerysource--file-connection"></a>WQLQuerySource = Соединение с файлом  
 **WQLQuerySource**  
 Выберите Диспетчер подключения файлов в списке или нажмите кнопку \< **создать соединение...**>, чтобы создать новый диспетчер соединений.  
  
 **См. также:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)  
  
### <a name="wqlquerysource--variable"></a>WQLQuerySource = Переменная  
 **WQLQuerySource**  
 Выберите переменную из списка или нажмите кнопку \< **создать переменную...**>, чтобы создать новую переменную.  
  
 **См. также:** [Integration Services &#40;переменные&#41; SSIS](integration-services-ssis-variables.md), [Добавить переменную](../../2014/integration-services/add-variable.md)  
  
## <a name="see-also"></a>См. также  
 [Справочник по ошибкам и сообщениям Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Редактор задачи "наблюдатель событий WMI" &#40;общие&#41;страницы](general-page-of-integration-services-designers-options.md)   
 [Страница "выражения"](expressions/expressions-page.md)   
 [Задача «Модуль чтения данных WMI»](control-flow/wmi-data-reader-task.md)  
  
  
