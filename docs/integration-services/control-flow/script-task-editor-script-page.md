---
title: "Редактор задачи &#171;Скрипт&#187; (страница &#171;Скрипт&#187;) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.scripttask.script.f1"
helpviewer_keywords: 
  - "редактор задачи «Скрипт»"
ms.assetid: 93da0e0d-83f5-406d-b144-4cce216571cb
caps.latest.revision: 42
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 40
---
# Редактор задачи &#171;Скрипт&#187; (страница &#171;Скрипт&#187;)
  Используйте страницу **Скрипт** в диалоговом окне **Редактор задачи «Скрипт»** , чтобы задать свойства скрипта и указать переменные, к которым скрипт будет иметь доступ.  
  
> [!NOTE]  
>  В [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] и более поздних версиях все скрипты предварительно скомпилированы. В предыдущих версиях для предварительной компиляции необходимо было установить свойство **PrecompileScriptIntoBinaryCode** .  
  
 Дополнительные сведения о задаче «Скрипт» см. в разделах [Script Task](../../integration-services/control-flow/script-task.md) и [Configuring the Script Task in the Script Task Editor](../../integration-services/extending-packages-scripting/task/configuring-the-script-task-in-the-script-task-editor.md). Дополнительные сведения о программировании задачи «Скрипт» см. в разделе [Extending the Package with the Script Task](../../integration-services/extending-packages-scripting/task/extending-the-package-with-the-script-task.md).  
  
## Параметры  
 **ScriptLanguage**  
 Выберите используемый для задачи язык скрипта: [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic или [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C#.  
  
 Изменить значение свойства **ScriptLanguage** для задачи после создания скрипта нельзя.  
  
 Чтобы установить значение по умолчанию языка скрипта для задачи «Скрипт», воспользуйтесь параметром **Язык скрипта** страницы **Общие** диалогового окна **Параметры** . Дополнительные сведения см. в разделе [General Page](../Topic/General%20Page.md).  
  
 **EntryPoint**  
 Укажите метод, вызываемый средой выполнения служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], в качестве точки входа в код задачи "Скрипт". Этот метод должен быть членом класса ScriptMain проекта [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA). ScriptMain является заданным по умолчанию классом, который создается в шаблонах скриптов.  
  
 Для изменения имени метода в проекте VSTA следует поменять значение свойства **EntryPoint** .  
  
 **ReadOnlyVariables**  
 Введите через запятую список переменных "только для чтения", которые доступны для скрипта, или нажмите кнопку с многоточием (**…**) и выберите переменные в диалоговом окне **Выбор переменных**.  
  
> [!NOTE]  
>  В именах переменных учитывается регистр.  
  
 **ReadWriteVariables**  
 Введите через запятую список переменных "для чтения и записи", которые доступны для скрипта, или нажмите кнопку с многоточием (**…**) и выберите переменные в диалоговом окне **Выбор переменных**.  
  
> [!NOTE]  
>  В именах переменных учитывается регистр.  
  
 **Изменение скрипта**  
 Открывает среду VSTA IDE, в которой можно создать или изменить скрипт.  
  
## См. также  
 [Справочник по сообщениям об ошибках служб Integration Services](../../integration-services/integration-services-error-and-message-reference.md)   
 [Страница «Общие»](../Topic/General%20Page.md)   
 [Редактор задачи "Скрипт" (страница "Общие")](../../integration-services/control-flow/script-task-editor-general-page.md)   
 [Страница «Выражения»](../../integration-services/expressions/expressions-page.md)   
 [Примеры задачи «Скрипт»](../../integration-services/extending-packages-scripting-task-examples/script-task-examples.md)   
 [Переменные в службах Integration Services (SSIS)](../../integration-services/integration-services-ssis-variables.md)   
 [Добавление, удаление и изменение области определяемой пользователем переменной в пакете](../Topic/Add,%20Delete,%20Change%20Scope%20of%20User-Defined%20Variable%20in%20a%20Package.md)  
  
  