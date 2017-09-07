---
title: "Расширение пакетов с помощью задачи «скрипт» | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-xml
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
dev_langs:
- VB
helpviewer_keywords:
- scripts [Integration Services]
- SSIS Script task
- tasks [Integration Services], scripts
- Script task [Integration Services], about Script task
- scripts [Integration Services], about Script task with packages
- SSIS Script task, about Script task
ms.assetid: 911e6d26-a6fd-4fc3-a111-bf5f048e9bff
caps.latest.revision: 57
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: b2e0b0a933568f8313cefd2f1d6dbdd02f5d3cbc
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="extending-the-package-with-the-script-task"></a>Расширение пакета с помощью задачи «Скрипт»
  Задача «скрипт» расширяет возможности времени выполнения [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] пакеты с пользовательским кодом, написанным [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic или [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C#, который компилируется и выполняется во время выполнения пакета. Задача «Скрипт» упрощает разработку пользовательской задачи времени выполнения, если задачи, включенные в службы [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], не полностью удовлетворяют требованиям разработчика. Задача «Скрипт» самостоятельно пишет весь инфраструктурный код, давая разработчику возможность сосредоточиться исключительно на коде, необходимом для пользовательской обработки.  
  
 Задача «скрипт» взаимодействует с пакетом-контейнером через глобальный **Dts** объекта, экземпляр <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel> класса, предоставляемого средой скриптов. В задаче «Скрипт» можно писать код, который изменяет значения, хранящиеся в переменных служб [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]. Позже пакет использует эти обновленные значения для определения рабочего процесса. Задача «Скрипт» может также использовать пространство имен [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)], библиотеку классов платформы [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] и пользовательские сборки для реализации собственной функциональности.  
  
 Задача «Скрипт» и инфраструктурный код, который она создает, значительно упрощают разработку пользовательской задачи. Тем не менее, чтобы понять, как работает задача «скрипт», то может быть полезно прочитать раздел [разработку пользовательской задачи](../../../integration-services/extending-packages-custom-objects/task/developing-a-custom-task.md) для понимания шагов, которые участвуют в разработку пользовательской задачи.  
  
 Если создается задача, которую планируется повторно использовать в нескольких пакетах, вместо использования задачи «Скрипт» следует разработать собственную задачу. Дополнительные сведения см. в разделе [сравнение решений сценариев и пользовательскими объектами](../../../integration-services/extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md).  
  
## <a name="in-this-section"></a>В этом разделе  
 В следующих разделах представлены дополнительные сведения о задаче «Скрипт».  
  
 [Настройка задачи «скрипт» в редакторе сценариев задач](../../../integration-services/extending-packages-scripting/task/configuring-the-script-task-in-the-script-task-editor.md)  
 Объясняет, как свойства, которые можно настроить в **редактор задачи «скрипт»** влияют на возможности и производительность кода в задаче «скрипт».  
  
 [Кодирование и отладка задачи «скрипт»](../../../integration-services/extending-packages-scripting/task/coding-and-debugging-the-script-task.md)  
 Описание способов использования [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] средств для приложений (VSTA) для разработки скриптов, содержащихся в задаче «скрипт».  
  
 [Использование переменных в задаче «скрипт»](../../../integration-services/extending-packages-scripting/task/using-variables-in-the-script-task.md)  
 Объясняется использование переменных с помощью свойства <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A>.  
  
 [Подключение к источникам данных в задаче «скрипт»](../../../integration-services/extending-packages-scripting/task/connecting-to-data-sources-in-the-script-task.md)  
 Объясняется использование соединений с помощью свойства <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Connections%2A>.  
  
 [Создание событий в задаче «скрипт»](../../../integration-services/extending-packages-scripting/task/raising-events-in-the-script-task.md)  
 Объясняется инициирование событий с помощью свойства <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Events%2A>.  
  
 [Ведение журналов в задаче «скрипт»](../../../integration-services/extending-packages-scripting/task/logging-in-the-script-task.md)  
 Объясняется регистрация сведений с помощью метода <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A>.  
  
 [Возврат результатов из задачи «скрипт»](../../../integration-services/extending-packages-scripting/task/returning-results-from-the-script-task.md)  
 Объясняется возвращение результатов через свойства <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.TaskResult%2A> и <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.ExecutionValue%2A>.  
  
 [Примеры сценариев задач](../../../integration-services/extending-packages-scripting-task-examples/script-task-examples.md)  
 Содержит примеры, в которых показано несколько возможных использований задачи «Скрипт».  
  
## <a name="see-also"></a>См. также:  
 [Задача «скрипт»](../../../integration-services/control-flow/script-task.md)   
 [Сравнение задачи «скрипт» и компоненте скрипта](../../../integration-services/extending-packages-scripting/comparing-the-script-task-and-the-script-component.md)  
  
  
