---
title: Разработка пользовательской задачи | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
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
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 7f597ee3a063da534267f7d4674a024a8fcc02f1
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "62896145"
---
# <a name="developing-a-custom-task"></a>Разработка пользовательской задачи
  Для выполнения элементов работы, направленных на обеспечение извлечения, преобразования и загрузки данных службы [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] используют задачи. В службах [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] имеются различные задачи, выполняющие наиболее часто используемые действия, от извлечения инструкции SQL до загрузки файла с FTP-сайта. Если имеющиеся задачи и поддерживаемые действия не удовлетворяют потребностям пользователя, можно создать пользовательскую задачу.  
  
 Для создания пользовательской задачи необходимо создать класс, наследующий от базового класса <xref:Microsoft.SqlServer.Dts.Runtime.Task>, применить атрибут <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute> к новому классу и переопределить важные методы и свойства базового класса, в том числе метод <xref:Microsoft.SqlServer.Dts.Runtime.Task.Execute%2A>.  
  
## <a name="in-this-section"></a>в этом разделе  
 В этом разделе описывается, как создавать, настраивать и кодировать пользовательскую задачу и, при необходимости, пользовательский интерфейс.  
  
 [Создание пользовательской задачи](creating-a-custom-task.md)  
 Описывает первый шаг, состоящий в создании пользовательской задачи.  
  
 [Создание кода пользовательской задачи](coding-a-custom-task.md)  
 Описывает, как кодировать основные методы пользовательской задачи.  
  
 [Соединение с источниками данных в пользовательской задаче](connecting-to-data-sources-in-a-custom-task.md)  
 Описывает, как соединить пользовательскую задачу с источником данных.  
  
 [Вызов и определение событий в пользовательской задаче](raising-and-defining-events-in-a-custom-task.md)  
 Описывает, как обеспечить вызов событий и определить пользовательские события для пользовательской задачи.  
  
 [Добавление поддержки отладки в пользовательскую задачу](adding-support-for-debugging-in-a-custom-task.md)  
 Описывает, как создать целевые объекты точек останова в пользовательской задаче.  
  
 [Разработка пользовательского интерфейса для пользовательской задачи](developing-a-user-interface-for-a-custom-task.md)  
 Описывает, как создать пользовательский интерфейс, отображаемый в конструкторе служб [!INCLUDE[ssIS](../../../includes/ssis-md.md)] для настройки свойств пользовательской задачи.  
  
## <a name="related-sections"></a>См. также  
  
### <a name="information-common-to-all-custom-objects"></a>Общие сведения для всех пользовательских объектов  
 Сведения, общие для всех типов пользовательских объектов, которые можно создавать в службах [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], см. в следующих разделах.  
  
 [Разработка пользовательских объектов для служб Integration Services](../developing-custom-objects-for-integration-services.md)  
 Описывает основные шаги реализации всех типов пользовательских объектов для служб [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)].  
  
 [Сохранение пользовательских объектов](../persisting-custom-objects.md)  
 Описывает пользовательский механизм сохраняемости, при необходимости приводя пояснения.  
  
 [Сборка, развертывание и отладка пользовательских объектов](../building-deploying-and-debugging-custom-objects.md)  
 Описывает методы построения, подписывания, развертывания и отладки пользовательских объектов.  
  
### <a name="information-about-other-custom-objects"></a>Сведения о других пользовательских объектах  
 Сведения о других типах пользовательских объектов, которые можно создавать в службах [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], см. в следующих разделах.  
  
 [Разработка пользовательского диспетчера соединений](../connection-manager/developing-a-custom-connection-manager.md)  
 Описывает вопросы программирования пользовательских диспетчеров соединений.  
  
 [Разработка пользовательского регистратора](../log-provider/developing-a-custom-log-provider.md)  
 Описывает вопросы программирования пользовательских регистраторов.  
  
 [Разработка пользовательского перечислителя по каждому элементу](../foreach-enumerator/developing-a-custom-foreach-enumerator.md)  
 Описывает вопросы программирования пользовательских перечислителей.  
  
 [Разработка пользовательского компонента потока данных](../data-flow/developing-a-custom-data-flow-component.md)  
 Описывает вопросы программирования пользовательских источников, преобразований и назначений потока данных.  
  
![Значок Integration Services (маленький)](../../media/dts-16.gif "Значок служб Integration Services (маленький)")  **следит за обновлениями Integration Services**<br /> Чтобы загрузить новейшую документацию, статьи, образцы и видеоматериалы корпорации Майкрософт, а также лучшие решения участников сообщества, посетите страницу служб [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] на сайте MSDN:<br /><br /> [Посетить страницу «Службы Integration Services» на сайте MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Чтобы получать автоматические уведомления об этих обновлениях, подпишитесь на RSS-каналы, предлагаемые на этой странице.  
  
## <a name="see-also"></a>См. также  
 [Расширение пакета с помощью задачи «Скрипт»](../../extending-packages-scripting/task/extending-the-package-with-the-script-task.md)   
 [Сравнение решений со сценариями и пользовательских объектов](../../extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md)  
  
  
