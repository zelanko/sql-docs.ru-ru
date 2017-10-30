---
title: "Использование переменных в компоненте скрипта | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- Script component [Integration Services], using variables
ms.assetid: 92d1881a-1ef1-43ae-b1ca-48d0536bdbc2
caps.latest.revision: 13
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: bac1e6d96e872be0355282c3e12fc81054ca41cd
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="using-variables-in-the-script-component"></a>Использование переменных в компоненте скрипта
  Переменные хранят значения, которые пакет и его контейнеры, задачи и обработчики событий могут использовать во время выполнения. Дополнительные сведения см. в разделе [Integration Services &#40;SSIS&#41; Variables](../../../integration-services/integration-services-ssis-variables.md).  
  
 Можно сделать доступными для существующих переменных только для чтения или чтения и записи с помощью пользовательского скрипта, введя разделенные запятыми списки переменных в **ReadOnlyVariables** и **ReadWriteVariables** полей на **сценарий** страница **редактор преобразования «скрипт»**. Помните, что в именах переменных учитывается регистр. Используйте **значение** свойство для чтения и записи в отдельные переменные. Компонент скрипта обрабатывает любые необходимые блокировки в фоновом режиме, пока скрипт во время выполнения обрабатывает переменные.  
  
> [!IMPORTANT]  
>  Коллекция **ReadWriteVariables** доступна только в **PostExecute** способ повышения производительности и снижения риска конфликта блокировок. Поэтому нельзя непосредственно увеличивать значение переменной пакета после обработки каждой строки данных. Вместо этого увеличьте значение локальной переменной и присвоено значение переменной пакета значение локальной переменной в **PostExecute** метод после все данные были обработаны. Чтобы обойти это ограничение можно также использовать свойство <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.VariableDispenser%2A>, как описано ниже в этом разделе. Однако запись напрямую в переменную пакета по мере обработки каждой строки отрицательно скажется на производительности и увеличит риск конфликта блокировок.  
  
 Дополнительные сведения о **сценарий** страница **редактор преобразования «скрипт»**, в разделе [Настройка компонента скрипта в редакторе компонентов скрипта](../../../integration-services/extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md) и [редактор преобразования «скрипт» &#40; Страница «скрипт» &#41; ](../../../integration-services/data-flow/transformations/script-transformation-editor-script-page.md).  
  
 Компонент скрипта создает **переменных** класс коллекции в **ComponentWrapper** элемент проекта с помощью свойства строго типизированных методов доступа для значения каждой предварительно настроенной переменной, где свойство имеет то же имя, что и сама переменная. Эта коллекция предоставляется через **переменных** свойство **ScriptMain** класса. Свойство метода доступа предоставляет разрешения только для чтения или для чтения и записи значения этой переменной, в зависимости от ситуации. Например, если вы добавили целочисленная переменная с именем `MyIntegerVariable` для **ReadOnlyVariables** список, можно получить его значение в скрипте, используя следующий код:  
  
 `Dim myIntegerVariableValue As Integer = Me.Variables.MyIntegerVariable`  
  
 Для работы с переменными в компоненте скрипта можно также использовать свойство <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.VariableDispenser%2A>, вызвав метод `Me.VariableDispenser`. В этом случае доступ к переменным осуществляется напрямую, без использования типизированных и именованных свойств метода доступа к переменным. При использовании свойства <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.VariableDispenser%2A> необходимо обрабатывать в коде и семантику блокирования, и приведение типов данных для значений переменных. Необходимо использовать свойство <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.VariableDispenser%2A> вместо типизированных и именованных свойств метода доступа, если требуется работать с переменной, недоступной во время разработки, но создающейся программным способом во время выполнения.  
  
## <a name="see-also"></a>См. также:  
 [Службы Integration Services &#40; Службы SSIS &#41; Переменные](../../../integration-services/integration-services-ssis-variables.md)   
 [Использование переменных в пакетах](http://msdn.microsoft.com/library/7742e92d-46c5-4cc4-b9a3-45b688ddb787)  
  
  

