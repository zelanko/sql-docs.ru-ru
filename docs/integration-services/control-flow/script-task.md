---
title: "Задаче «скрипт» | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.scripttask.f1
helpviewer_keywords:
- scripts [Integration Services], tasks
- Script task [Integration Services], about Script task
- Script task [Integration Services]
ms.assetid: f6cce7df-4bd6-4b75-9f89-6c37b4bb5558
caps.latest.revision: 67
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: c3e47e4a5ae297202ba43679fba393421880a7ea
ms.openlocfilehash: 0ab143db0dfc6cda94bd0ba5e51fec66da7b46be
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="script-task"></a>Задача «Скрипт»
  Задача "Скрипт" представляет код для выполнения функций, недоступных в задачах и преобразованиях, предоставляемых средствами служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Задача «Скрипт» также позволяет объединять функции в одном скрипте вместо использования нескольких задач и преобразований. Задачу «Скрипт» следует использовать для выполнения операций над пакетом (или над каждым перечисленным объектом), а не над каждой строкой данных.  
  
 Задача «Скрипт» позволяет выполнять следующее:  
  
-   Получать доступ к данным с помощью дополнительных технологий, не поддерживаемых встроенными типами соединений. Например, скрипт может использовать интерфейсы служб каталогов Active Directory (ADSI) для обращения и извлечения имен пользователей из Active Directory.  
  
-   Создавать счетчики производительности специально для конкретного пакета. Например, скрипт может создать счетчик производительности, обновляемый при выполнении сложной или медленно работающей задачи.  
  
-   Определять, пусты ли указанные файлы или сколько строк в них содержится, а затем на основании этой оценки влиять на поток управления в пакете. Например, если в файле нет строк, значение переменной равно 0, а управление очередностью, вычисляющее значение, не позволяет задаче «Файловая система» копировать файл.  
  
 Если необходимо использовать скрипт для выполнения одинаковых операций над каждой строкой в наборе, следует использовать компонент скрипта, а не задачу «Скрипт». Например, если необходимо определить адекватность почтовых расходов и пропустить записи с очень большими или очень маленькими суммами, следует использовать компонент скрипта. Дополнительные сведения см. в статье [Script Component](../../integration-services/data-flow/transformations/script-component.md).  
  
 Если скрипт используется несколькими пакетами, рекомендуется написать пользовательскую задачу, а не использовать задачу «Скрипт». Дополнительные сведения см. в разделе [Разработка пользовательской задачи](../../integration-services/extending-packages-custom-objects/task/developing-a-custom-task.md).  
  
 Если в пакете решено использовать задачу «Скрипт», необходимо разработать скрипт, используемый задачей, и настроить саму задачу.  
  
## <a name="writing-and-running-the-script-that-the-task-uses"></a>Разработка и выполнение скрипта, используемого задачей  
 Задача "Скрипт" использует средства [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] для приложений (VSTA) в качестве среды для разработки скриптов и обработчика, выполняющего эти скрипты.  
  
 Среда VSTA располагает всеми стандартными функциями среды [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , в том числе редактором [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] с выделением цветом, технологией IntelliSense и **обозревателем объектов**. Среда VSTA использует тот же отладчик, что и другие средства разработки [!INCLUDE[msCoName](../../includes/msconame-md.md)] . Точки останова в скрипте прозрачно совмещаются с точками останова в задачах и контейнерах служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Среда VSTA поддерживает языки программирования [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic и [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C#.  
  
 Чтобы запустить скрипт, на компьютере, где работает пакет, должна быть установлена среда VSTA. При выполнении пакета задача загружает ядро скрипта и запускает его. Обращаться к внешним сборкам .NET в скриптах можно, добавив ссылки на них в проект.  
  
> [!NOTE]  
>  В отличие от предыдущих версий, где можно было указать, являются ли скрипты предварительно скомпилированными, в версии [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] и более поздних версиях все скрипты компилируются заранее. Если скрипт компилируется заранее, то во время выполнения не загружается языковая подсистема и пакет выполняется быстрее. Однако заранее скомпилированные двоичные файлы занимают значительное место на диске.  
  
## <a name="configuring-the-script-task"></a>Настройка задачи «Скрипт»  
 Задачу «Скрипт» можно настроить следующими способами:  
  
-   Предоставить пользовательский скрипт, выполняемый задачей.  
  
-   Укажите в проекте VSTA метод, который службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] вызывают во время выполнения как точку входа в код задачи «Скрипт».  
  
-   Укажите язык скрипта.  
  
-   При необходимости предоставить списки используемых в скрипте переменных чтения и записи и только чтения.  
  
 Эти свойства можно задать с помощью конструктора служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] или программно.  
  
### <a name="configuring-the-script-task-in-the-designer"></a>Настройка задачи «Скрипт» в конструкторе  
 В следующей таблице описано событие **ScriptTaskLogEntry** , которое может быть зарегистрировано для задачи «Скрипт». Событие **ScriptTaskLogEntry** выбирается для регистрации на вкладке **Подробности** диалогового окна **Настройка журналов служб SSIS** . Дополнительные сведения см. в разделе [Ведение журналов в службах Integration Services (SSIS)](../../integration-services/performance/integration-services-ssis-logging.md).  
  
|Запись журнала|Description|  
|---------------|-----------------|  
|**ScriptTaskLogEntry**|Сообщает о результатах выполнения операции ведения журнала в скрипте. Задача формирует запись журнала для каждого вызова метода **Log** объекта **Dts** . Задача формирует эти записи в момент запуска кода. Дополнительные сведения см. в статье [Logging in the Script Task](../../integration-services/extending-packages-scripting/task/logging-in-the-script-task.md).|  
  
 Дополнительные сведения о свойствах, которые можно задать в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] , см. в следующих разделах:  
  
-   [Редактор задачи "Скрипт" (страница "Общие")](../../integration-services/control-flow/script-task-editor-general-page.md)  
  
-   [Редактор задачи "Скрипт" (страница "Скрипт")](../../integration-services/control-flow/script-task-editor-script-page.md)  
  
-   [Страница «Выражения»](../../integration-services/expressions/expressions-page.md)  
  
 Дополнительные сведения об установке этих свойств в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] см. в следующем разделе:  
  
-   [Задание свойств задач или контейнеров](http://msdn.microsoft.com/library/52d47ca4-fb8c-493d-8b2b-48bb269f859b)  
  
### <a name="configuring-the-script-task-programmatically"></a>Программная настройка задачи «Скрипт»  
 Дополнительные сведения о программной установке этих свойств см. в следующем разделе:  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptTask>  
  
## <a name="related-content"></a>См. также  
  
-   Техническая статья [How to send email with delivery notification in C#](http://go.microsoft.com/fwlink/?LinkId=237625)на сайте shareourideas.com  
  
  
