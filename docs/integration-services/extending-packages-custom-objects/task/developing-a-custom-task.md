---
title: "Разработка пользовательской задачи | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: extending-packages-custom-objects
ms.reviewer: 
ms.suite: sql
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
- custom tasks [Integration Services], about custom tasks
- Task class
- custom tasks [Integration Services]
- SSIS custom tasks
- SSIS custom tasks, about custom tasks
- IDtsTaskUI interface
- DtsTaskAttribute attribute
- tasks [Integration Services], custom
- TaskHost object
ms.assetid: dcbd8615-fa6d-4ddb-b8a5-0b19dddd6239
caps.latest.revision: 67
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: a6f9c16453365ce5b7a278f352c8cec8d86c2780
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="developing-a-custom-task"></a>Разработка пользовательской задачи
  Для выполнения элементов работы, направленных на обеспечение извлечения, преобразования и загрузки данных службы [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] используют задачи. В службах [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] имеются различные задачи, выполняющие наиболее часто используемые действия, от извлечения инструкции SQL до загрузки файла с FTP-сайта. Если имеющиеся задачи и поддерживаемые действия не удовлетворяют потребностям пользователя, можно создать пользовательскую задачу.  
  
 Для создания пользовательской задачи необходимо создать класс, наследующий от базового класса <xref:Microsoft.SqlServer.Dts.Runtime.Task>, применить атрибут <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute> к новому классу и переопределить важные методы и свойства базового класса, в том числе метод <xref:Microsoft.SqlServer.Dts.Runtime.Task.Execute%2A>.  
  
## <a name="in-this-section"></a>В этом разделе  
 В этом разделе описывается, как создавать, настраивать и кодировать пользовательскую задачу и, при необходимости, пользовательский интерфейс.  
  
 [Создание пользовательской задачи](../../../integration-services/extending-packages-custom-objects/task/creating-a-custom-task.md)  
 Описывает первый шаг, состоящий в создании пользовательской задачи.  
  
 [Программирования пользовательской задачи](../../../integration-services/extending-packages-custom-objects/task/coding-a-custom-task.md)  
 Описывает, как кодировать основные методы пользовательской задачи.  
  
 [Подключение к источникам данных в пользовательской задаче](../../../integration-services/extending-packages-custom-objects/task/connecting-to-data-sources-in-a-custom-task.md)  
 Описывает, как соединить пользовательскую задачу с источником данных.  
  
 [Вызов и определение событий в пользовательской задаче](../../../integration-services/extending-packages-custom-objects/task/raising-and-defining-events-in-a-custom-task.md)  
 Описывает, как обеспечить вызов событий и определить пользовательские события для пользовательской задачи.  
  
 [Добавление поддержки отладки в пользовательской задаче](../../../integration-services/extending-packages-custom-objects/task/adding-support-for-debugging-in-a-custom-task.md)  
 Описывает, как создать целевые объекты точек останова в пользовательской задаче.  
  
 [Разработка пользовательского интерфейса для пользовательской задачи](../../../integration-services/extending-packages-custom-objects/task/developing-a-user-interface-for-a-custom-task.md)  
 Описывает, как создать пользовательский интерфейс, отображаемый в конструкторе служб [!INCLUDE[ssIS](../../../includes/ssis-md.md)] для настройки свойств пользовательской задачи.  
  
## <a name="related-sections"></a>См. также  
  
### <a name="information-common-to-all-custom-objects"></a>Общие сведения для всех пользовательских объектов  
 Сведения, общие для всех типов пользовательских объектов, которые можно создавать в службах [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], см. в следующих разделах.  
  
 [Разработка пользовательских объектов для служб Integration Services](../../../integration-services/extending-packages-custom-objects/developing-custom-objects-for-integration-services.md)  
 Описывает основные шаги реализации всех типов пользовательских объектов для служб [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)].  
  
 [Сохранение пользовательских объектов](../../../integration-services/extending-packages-custom-objects/persisting-custom-objects.md)  
 Описывает пользовательский механизм сохраняемости, при необходимости приводя пояснения.  
  
 [Сборка, развертывание и отладка пользовательских объектов](../../../integration-services/extending-packages-custom-objects/building-deploying-and-debugging-custom-objects.md)  
 Описывает методы построения, подписывания, развертывания и отладки пользовательских объектов.  
  
### <a name="information-about-other-custom-objects"></a>Сведения о других пользовательских объектах  
 Сведения о других типах пользовательских объектов, которые можно создавать в службах [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], см. в следующих разделах.  
  
 [Разработка пользовательского диспетчера соединений](../../../integration-services/extending-packages-custom-objects/connection-manager/developing-a-custom-connection-manager.md)  
 Описывает вопросы программирования пользовательских диспетчеров соединений.  
  
 [Разработка пользовательского регистратора](../../../integration-services/extending-packages-custom-objects/log-provider/developing-a-custom-log-provider.md)  
 Описывает вопросы программирования пользовательских регистраторов.  
  
 [Разработка пользовательских перечислитель](../../../integration-services/extending-packages-custom-objects/foreach-enumerator/developing-a-custom-foreach-enumerator.md)  
 Описывает вопросы программирования пользовательских перечислителей.  
  
 [Разработка пользовательского компонента потока данных](../../../integration-services/extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md)  
 Описывает вопросы программирования пользовательских источников, преобразований и назначений потока данных.  
  
## <a name="see-also"></a>См. также:  
 [Расширение пакетов с помощью задачи «скрипт»](../../../integration-services/extending-packages-scripting/task/extending-the-package-with-the-script-task.md)   
 [Сравнение решений со сценариями и пользовательских объектов](../../../integration-services/extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md)  
  
  

