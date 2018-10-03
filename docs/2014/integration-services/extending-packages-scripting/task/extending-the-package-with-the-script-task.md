---
title: Расширение пакета с помощью задачи "Скрипт" | Документы Майкрософт
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- integration-services
ms.topic: reference
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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 50908fe5913a07760db26bcf039fd27eb6d062f8
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48052604"
---
# <a name="extending-the-package-with-the-script-task"></a>Расширение пакета с помощью задачи «Скрипт»
  Задача "Скрипт" расширяет возможности времени выполнения для пакетов служб [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] благодаря пользовательскому коду, написанному на языке [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic или [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C#, который компилируется и выполняется во время выполнения пакетов. Задача «Скрипт» упрощает разработку пользовательской задачи времени выполнения, если задачи, включенные в службы [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], не полностью удовлетворяют требованиям разработчика. Задача «Скрипт» самостоятельно пишет весь инфраструктурный код, давая разработчику возможность сосредоточиться исключительно на коде, необходимом для пользовательской обработки.  
  
 Задача «Скрипт» взаимодействует с пакетом-контейнером через глобальный объект `Dts`, экземпляр класса <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel>, предоставляемого средой скриптов. В задаче «Скрипт» можно писать код, который изменяет значения, хранящиеся в переменных служб [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]. Позже пакет использует эти обновленные значения для определения рабочего процесса. Задача «Скрипт» может также использовать пространство имен [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)], библиотеку классов платформы [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] и пользовательские сборки для реализации собственной функциональности.  
  
 Задача «Скрипт» и инфраструктурный код, который она создает, значительно упрощают разработку пользовательской задачи. Однако, чтобы понять, как работает задача "Скрипт", будет полезно прочитать раздел [Разработка пользовательской задачи](../../extending-packages-custom-objects/task/developing-a-custom-task.md), чтобы ознакомиться с шагами разработки пользовательской задачи.  
  
 Если создается задача, которую планируется повторно использовать в нескольких пакетах, вместо использования задачи «Скрипт» следует разработать собственную задачу. Дополнительные сведения см. в разделе [Сравнение решений со сценариями и пользовательских объектов](../comparing-scripting-solutions-and-custom-objects.md).  
  
## <a name="in-this-section"></a>в этом разделе  
 В следующих разделах представлены дополнительные сведения о задаче «Скрипт».  
  
 [Настройка задачи «Скрипт» в редакторе задачи «Скрипт»](configuring-the-script-task-in-the-script-task-editor.md)  
 Объясняется, как настроенные в окне **Редактор задачи "скрипт"** свойства влияют на возможности и производительность кода в задаче "Скрипт".  
  
 [Написание кода и отладка задачи «Скрипт»](../../control-flow/script-task.md)  
 Объясняется использование редактора средств [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] для приложений (VSTA) для разработки скриптов, содержащихся в задаче "Скрипт".  
  
 [Использование переменных в задаче «Скрипт»](using-variables-in-the-script-task.md)  
 Объясняется использование переменных с помощью свойства <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A>.  
  
 [Соединение с источниками данных в задаче «Скрипт»](connecting-to-data-sources-in-the-script-task.md)  
 Объясняется использование соединений с помощью свойства <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Connections%2A>.  
  
 [Вызов событий в задаче «Скрипт»](raising-events-in-the-script-task.md)  
 Объясняется инициирование событий с помощью свойства <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Events%2A>.  
  
 [Ведение журнала в задаче «Скрипт»](logging-in-the-script-task.md)  
 Объясняется регистрация сведений с помощью метода <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A>.  
  
 [Возврат результатов из задачи «Скрипт»](returning-results-from-the-script-task.md)  
 Объясняется возвращение результатов через свойства <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.TaskResult%2A> и <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.ExecutionValue%2A>.  
  
 [Примеры задачи «Скрипт»](../../extending-packages-scripting-task-examples/script-task-examples.md)  
 Содержит примеры, в которых показано несколько возможных использований задачи «Скрипт».  
  
![Значок служб Integration Services (маленький)](../../media/dts-16.gif "значок служб Integration Services (маленький)")**оставаться до даты со службами Integration Services** <br /> Загрузить последнюю документацию, статьи, примеры и видео с сайта [!INCLUDE[msCoName](../../../includes/msconame-md.md)], а также лучшие решения участников сообщества, посетите [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] на портале MSDN:<br /><br /> [Посетите страницу служб Integration Services на сайте MSDN](http://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Чтобы получать автоматические уведомления об этих обновлениях, подпишитесь на RSS-каналы, предлагаемые на этой странице.  
  
## <a name="see-also"></a>См. также  
 [Задача "Скрипт"](../../control-flow/script-task.md)   
 [Сравнение задачи «Скрипт» и компонента скрипта](../../extending-packages-scripting/comparing-the-script-task-and-the-script-component.md)  
  
  
