---
title: Разработка пользовательского регистратора | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- SSIS packages, log providers
- custom log providers [Integration Services]
- SQL Server Integration Services packages, log providers
- log providers [Integration Services]
- packages [Integration Services], logs
- Integration Services packages, log providers
ms.assetid: 3f715b95-7074-4f5c-8ae2-246998052e78
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 25531ce8e4a405b1e52a0f1f8d81fb536087cff7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62768610"
---
# <a name="developing-a-custom-log-provider"></a>Разработка пользовательского регистратора
  В службах [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] имеются различные возможности по ведению журналов, которые позволяют отслеживать события, возникающие во время выполнения пакетов. Службы [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] включают целый ряд регистраторов, используя которые можно создавать и сохранять журналы в различных форматах, например XML, текстовом, базы данных или в виде журнала событий Windows. Если предоставляемые регистраторы и форматы выходных данных не вполне отвечают вашим требованиям, вы можете создать пользовательский регистратор.  
  
 Чтобы создать пользовательский регистратор, необходимо создать класс, унаследованный от базового класса <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase>, применить к этому новому классу атрибут <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute> и переопределить важные методы и свойства базового класса, включая свойство <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.ConfigString%2A> и метод <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Log%2A>.  
  
## <a name="in-this-section"></a>в этом разделе  
 Этот раздел описывает создание, настройку и программирование пользовательского регистратора.  
  
 [Создание пользовательского регистратора](creating-a-custom-log-provider.md)  
 Описывает создание классов для проекта пользовательского регистратора.  
  
 [Создание кода пользовательского регистратора](coding-a-custom-log-provider.md)  
 Описывает реализацию пользовательского регистратора путем перекрытия методов и свойств базового класса.  
  
 [Разработка пользовательского интерфейса для пользовательского регистратора](developing-a-user-interface-for-a-custom-log-provider.md)  
 Настраиваемые пользовательские интерфейсы для пользовательских регистраторов не поддерживаются в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)].  
  
## <a name="related-topics"></a>Связанные темы  
  
### <a name="information-common-to-all-custom-objects"></a>Общие сведения для всех пользовательских объектов  
 Сведения, общие для всех типов пользовательских объектов, которые можно создавать в службах [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], см. в следующих разделах.  
  
 [Разработка пользовательских объектов для служб Integration Services](../developing-custom-objects-for-integration-services.md)  
 Описывает основные шаги по реализации всех типов пользовательских объектов для служб [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)].  
  
 [Сохранение пользовательских объектов](../persisting-custom-objects.md)  
 Описывает пользовательский механизм сохраняемости, при необходимости приводя пояснения.  
  
 [Построение, развертывание и отладка пользовательских объектов](../building-deploying-and-debugging-custom-objects.md)  
 Описывает методы построения, подписывания, развертывания и отладки пользовательских объектов.  
  
### <a name="information-about-other-custom-objects"></a>Сведения о других пользовательских объектах  
 Сведения о других типах пользовательских объектов, которые можно создавать в службах [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], см. в следующих разделах.  
  
 [Разработка пользовательской задачи](../task/developing-a-custom-task.md)  
 Описывает программирование пользовательских задач.  
  
 [Разработка пользовательского диспетчера соединений](../connection-manager/developing-a-custom-connection-manager.md)  
 Описывает вопросы программирования пользовательских диспетчеров соединений.  
  
 [Разработка пользовательского перечислителя по каждому элементу](../foreach-enumerator/developing-a-custom-foreach-enumerator.md)  
 Описывает вопросы программирования пользовательских перечислителей.  
  
 [Разработка пользовательского компонента потока данных](../data-flow/developing-a-custom-data-flow-component.md)  
 Описывает вопросы программирования пользовательских источников, преобразований и назначений потока данных.  
  
![Значок Integration Services (маленький)](../../media/dts-16.gif "Значок служб Integration Services (маленький)")  **следит за обновлениями Integration Services**<br /> Чтобы загрузить новейшую документацию, статьи, образцы и видеоматериалы корпорации Майкрософт, а также лучшие решения участников сообщества, посетите страницу служб [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] на сайте MSDN:<br /><br /> [Посетить страницу «Службы Integration Services» на сайте MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Чтобы получать автоматические уведомления об этих обновлениях, подпишитесь на RSS-каналы, предлагаемые на этой странице.  
  
  
