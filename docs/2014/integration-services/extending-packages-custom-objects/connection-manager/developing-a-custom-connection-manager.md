---
title: Разработка пользовательского диспетчера соединений | Документы Майкрософт
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- integration-services
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- packages [Integration Services], connections
- custom connection managers [Integration Services], about custom connection managers
- connection managers [Integration Services], custom
- Integration Services packages, connection managers
- SSIS packages, connection managers
- SQL Server Integration Services packages, connection managers
- custom connection managers [Integration Services]
ms.assetid: bda0b29e-57f5-4879-b04d-1396dc56daa8
caps.latest.revision: 21
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: f0d1f1c94415556f3d9930f3ef878ae8d0a9498b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36180317"
---
# <a name="developing-a-custom-connection-manager"></a>Разработка пользовательского диспетчера соединений
  Службы [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] инкапсулируют сведения, необходимые для подключения к внешнему источнику данных, с помощью диспетчеров соединений. В службах [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] имеются различные диспетчеры соединений, поддерживающие соединения с наиболее распространенными источниками данных, от корпоративных баз данных до текстовых файлов и книг Excel. Если набор диспетчеров соединений и внешних источников данных, поддерживаемых службами [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], не отвечает потребностям пользователя, можно создать пользовательский диспетчер соединений.  
  
 Для создания пользовательского диспетчера соединений необходимо создать класс, наследующий от базового класса <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase>, применить атрибут <xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute> к новому классу и переопределить важные методы и свойства базового класса, в том числе свойство <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.ConnectionString%2A> и метод <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.AcquireConnection%2A>.  
  
> [!IMPORTANT]  
>  Большая часть задач, источников и назначений в службах [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] работает только с определенными типами встроенных диспетчеров соединений. Прежде чем приступить к разработке пользовательского диспетчера соединений для использования со встроенными задачами и компонентами, необходимо выяснить, ограничивается ли список диспетчеров соединений, применимых для этих компонентов, каким-либо определенным типом. Если для решения необходим пользовательский диспетчер соединений, также может понадобиться разработать пользовательскую задачу, источник или назначение для работы с пользовательским диспетчером.  
  
## <a name="in-this-section"></a>в этом разделе  
 В этом разделе описывается, как создавать, настраивать и кодировать пользовательский диспетчер соединений и, при необходимости, его пользовательский интерфейс. Фрагменты кода, приведенные в этом разделе, являются производными от образца пользовательского диспетчера соединений SQL Server.  
  
 [Создание пользовательского диспетчера соединений](creating-a-custom-connection-manager.md)  
 Описывает, как создать классы для проекта пользовательского диспетчера соединений.  
  
 [Написание кода пользовательского диспетчера соединений](coding-a-custom-connection-manager.md)  
 Описывает, как реализовать пользовательский диспетчер соединений путем переопределения методов и свойств базового класса.  
  
 [Разработка пользовательского интерфейса для пользовательского диспетчера соединений](developing-a-user-interface-for-a-custom-connection-manager.md)  
 Описывает, как реализовать класс пользовательского интерфейса и форму, используемую для настройки пользовательского диспетчера соединений.  
  
## <a name="related-sections"></a>См. также  
  
### <a name="information-common-to-all-custom-objects"></a>Общие сведения для всех пользовательских объектов  
 Сведения, общие для всех типов пользовательских объектов, которые можно создавать в службах [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], см. в следующих разделах.  
  
 [Разработка пользовательских объектов для служб Integration Services](../developing-custom-objects-for-integration-services.md)  
 Описывает основные шаги по реализации всех типов пользовательских объектов для служб [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)].  
  
 [Сохранение пользовательских объектов](../persisting-custom-objects.md)  
 Описывает пользовательский механизм сохраняемости, при необходимости приводя пояснения.  
  
 [Сборка, развертывание и отладка пользовательских объектов](../building-deploying-and-debugging-custom-objects.md)  
 Описывает методы построения, подписывания, развертывания и отладки пользовательских объектов.  
  
### <a name="information-about-other-custom-objects"></a>Сведения о других пользовательских объектах  
 Сведения о других типах пользовательских объектов, которые можно создавать в службах [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], см. в следующих разделах.  
  
 [Разработка пользовательской задачи](../task/developing-a-custom-task.md)  
 Описывает программирование пользовательских задач.  
  
 [Разработка пользовательского регистратора](../log-provider/developing-a-custom-log-provider.md)  
 Описывает вопросы программирования пользовательских регистраторов.  
  
 [Разработка пользовательского перечислителя по каждому элементу](../foreach-enumerator/developing-a-custom-foreach-enumerator.md)  
 Описывает вопросы программирования пользовательских перечислителей.  
  
 [Разработка пользовательского компонента потока данных](../data-flow/developing-a-custom-data-flow-component.md)  
 Описывает вопросы программирования пользовательских источников, преобразований и назначений потока данных.  
  
![Значок служб Integration Services (маленький)](../../media/dts-16.gif "значок служб Integration Services (маленький)")**оставаться установка последних со службами Integration Services** <br /> Чтобы загрузить новейшую документацию, статьи, образцы и видеоматериалы корпорации Майкрософт, а также лучшие решения участников сообщества, посетите страницу служб [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] на сайте MSDN:<br /><br /> [Посетите страницу служб Integration Services в MSDN](http://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Чтобы получать автоматические уведомления об этих обновлениях, подпишитесь на RSS-каналы, предлагаемые на этой странице.  
  
  