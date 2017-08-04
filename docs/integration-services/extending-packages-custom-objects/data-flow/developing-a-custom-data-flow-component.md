---
title: "Разработка пользовательского компонента потока данных | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
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
- CSharp
helpviewer_keywords:
- data flow task [Integration Services], extending
- data flow [Integration Services], extending
- extending data flow task [Integration Services]
- components [Integration Services], data flow
ms.assetid: be126913-2a9a-41c9-9bf5-a7b0a0aea2f8
caps.latest.revision: 57
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: f25c74b52eaccb6c7b0e92cb7dace3d56f3cdd83
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="developing-a-custom-data-flow-component"></a>Разработка пользовательского компонента потока данных
  Задача потока данных состоит из компонентов, которые соединяются с различными источниками данных, а затем преобразуют и перенаправляют данные с высокой скоростью. [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] предоставляет модель расширяемых объектов, которая позволяет разработчикам создавать пользовательские источники, преобразования и назначения, которые можно использовать в [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] и развернутых пакетов. В этом разделе содержатся инструкции и рекомендации по разработке пользовательских компонентов потока данных.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Создание пользовательского компонента потока данных](../../../integration-services/extending-packages-custom-objects/data-flow/creating-a-custom-data-flow-component.md)  
 Описывает первые шаги создания пользовательского компонента потока данных.  
  
 [Методы времени разработки компонента потока данных](../../../integration-services/extending-packages-custom-objects/data-flow/design-time-methods-of-a-data-flow-component.md)  
 Описывает методы времени разработки, реализуемые в пользовательском компоненте потока данных.  
  
 [Методы во время выполнения компонента потока данных](../../../integration-services/extending-packages-custom-objects/data-flow/run-time-methods-of-a-data-flow-component.md)  
 Описывает методы времени выполнения, реализуемые в пользовательском компоненте потока данных.  
  
 [План выполнения и выделения буфера](../../../integration-services/extending-packages-custom-objects/data-flow/execution-plan-and-buffer-allocation.md)  
 Описывает план выполнения потока данных и выделение буферов данных.  
  
 [Работа с типами данных в потоке данных](../../../integration-services/extending-packages-custom-objects/data-flow/working-with-data-types-in-the-data-flow.md)  
 Поясняет, как поток данных сопоставляет типы данных служб [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] с управляемыми типами данных платформы .NET Framework.  
  
 [Проверка компоненте потока данных](../../../integration-services/extending-packages-custom-objects/data-flow/validating-a-data-flow-component.md)  
 Поясняет методы, используемые для проверки конфигурации компонента и изменения метаданных компонента.  
  
 [Реализация внешних метаданных](../../../integration-services/extending-packages-custom-objects/data-flow/implementing-external-metadata.md)  
 Поясняет, как использовать столбцы внешних метаданных для проверки данных.  
  
 [Компонент потока вызов и определение событий в данных.](../../../integration-services/extending-packages-custom-objects/data-flow/raising-and-defining-events-in-a-data-flow-component.md)  
 Поясняет, как формировать стандартные и пользовательские события.  
  
 [Компонент потока ведение журнала и определение элементов журнала в данных.](../../../integration-services/extending-packages-custom-objects/data-flow/logging-and-defining-log-entries-in-a-data-flow-component.md)  
 Поясняет, как создавать и записывать пользовательские записи журнала.  
  
 [Использование выводов ошибок в компоненте потока данных](../../../integration-services/extending-packages-custom-objects/data-flow/using-error-outputs-in-a-data-flow-component.md)  
 Поясняет, как перенаправлять строки ошибок на альтернативный выход.  
  
 [Обновление версии компонента потока данных](../../../integration-services/extending-packages-custom-objects/data-flow/upgrading-the-version-of-a-data-flow-component.md)  
 Поясняет, как обновлять метаданные сохраненного компонента при первом использовании новой версии компонента.  
  
 [Разработка пользовательского интерфейса для компонента потока данных](../../../integration-services/extending-packages-custom-objects/data-flow/developing-a-user-interface-for-a-data-flow-component.md)  
 Поясняет, как реализовать пользовательский редактор для компонента.  
  
 [Компоненты потока данных разработки определенных типов](../../../integration-services/extending-packages-custom-objects-data-flow-types/developing-specific-types-of-data-flow-components.md)  
 Содержит сведения о разработке трех типов компонентов потока данных: источников, преобразований и объектов назначения.  
  
## <a name="reference"></a>Справочник  
 <xref:Microsoft.SqlServer.Dts.Pipeline>  
 Содержит классы и интерфейсы, используемые для создания пользовательских компонентов потока данных.  
  
 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper>  
 Содержит классы и интерфейсы, которые составляют модель объектов задачи потока данных. Используется для создания пользовательских компонентов потока данных или построения задачи потока данных.  
  
 <xref:Microsoft.SqlServer.Dts.Pipeline.Design>  
 Содержит классы и интерфейсы, используемые для создания пользовательского интерфейса для компонентов потока данных.  
  
 [Об ошибках служб Integration Services и справочник по сообщениям](../../../integration-services/integration-services-error-and-message-reference.md)  
 Содержится список стандартных кодов ошибок служб [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] с символическими именами и описаниями.  
  
## <a name="related-sections"></a>См. также  
  
### <a name="information-common-to-all-custom-objects"></a>Общие сведения для всех пользовательских объектов  
 Сведения, общие для всех типов пользовательских объектов, которые можно создавать в службах [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], см. в следующих разделах.  
  
 [Разработка пользовательских объектов для служб Integration Services](../../../integration-services/extending-packages-custom-objects/developing-custom-objects-for-integration-services.md)  
 Описывает основные шаги по реализации всех типов пользовательских объектов для служб [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)].  
  
 [Сохранение пользовательских объектов](../../../integration-services/extending-packages-custom-objects/persisting-custom-objects.md)  
 Описывает пользовательский механизм сохраняемости, при необходимости приводя пояснения.  
  
 [Сборка, развертывание и отладка пользовательских объектов](../../../integration-services/extending-packages-custom-objects/building-deploying-and-debugging-custom-objects.md)  
 Описывает методы построения, подписывания, развертывания и отладки пользовательских объектов.  
  
### <a name="information-about-other-custom-objects"></a>Сведения о других пользовательских объектах  
 Сведения о других типах пользовательских объектов, которые можно создавать в службах [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], см. в следующих разделах.  
  
 [Разработка пользовательской задачи](../../../integration-services/extending-packages-custom-objects/task/developing-a-custom-task.md)  
 Описывает программирование пользовательских задач.  
  
 [Разработка пользовательского диспетчера соединений](../../../integration-services/extending-packages-custom-objects/connection-manager/developing-a-custom-connection-manager.md)  
 Описывает вопросы программирования пользовательских диспетчеров соединений.  
  
 [Разработка пользовательского регистратора](../../../integration-services/extending-packages-custom-objects/log-provider/developing-a-custom-log-provider.md)  
 Описывает вопросы программирования пользовательских регистраторов.  
  
 [Разработка пользовательских перечислитель](../../../integration-services/extending-packages-custom-objects/foreach-enumerator/developing-a-custom-foreach-enumerator.md)  
 Описывает вопросы программирования пользовательских перечислителей.  
  
## <a name="see-also"></a>См. также:  
 [Расширение потока данных с помощью компонента скрипта](../../../integration-services/extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md)   
 [Сравнение решений со сценариями и пользовательских объектов](../../../integration-services/extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md)  
  
  
