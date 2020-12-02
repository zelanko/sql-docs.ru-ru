---
description: Расширение потока данных с помощью компонента скрипта
title: Расширение потока данных с помощью компонента скрипта | Документы Майкрософт
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
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
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 82f34ab83935bee2972a4dbb2b007eb2632b9fba
ms.sourcegitcommit: 192f6a99e19e66f0f817fdb1977f564b2aaa133b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/25/2020
ms.locfileid: "96122937"
---
# <a name="extending-the-data-flow-with-the-script-component"></a>Расширение потока данных с помощью компонента скрипта

[!INCLUDE[sqlserver-ssis](../../../includes/applies-to-version/sqlserver-ssis.md)]


  Компонент "Скрипт" расширяет возможности по работе с потоком данных пакетов служб [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] с пользовательским кодом, написанным на языке [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic или [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C#, который компилируется и выполняется во время выполнения пакетов. Компонент «Скрипт» упрощает разработку пользовательских источников потоков данных, преобразований или назначений, если источники, преобразования и назначения, входящие в службы [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], не полностью удовлетворяют нуждам пользователя. После настройки компонент с расширенными входными и выходными данными пишет весь необходимый код инфраструктуры, позволяя сконцентрировать усилия исключительно на коде, который требуется для пользовательской обработки.  
  
 Компонент скрипта взаимодействует с пакетом, в котором он содержится, и с потоком данных с помощью автоматически сформированных классов в элементах проекта **ComponentWrapper** и **BufferWrapper**, являющихся экземплярами классов <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> и <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer> соответственно. Эти классы обеспечивают доступ к соединениям, переменным и другим элементам пакета как к типизированным объектам и управляют входными и выходными данными. Для реализации пользовательской функции компонент скрипта также может использовать пространство имен [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] и библиотеку классов платформы [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], а также пользовательские сборки.  
  
 Компонент скрипта и формируемый им код инфраструктуры значительно упрощают процесс создания пользовательских компонентов потока данных. Однако, чтобы понять, как работает компонент скрипта, может быть полезно прочитать раздел [Разработка пользовательского компонента потока данных](../../../integration-services/extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md), в котором описываются шаги по разработке пользовательских компонентов потока данных.  
  
 При создании источника, преобразования или назначения, которые планируется повторно использовать в нескольких пакетах, следует создать пользовательский компонент, а не использовать компонент скрипта. Дополнительные сведения см. в разделе [Разработка пользовательского компонента потока данных](../../../integration-services/extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md).  
  
## <a name="in-this-section"></a>в этом разделе  
 В следующих подразделах представлены дополнительные сведения о компоненте скрипта.  
  
 [Настройка компонента скрипта в редакторе компонента скрипта](../../../integration-services/extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md)  
 Свойства, настраиваемые в **редакторе преобразования "Скрипт"**, влияют на возможности и производительность кода компонента скрипта.  
  
 [Кодирование и отладка компонента скрипта](../../../integration-services/extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md)  
 Для разработки скриптов, содержащихся в компоненте скрипта, используется среда разработки на базе набора средств [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] для работы с приложениями (VSTA).  
  
 [Основные сведения о модели объектов компонента скрипта](../../../integration-services/extending-packages-scripting/data-flow-script-component/understanding-the-script-component-object-model.md)  
 Создаваемый проект компонента скрипта содержит три элемента проекта, а также несколько классов автоформируемых свойств и методов.  
  
 [Использование переменных в компоненте скрипта](../../../integration-services/extending-packages-scripting/data-flow-script-component/using-variables-in-the-script-component.md)  
 Элемент проекта **ComponentWrapper** содержит свойства строго типизированных методов доступа для переменных пакета.  
  
 [Соединение с источниками данных в компоненте скрипта](../../../integration-services/extending-packages-scripting/data-flow-script-component/connecting-to-data-sources-in-the-script-component.md)  
 Элемент проекта **ComponentWrapper** также содержит свойства строго типизированных методов доступа для соединений, определенных в пакете.  
  
 [Вызов событий в компоненте скрипта](../../../integration-services/extending-packages-scripting/data-flow-script-component/raising-events-in-the-script-component.md)  
 Можно создавать события для уведомления о проблемах и ошибках.  
  
 [Ведение журнала в компоненте скрипта](../../../integration-services/extending-packages-scripting/data-flow-script-component/logging-in-the-script-component.md)  
 Можно записывать сведения в регистраторы, включенные в пакете.  
  
 [Разработка компонентов скрипта определенных типов](../../../integration-services/extending-packages-scripting-data-flow-script-component-types/developing-specific-types-of-script-components.md)  
 Следующие простые примеры демонстрируют, как компонент скрипта используется для разработки источников потоков данных, преобразований и назначений.  
  
 [Дополнительные примеры компонента скрипта](../../../integration-services/extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md)  
 Следующие простые примеры демонстрируют несколько возможных способов использования компонента скрипта.  
  
## <a name="see-also"></a>См. также  
 [Компонент скрипта](../../../integration-services/data-flow/transformations/script-component.md)   
 [Сравнение задачи «Скрипт» и компонента скрипта](../../../integration-services/extending-packages-scripting/comparing-the-script-task-and-the-script-component.md)  
  
  
