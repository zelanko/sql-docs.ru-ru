---
title: "Настройка задачи «скрипт» в редакторе задачи скрипта | Документы Microsoft"
ms.custom: 
ms.date: 03/15/2017
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
- Script task [Integration Services], configuring
- Script Task Editor
- SSIS Script task, configuring
ms.assetid: 232de0c9-b24d-4c38-861d-6c1f4a75bdf3
caps.latest.revision: 35
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 182a7b8f04c2339a8f3d3b986c978a7998c8a9c3
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="configuring-the-script-task-in-the-script-task-editor"></a>Настройка задачи «Скрипт» в редакторе задачи «Скрипт»
  Прежде чем писать пользовательский код в задаче «скрипт», настройте ее основные свойства на трех страницах **редактор задачи «скрипт»**. Дополнительные свойства задачи, не уникальные для задачи «Скрипт», можно настроить в окне «Свойства».  
  
> [!NOTE]  
>  В отличие от предыдущих версий, где можно было указать, являются ли скрипты предварительно скомпилированными, начиная с версии [!INCLUDE[ssISversion10](../../../includes/ssisversion10-md.md)] все скрипты компилируются заранее.  
  
## <a name="general-page-of-the-script-task-editor"></a>Страница «Общие свойства» окна «Редактор задачи "Скрипт"»  
 На **Общие** страница **редактор задачи «скрипт»**, присвоить уникальное имя и описание для задачи «скрипт».  
  
## <a name="script-page-of-the-script-task-editor"></a>Страница «Скрипт» окна «Редактор задачи "Скрипт"»  
 **Сценарий** страница **редактор задачи «скрипт»** отображает пользовательские свойства задачи «скрипт».  
  
### <a name="scriptlanguage-property"></a>Свойство ScriptLanguage  
 [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Средств для приложений (VSTA) поддерживает [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic или [!INCLUDE[msCoName](../../../includes/msconame-md.md)] языки программирования Visual C#. После создания скрипта в задаче «скрипт», не удается изменить значение **ScriptLanguage** свойство.  
  
 Чтобы задать язык сценариев по умолчанию для компонентов скрипта и задач, используйте **ScriptLanguage** свойство **Общие** страница **параметры** диалоговое окно. Дополнительные сведения см. в разделе [General Page](https://msdn.microsoft.com/library/ms189436(v=sql.110).aspx).  
  
### <a name="entrypoint-property"></a>Свойство EntryPoint  
 **EntryPoint** свойство задает метод на **ScriptMain** класса в VSTA проектом, [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] вызывают во время выполнения как точку входа в код задачи скрипта. **ScriptMain** классом является класс по умолчанию, созданных шаблонами скриптов.  
  
 Для изменения имени метода в проекте VSTA следует поменять значение свойства **EntryPoint** .  
  
### <a name="readonlyvariables-and-readwritevariables-properties"></a>Свойства ReadOnlyVariables и ReadWriteVariables  
 В качестве значений этих свойств можно ввести разделенные запятыми списки существующих переменных, чтобы обеспечить доступ к ним в коде задачи «Скрипт» в режиме только для чтения или чтения и записи. Переменные обоих типов доступны в коде с помощью <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> свойство **Dts** объекта. Дополнительные сведения см. в статье [Using Variables in the Script Task](../../../integration-services/extending-packages-scripting/task/using-variables-in-the-script-task.md).  
  
> [!NOTE]  
>  В именах переменных учитывается регистр букв.  
  
 Чтобы выбрать переменные, нажмите кнопку с многоточием (**...** ) рядом с полем свойства. Дополнительные сведения см. в разделе [Выбор переменных страницы](../../../integration-services/control-flow/select-variables-page.md).  
  
### <a name="edit-script-button"></a>Кнопка «Изменить скрипт»  
 **Изменить скрипт** кнопка запускает среду разработки VSTA, в котором можно написать пользовательский скрипт. Дополнительные сведения см. в разделе [кодировании и отладке задачи «скрипт»](../../../integration-services/extending-packages-scripting/task/coding-and-debugging-the-script-task.md).  
  
## <a name="expressions-page-of-the-script-task-editor"></a>Страница «Выражения» окна «Редактор задачи "Скрипт"»  
 На **выражений** страница **редактор задачи «скрипт»**, можно использовать выражения для предоставления значений для свойств задачи «скрипт», перечисленных выше, а также для многих других свойств задач. Дополнительные сведения см. в разделе [Выражения служб Integration Services (SSIS)](../../../integration-services/expressions/integration-services-ssis-expressions.md).  
  
## <a name="see-also"></a>См. также:  
 [Кодирование и отладка задачи «скрипт»](../../../integration-services/extending-packages-scripting/task/coding-and-debugging-the-script-task.md)  
  
  
