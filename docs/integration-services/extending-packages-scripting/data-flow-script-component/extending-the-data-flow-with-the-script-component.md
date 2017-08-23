---
title: "Расширение потока данных с помощью компонента скрипта | Документы Microsoft"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
dev_langs:
- VB
helpviewer_keywords:
- data flow task [Integration Services], components
- data flow [Integration Services], extending
- debugging [Integration Services], components
- code design mode [Integration Services]
- metadata [Integration Services]
- scripts [Integration Services], extending data flow
- data flow components [Integration Services], Script component
- components [Integration Services], data flow
- Script component [Integration Services], about Script component
- Script component [Integration Services]
- data flow [Integration Services], components
ms.assetid: 072bc4b8-363a-4131-87c3-240338e2fa5c
caps.latest.revision: 46
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: c58a854082fcbd12333be63995e4fcdf2d55aac7
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="extending-the-data-flow-with-the-script-component"></a>Extending the Data Flow with the Script Component
  Компонент скрипта расширяет возможности потока данных [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] пакеты с пользовательским кодом, написанным [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic или [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C#, который компилируется и выполняется во время выполнения пакета. Компонент «Скрипт» упрощает разработку пользовательских источников потоков данных, преобразований или назначений, если источники, преобразования и назначения, входящие в службы [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], не полностью удовлетворяют нуждам пользователя. После настройки компонент с расширенными входными и выходными данными пишет весь необходимый код инфраструктуры, позволяя сконцентрировать усилия исключительно на коде, который требуется для пользовательской обработки.  
  
 Компонент скрипта взаимодействует с содержащим их пакетом и с потоком данных с помощью автоматически сформированных классов в **ComponentWrapper** и **BufferWrapper** элементы, которые являются экземплярами проекта из <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> и <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer> классы соответственно. Эти классы обеспечивают доступ к соединениям, переменным и другим элементам пакета как к типизированным объектам и управляют входными и выходными данными. Для реализации пользовательской функции компонент скрипта также может использовать пространство имен [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] и библиотеку классов платформы [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], а также пользовательские сборки.  
  
 Компонент скрипта и формируемый им код инфраструктуры значительно упрощают процесс создания пользовательских компонентов потока данных. Тем не менее, чтобы понять, как работает компонент скрипта, вам может быть полезно прочитать раздел [разработке пользовательского компонента потока данных](../../../integration-services/extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md) для понимания шагов, которые участвуют в разработке пользовательского компонента потока данных.  
  
 При создании источника, преобразования или назначения, которые планируется повторно использовать в нескольких пакетах, следует создать пользовательский компонент, а не использовать компонент скрипта. Дополнительные сведения см. в разделе [Разработка пользовательского компонента потока данных](../../../integration-services/extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md).  
  
## <a name="in-this-section"></a>В этом разделе  
 В следующих подразделах представлены дополнительные сведения о компоненте скрипта.  
  
 [Настройка компонента скрипта в редакторе компонентов скрипта](../../../integration-services/extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md)  
 Свойства, которые можно настроить в **редактор преобразования «скрипт»** влияют на возможности и производительность кода компонента скрипта.  
  
 [Кодирование и отладка компонента скрипта](../../../integration-services/extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md)  
 Вы используете [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] средства среды разработки приложений (VSTA) для разработки скриптов, содержащихся в компоненте скрипта.  
  
 [Основные сведения о модели объектов компонента скрипта](../../../integration-services/extending-packages-scripting/data-flow-script-component/understanding-the-script-component-object-model.md)  
 Создаваемый проект компонента скрипта содержит три элемента проекта, а также несколько классов автоформируемых свойств и методов.  
  
 [Использование переменных в компоненте скрипта](../../../integration-services/extending-packages-scripting/data-flow-script-component/using-variables-in-the-script-component.md)  
 **ComponentWrapper** элемент проекта содержит свойства строго типизированных методов доступа для переменных пакета.  
  
 [Подключение к источникам данных в компоненте скрипта](../../../integration-services/extending-packages-scripting/data-flow-script-component/connecting-to-data-sources-in-the-script-component.md)  
 **ComponentWrapper** элемент проекта также содержит свойства строго типизированных методов доступа для соединений, определенных в пакете.  
  
 [Создание событий в компоненте скрипта](../../../integration-services/extending-packages-scripting/data-flow-script-component/raising-events-in-the-script-component.md)  
 Можно создавать события для уведомления о проблемах и ошибках.  
  
 [Ведение журнала в компоненте скрипта](../../../integration-services/extending-packages-scripting/data-flow-script-component/logging-in-the-script-component.md)  
 Можно записывать сведения в регистраторы, включенные в пакете.  
  
 [Разработка компонентов скрипта определенных типов](../../../integration-services/extending-packages-scripting-data-flow-script-component-types/developing-specific-types-of-script-components.md)  
 Следующие простые примеры демонстрируют, как компонент скрипта используется для разработки источников потоков данных, преобразований и назначений.  
  
 [Дополнительные примеры компонента скрипта](../../../integration-services/extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md)  
 Следующие простые примеры демонстрируют несколько возможных способов использования компонента скрипта.  
  
## <a name="see-also"></a>См. также:  
 [Компонент скрипта](../../../integration-services/data-flow/transformations/script-component.md)   
 [Сравнение задачи «скрипт» и компоненте скрипта](../../../integration-services/extending-packages-scripting/comparing-the-script-task-and-the-script-component.md)  
  
  
