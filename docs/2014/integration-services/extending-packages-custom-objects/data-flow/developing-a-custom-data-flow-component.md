---
title: Разработка пользовательского компонента потока данных | Документы Майкрософт
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data flow task [Integration Services], extending
- data flow [Integration Services], extending
- extending data flow task [Integration Services]
- components [Integration Services], data flow
ms.assetid: be126913-2a9a-41c9-9bf5-a7b0a0aea2f8
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 061daaa3b44c151a1f77b075bef66ef90570af98
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "78176354"
---
# <a name="developing-a-custom-data-flow-component"></a>Разработка пользовательского компонента потока данных
  Задача потока данных состоит из компонентов, которые соединяются с различными источниками данных, а затем преобразуют и перенаправляют данные с высокой скоростью. Службы [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] предоставляют модель расширяемых объектов, которая позволяет разработчикам создавать пользовательские источники, преобразования и назначения, которые можно использовать в среде [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] и в развернутых пакетах. В этом разделе содержатся инструкции и рекомендации по разработке пользовательских компонентов потока данных.

## <a name="in-this-section"></a>в этом разделе
 [Создание пользовательского компонента потока данных](creating-a-custom-data-flow-component.md) Описывает начальные шаги при создании пользовательского компонента потока данных.

 [Методы времени разработки компонента потока данных](design-time-methods-of-a-data-flow-component.md) Описывает методы времени разработки для реализации в пользовательском компоненте потока данных.

 [Методы времени выполнения компонента потока данных](run-time-methods-of-a-data-flow-component.md) Описывает методы времени выполнения для реализации в пользовательском компоненте потока данных.

 [План выполнения и выделение буфера](execution-plan-and-buffer-allocation.md) Описывает план выполнения потока данных и выделение буферов данных.

 [Работа с типами данных в потоке данных](working-with-data-types-in-the-data-flow.md) Объясняет, как поток данных сопоставляет [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] типы данных с .NET Framework управляемыми типами данных.

 [Проверка компонента потока данных](validating-a-data-flow-component.md) Описывает методы, используемые для проверки конфигурации компонента и для перенастройки метаданных компонента.

 [Реализация внешних метаданных](implementing-external-metadata.md) Объясняет, как использовать столбцы внешних метаданных для проверки данных.

 [Вызов и определение событий в компоненте потока данных](raising-and-defining-events-in-a-data-flow-component.md) Объясняет, как создавать стандартные и пользовательские события.

 [Ведение журнала и определение записей журнала в компоненте потока данных](logging-and-defining-log-entries-in-a-data-flow-component.md) Объясняет, как создавать и записывать данные в пользовательские записи журнала.

 [Использование вывода ошибок в компоненте потока данных](using-error-outputs-in-a-data-flow-component.md) Объясняет, как перенаправлять строки ошибок в альтернативный выход.

 [Обновление версии компонента потока данных](upgrading-the-version-of-a-data-flow-component.md) Объясняет, как обновить метаданные сохраненного компонента при первом использовании новой версии компонента.

 [Разработка пользовательского интерфейса для компонента потока данных](developing-a-user-interface-for-a-data-flow-component.md) Объясняет, как реализовать пользовательский редактор для компонента.

 [Разработка конкретных типов компонентов потока данных](../../extending-packages-custom-objects-data-flow-types/developing-specific-types-of-data-flow-components.md) Содержит сведения о разработке трех типов компонентов потока данных: источников, преобразований и назначений.

## <a name="reference"></a>Справочник
 <xref:Microsoft.SqlServer.Dts.Pipeline>Содержит классы и интерфейсы, используемые для создания пользовательских компонентов потока данных.

 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper>Содержит классы и интерфейсы, которые составляют объектную модель задачи «Поток данных» и используются для создания пользовательских компонентов потока данных или построения задачи потока данных.

 <xref:Microsoft.SqlServer.Dts.Pipeline.Design>Содержит классы и интерфейсы, используемые для создания пользовательского интерфейса для компонентов потока данных.

 [Справочник по ошибкам и сообщениям Integration Services](../../integration-services-error-and-message-reference.md) Список стандартных [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] кодов ошибок со своими символическими именами и описаниями.

## <a name="related-sections"></a>Связанные разделы

### <a name="information-common-to-all-custom-objects"></a>Общие сведения для всех пользовательских объектов
 Сведения, общие для всех типов пользовательских объектов, которые можно создавать в службах [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], см. в следующих разделах.

 [Разработка пользовательских объектов для Integration Services](../../extending-packages-custom-objects/developing-custom-objects-for-integration-services.md) Описывает основные шаги реализации всех типов пользовательских объектов для [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)].

 [Сохранение пользовательских объектов](../../extending-packages-custom-objects/persisting-custom-objects.md) Описывает пользовательскую сохраняемость и объясняет, когда это необходимо.

 [Сборка, развертывание и отладка пользовательских объектов](../../extending-packages-custom-objects/building-deploying-and-debugging-custom-objects.md) Описывает методы создания, подписывания, развертывания и отладки пользовательских объектов.

### <a name="information-about-other-custom-objects"></a>Сведения о других пользовательских объектах
 Сведения о других типах пользовательских объектов, которые можно создавать в службах [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], см. в следующих разделах.

 [Разработка пользовательской задачи](../../extending-packages-custom-objects/task/developing-a-custom-task.md) Описывает, как программировать пользовательские задачи.

 [Разработка пользовательского диспетчера соединений](../../extending-packages-custom-objects/connection-manager/developing-a-custom-connection-manager.md) Описывает, как программировать пользовательские диспетчеры соединений.

 [Разработка пользовательского регистратора](../../extending-packages-custom-objects/log-provider/developing-a-custom-log-provider.md) Описывает, как программировать пользовательские регистраторы.

 [Разработка пользовательского перечислителя Foreach](../../extending-packages-custom-objects/foreach-enumerator/developing-a-custom-foreach-enumerator.md) Описывает, как программировать пользовательские перечислители.

![Значок Integration Services (маленький)](../../media/dts-16.gif "Значок служб Integration Services (маленький)")  **следит за обновлениями Integration Services**<br /> Чтобы загрузить новейшую документацию, статьи, образцы и видеоматериалы корпорации Майкрософт, а также лучшие решения участников сообщества, посетите страницу служб [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] на сайте MSDN:<br /><br /> [Посетить страницу «Службы Integration Services» на сайте MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Чтобы получать автоматические уведомления об этих обновлениях, подпишитесь на RSS-каналы, предлагаемые на этой странице.

## <a name="see-also"></a>См. также:
 [Расширение потока данных с помощью компонента скрипта] (.. /.. /екстендинг-паккажес-скриптинг/Дата-Флов-скрипт-компонент/екстендинг-СЕ-Дата-Флов-ВИС-СЕ-скрипт-компонент.МД [Сравнение решений сценариев и пользовательских объектов](../../extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md)


