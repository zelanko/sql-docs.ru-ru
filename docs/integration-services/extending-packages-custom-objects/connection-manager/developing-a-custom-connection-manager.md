---
description: Разработка пользовательского диспетчера соединений
title: Разработка пользовательского диспетчера соединений | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
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
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ad61fc88b68d2df7fb04839ef0f8fc3978a05e14
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88484269"
---
# <a name="developing-a-custom-connection-manager"></a>Разработка пользовательского диспетчера соединений

[!INCLUDE[sqlserver-ssis](../../../includes/applies-to-version/sqlserver-ssis.md)]


  Службы [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] инкапсулируют сведения, необходимые для подключения к внешнему источнику данных, с помощью диспетчеров соединений. В службах [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] имеются различные диспетчеры соединений, поддерживающие соединения с наиболее распространенными источниками данных, от корпоративных баз данных до текстовых файлов и книг Excel. Если набор диспетчеров соединений и внешних источников данных, поддерживаемых службами [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], не отвечает потребностям пользователя, можно создать пользовательский диспетчер соединений.  
  
 Для создания пользовательского диспетчера соединений необходимо создать класс, наследующий от базового класса <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase>, применить атрибут <xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute> к новому классу и переопределить важные методы и свойства базового класса, в том числе свойство <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.ConnectionString%2A> и метод <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.AcquireConnection%2A>.  
  
> [!IMPORTANT]  
>  Большая часть задач, источников и назначений в службах [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] работает только с определенными типами встроенных диспетчеров соединений. Прежде чем приступить к разработке пользовательского диспетчера соединений для использования со встроенными задачами и компонентами, необходимо выяснить, ограничивается ли список диспетчеров соединений, применимых для этих компонентов, каким-либо определенным типом. Если для решения необходим пользовательский диспетчер соединений, также может понадобиться разработать пользовательскую задачу, источник или назначение для работы с пользовательским диспетчером.  
  
## <a name="in-this-section"></a>в этом разделе  
 В этом разделе описывается, как создавать, настраивать и кодировать пользовательский диспетчер соединений и, при необходимости, его пользовательский интерфейс. Фрагменты кода, приведенные в этом разделе, являются производными от образца пользовательского диспетчера соединений SQL Server.  
  
 [Создание пользовательского диспетчера соединений](../../../integration-services/extending-packages-custom-objects/connection-manager/creating-a-custom-connection-manager.md)  
 Описывает, как создать классы для проекта пользовательского диспетчера соединений.  
  
 [Написание кода пользовательского диспетчера соединений](../../../integration-services/extending-packages-custom-objects/connection-manager/coding-a-custom-connection-manager.md)  
 Описывает, как реализовать пользовательский диспетчер соединений путем переопределения методов и свойств базового класса.  
  
 [Разработка пользовательского интерфейса для пользовательского диспетчера соединений](../../../integration-services/extending-packages-custom-objects/connection-manager/developing-a-user-interface-for-a-custom-connection-manager.md)  
 Описывает, как реализовать класс пользовательского интерфейса и форму, используемую для настройки пользовательского диспетчера соединений.  
  
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
  
 [Разработка пользовательского регистратора](../../../integration-services/extending-packages-custom-objects/log-provider/developing-a-custom-log-provider.md)  
 Описывает вопросы программирования пользовательских регистраторов.  
  
 [Разработка пользовательского перечислителя по каждому элементу](../../../integration-services/extending-packages-custom-objects/foreach-enumerator/developing-a-custom-foreach-enumerator.md)  
 Описывает вопросы программирования пользовательских перечислителей.  
  
 [Разработка пользовательского компонента потока данных](../../../integration-services/extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md)  
 Описывает вопросы программирования пользовательских источников, преобразований и назначений потока данных.  
  
