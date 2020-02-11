---
title: Расширение потока данных с помощью компонента скрипта | Документы Майкрософт
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
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
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 051f2ed14e8218a3909a43052f08e0e339138dab
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62894808"
---
# <a name="extending-the-data-flow-with-the-script-component"></a>Расширение потока данных с помощью компонента скрипта
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] Компонент скрипта расширяет возможности потока данных пакетов с помощью пользовательского кода, написанного [!INCLUDE[msCoName](../../../includes/msconame-md.md)] на Visual Basic [!INCLUDE[msCoName](../../../includes/msconame-md.md)] или Visual C#, который компилируется и выполняется во время выполнения пакета. Компонент «Скрипт» упрощает разработку пользовательских источников потоков данных, преобразований или назначений, если источники, преобразования и назначения, входящие в службы [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], не полностью удовлетворяют нуждам пользователя. После настройки компонент с расширенными входными и выходными данными пишет весь необходимый код инфраструктуры, позволяя сконцентрировать усилия исключительно на коде, который требуется для пользовательской обработки.  
  
 Компонент скрипта взаимодействует с пакетом, в котором он содержится, и с потоком данных с помощью автоматически сформированных классов в элементах проекта `ComponentWrapper` и `BufferWrapper`, являющихся экземплярами классов <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> и <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer> соответственно. Эти классы обеспечивают доступ к соединениям, переменным и другим элементам пакета как к типизированным объектам и управляют входными и выходными данными. Для реализации пользовательской функции компонент скрипта также может использовать пространство имен [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] и библиотеку классов платформы [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], а также пользовательские сборки.  
  
 Компонент скрипта и формируемый им код инфраструктуры значительно упрощают процесс создания пользовательских компонентов потока данных. Однако, чтобы понять, как работает компонент скрипта, может быть полезно прочитать раздел [Разработка пользовательского компонента потока данных](../../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md), в котором описываются шаги по разработке пользовательских компонентов потока данных.  
  
 При создании источника, преобразования или назначения, которые планируется повторно использовать в нескольких пакетах, следует создать пользовательский компонент, а не использовать компонент скрипта. Дополнительные сведения см. в разделе [Разработка пользовательского компонента потока данных](../../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md).  
  
## <a name="in-this-section"></a>в этом разделе  
 В следующих подразделах представлены дополнительные сведения о компоненте скрипта.  
  
 [Настройка компонента скрипта в редакторе компонента скрипта](configuring-the-script-component-in-the-script-component-editor.md)  
 Свойства, настраиваемые в **редакторе преобразования "Скрипт"**, влияют на возможности и производительность кода компонента скрипта.  
  
 [Написание кода и отладка компонента скрипта] (coding-and-debugging-the-script-component.md  
 Для разработки скриптов [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] , содержащихся в компоненте скрипта, используется среда разработки средств для приложений (VSTA).  
  
 [Основные сведения о модели объектов компонента скрипта](understanding-the-script-component-object-model.md)  
 Создаваемый проект компонента скрипта содержит три элемента проекта, а также несколько классов автоформируемых свойств и методов.  
  
 [Использование переменных в компоненте скрипта](using-variables-in-the-script-component.md)  
 Элемент проекта `ComponentWrapper` содержит свойства строго типизированных методов доступа для переменных пакета.  
  
 [Соединение с источниками данных в компоненте скрипта](connecting-to-data-sources-in-the-script-component.md)  
 Элемент проекта `ComponentWrapper` также содержит свойства строго типизированных методов доступа для соединений, определенных в пакете.  
  
 [Вызов событий в компоненте скрипта](raising-events-in-the-script-component.md)  
 Можно создавать события для уведомления о проблемах и ошибках.  
  
 [Ведение журнала в компоненте скрипта](logging-in-the-script-component.md)  
 Можно записывать сведения в регистраторы, включенные в пакете.  
  
 [Разработка компонентов скрипта определенных типов](../../extending-packages-scripting-data-flow-script-component-types/developing-specific-types-of-script-components.md)  
 Следующие простые примеры демонстрируют, как компонент скрипта используется для разработки источников потоков данных, преобразований и назначений.  
  
 [Дополнительные примеры компонента скрипта](../../extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md)  
 Следующие простые примеры демонстрируют несколько возможных способов использования компонента скрипта.  
  
![Значок Integration Services (маленький)](../../media/dts-16.gif "Значок служб Integration Services (маленький)")  **следит за обновлениями Integration Services**<br /> Чтобы загрузить новейшую документацию, статьи, образцы и видеоматериалы [!INCLUDE[msCoName](../../../includes/msconame-md.md)], а также лучшие решения участников сообщества, посетите страницу служб [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] на сайте MSDN:<br /><br /> [Посетить страницу «Службы Integration Services» на сайте MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Чтобы получать автоматические уведомления об этих обновлениях, подпишитесь на RSS-каналы, предлагаемые на этой странице.  
  
## <a name="see-also"></a>См. также:  
 [Компонент скрипта](../../data-flow/transformations/script-component.md)   
 [Сравнение задачи «Скрипт» и компонента скрипта](../comparing-the-script-task-and-the-script-component.md)  
  
  
