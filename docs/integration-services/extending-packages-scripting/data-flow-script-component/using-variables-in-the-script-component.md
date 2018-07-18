---
title: Использование переменных в компоненте скрипта | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: integration-services
ms.component: extending-packages-scripting
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- Script component [Integration Services], using variables
ms.assetid: 92d1881a-1ef1-43ae-b1ca-48d0536bdbc2
caps.latest.revision: 13
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: a67c9d59dd2a9eccf6ac19e99dab860cf57d1279
ms.sourcegitcommit: cc46afa12e890edbc1733febeec87438d6051bf9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/12/2018
ms.locfileid: "35405276"
---
# <a name="using-variables-in-the-script-component"></a>Использование переменных в компоненте скрипта
  Переменные хранят значения, которые пакет и его контейнеры, задачи и обработчики событий могут использовать во время выполнения. Дополнительные сведения см. в разделе [Integration Services &#40;SSIS&#41; Variables](../../../integration-services/integration-services-ssis-variables.md).  
  
 Существующие переменные можно сделать доступными только для чтения или чтения и записи с помощью пользовательского скрипта, введя список значений, разделенных запятыми, в поля **ReadOnlyVariables** и **ReadWriteVariables** на странице **Скрипт** в окне **Редактор преобразования "Скрипт"**. Помните, что в именах переменных учитывается регистр. Используйте свойство **Value**, чтобы считывать значения отдельных переменных и записывать значения в них. Компонент скрипта обрабатывает любые необходимые блокировки в фоновом режиме, пока скрипт во время выполнения обрабатывает переменные.  
  
> [!IMPORTANT]  
>  Коллекция **ReadWriteVariables** доступна только в методе **PostExecute** для повышения производительности и снижения риска конфликта блокировок. Поэтому нельзя непосредственно увеличивать значение переменной пакета после обработки каждой строки данных. Вместо этого увеличьте значение локальной переменной и присвойте значение переменной пакета локальной переменной в методе **PostExecute** после того, как все данные обработаны. Чтобы обойти это ограничение можно также использовать свойство <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.VariableDispenser%2A>, как описано ниже в этом разделе. Однако запись напрямую в переменную пакета по мере обработки каждой строки отрицательно скажется на производительности и увеличит риск конфликта блокировок.  
  
 Дополнительные сведения о странице **Скрипт** окна **Редактор преобразования "Скрипт"** см. в разделах [Настройка компонента скрипта в редакторе компонента скрипта](../../../integration-services/extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md) и [Редактор преобразования "Скрипт" (страница "Скрипт")](../../../integration-services/data-flow/transformations/script-transformation-editor-script-page.md).  
  
 Компонент скрипта создает класс коллекции **Variables** в элементе проекта **ComponentWrapper** со строго типизированным свойством метода доступа для значения каждой предварительно настроенной переменной, в которой свойство имеет то же самое имя, что и сама переменная. Эта коллекция доступна с помощью свойства **Variables** класса **ScriptMain**. Свойство метода доступа предоставляет разрешения только для чтения или для чтения и записи значения этой переменной, в зависимости от ситуации. Например, если к списку **ReadOnlyVariables** добавлена целочисленная переменная с именем `MyIntegerVariable`, ее значение можно получить в скрипте с помощью следующего кода:  
  
 `Dim myIntegerVariableValue As Integer = Me.Variables.MyIntegerVariable`  
  
 Для работы с переменными в компоненте скрипта можно также использовать свойство <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.VariableDispenser%2A>, вызвав метод `Me.VariableDispenser`. В этом случае доступ к переменным осуществляется напрямую, без использования типизированных и именованных свойств метода доступа к переменным. При использовании свойства <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.VariableDispenser%2A> необходимо обрабатывать в коде и семантику блокирования, и приведение типов данных для значений переменных. Необходимо использовать свойство <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.VariableDispenser%2A> вместо типизированных и именованных свойств метода доступа, если требуется работать с переменной, недоступной во время разработки, но создающейся программным способом во время выполнения.  
  
## <a name="see-also"></a>См. также:  
 [Переменные в службах Integration Services (SSIS)](../../../integration-services/integration-services-ssis-variables.md)   
 [Использование переменных в пакетах](http://msdn.microsoft.com/library/7742e92d-46c5-4cc4-b9a3-45b688ddb787)  
  
  
