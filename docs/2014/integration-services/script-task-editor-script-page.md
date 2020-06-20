---
title: Редактор задачи «Скрипт» (страница «Скрипт») | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.scripttask.script.f1
helpviewer_keywords:
- Script Task Editor
ms.assetid: 93da0e0d-83f5-406d-b144-4cce216571cb
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 8e9e9aef856276508ef557d465c20210e16f3073
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84964204"
---
# <a name="script-task-editor-script-page"></a>Редактор задачи «Скрипт» (страница «Скрипт»)
  Используйте страницу **Скрипт** в диалоговом окне **Редактор задачи «Скрипт»** , чтобы задать свойства скрипта и указать переменные, к которым скрипт будет иметь доступ.  
  
> [!NOTE]  
>  В [!INCLUDE[ssISversion10](../includes/ssisversion10-md.md)] и более поздних версиях все скрипты предварительно скомпилированы. В предыдущих версиях для предварительной компиляции необходимо было установить свойство **PrecompileScriptIntoBinaryCode** .  
  
 Дополнительные сведения о задаче «Скрипт» см. в разделах [Script Task](control-flow/script-task.md) и [Настройка задачи «Скрипт» в редакторе задачи «Скрипт»](extending-packages-scripting/task/configuring-the-script-task-in-the-script-task-editor.md). Дополнительные сведения о программировании задачи «Скрипт» см. в разделе [Extending the Package with the Script Task](extending-packages-scripting/task/extending-the-package-with-the-script-task.md).  
  
## <a name="options"></a>Варианты  
 **ScriptLanguage**  
 Выберите используемый для задачи язык скрипта: [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual Basic или [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual C#.  
  
 Изменить значение свойства **ScriptLanguage** для задачи после создания скрипта нельзя.  
  
 Чтобы установить значение по умолчанию языка скрипта для задачи «Скрипт», воспользуйтесь параметром **Язык скрипта** страницы **Общие** диалогового окна **Параметры** . Дополнительные сведения см. в разделе [General Page](general-page-of-integration-services-designers-options.md).  
  
 **EntryPoint**  
 Укажите метод, вызываемый средой выполнения служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , в качестве точки входа в код задачи "Скрипт". Указанный метод должен находиться в классе ScriptMain [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] проекта Tools for Applications (VSTA). класс ScriptMain является классом по умолчанию, созданным шаблонами скриптов.  
  
 Для изменения имени метода в проекте VSTA следует поменять значение свойства **EntryPoint** .  
  
 **ReadOnlyVariables**  
 Введите через запятую список переменных "только для чтения", которые доступны для скрипта, или нажмите кнопку с многоточием (**...**) и выберите переменные в диалоговом окне **Выбор переменных**.  
  
> [!NOTE]  
>  В именах переменных учитывается регистр.  
  
 **ReadWriteVariables**  
 Введите через запятую список переменных "для чтения и записи", которые доступны для скрипта, или нажмите кнопку с многоточием (**...**) и выберите переменные в диалоговом окне **Выбор переменных**.  
  
> [!NOTE]  
>  В именах переменных учитывается регистр.  
  
 **Изменение скрипта**  
 Открывает среду VSTA IDE, в которой можно создать или изменить скрипт.  
  
## <a name="see-also"></a>См. также:  
 [Справочник по ошибкам и сообщениям Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Страница "Общие"](general-page-of-integration-services-designers-options.md)   
 [Редактор задачи "Скрипт" &#40;страница "Общие"&#41;](../../2014/integration-services/script-task-editor-general-page.md)   
 [Страница "выражения"](expressions/expressions-page.md)   
 [Примеры задач "Скрипт"](extending-packages-scripting-task-examples/script-task-examples.md)   
 [Integration Services &#40;переменные&#41; SSIS](integration-services-ssis-variables.md)   
 [Добавление, удаление и изменение области определяемой пользователем переменной в пакете](../../2014/integration-services/add-delete-change-scope-of-user-defined-variable-in-a-package.md)  
  
  
