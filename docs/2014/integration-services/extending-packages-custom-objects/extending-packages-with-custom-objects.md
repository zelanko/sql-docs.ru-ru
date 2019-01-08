---
title: Расширение пакетов с помощью пользовательских объектов | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
ms.assetid: 26616eb8-9e80-434d-b22a-ece1b00f449d
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d7017ef85a86f16c94273db4d78980f510547320
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/13/2018
ms.locfileid: "53369866"
---
# <a name="extending-packages-with-custom-objects"></a>Расширение пакетов с помощью пользовательских объектов
  Если встроенные компоненты служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] не отвечают требованиям, их можно расширить, создав собственные программные расширения служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Существует два варианта расширения пакетов: можно написать код с использованием возможностей многофункциональных оболочек, предоставляемых задачей «Скрипт» и компонентом скрипта или самостоятельно создать пользовательские расширения служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], используя классы, производные от базовых классов, предоставляемых объектной моделью служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 В этом разделе подробно рассматривается расширение пакетов с помощью пользовательских объектов — вариант, предоставляющий более широкие возможности.  
  
 Если пользовательское решение служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] требует большей гибкости, чем обеспечивает задача или компонент «Скрипт», или если есть необходимость использования компонента, применение которого возможно в нескольких пакетах, модель объектов служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] позволяет создавать с нуля пользовательские задачи, компоненты потока данных и другие объекты пакета в управляемом коде.  
  
## <a name="in-this-section"></a>в этом разделе  
 [Разработка пользовательских объектов для служб Integration Services](developing-custom-objects-for-integration-services.md)  
 Описывает пользовательские объекты, которые можно создать для работы со службами [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], включая необходимые шаги и настройки.  
  
 [Сохранение пользовательских объектов](persisting-custom-objects.md)  
 Описывает механизм сохраняемости по умолчанию пользовательских объектов и процесс реализации пользовательской сохраняемости.  
  
 [Сборка, развертывание и отладка пользовательских объектов](building-deploying-and-debugging-custom-objects.md)  
 Описывает общие подходы к построению, развертыванию и тестированию различных типов пользовательских объектов.  
  
 [Разработка пользовательской задачи](task/developing-a-custom-task.md)  
 Описывает процесс программирования пользовательской задачи.  
  
 [Разработка пользовательского диспетчера соединений](connection-manager/developing-a-custom-connection-manager.md)  
 Описывает процесс программирования пользовательского диспетчера соединений.  
  
 [Разработка пользовательского регистратора](log-provider/developing-a-custom-log-provider.md)  
 Описывает процесс программирования пользовательского регистратора.  
  
 [Разработка пользовательского перечислителя по каждому элементу](foreach-enumerator/developing-a-custom-foreach-enumerator.md)  
 Описывает процесс программирования пользовательского перечислителя.  
  
 [Разработка пользовательского компонента потока данных](data-flow/developing-a-custom-data-flow-component.md)  
 Описывает вопросы программирования пользовательских источников, преобразований и назначений потока данных.  
  
## <a name="reference"></a>Справочник  
 [Справочник по сообщениям об ошибках служб Integration Services](../integration-services-error-and-message-reference.md)  
 Содержится список стандартных кодов ошибок служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] с символическими именами и описаниями.  
  
## <a name="related-sections"></a>См. также  
 [Расширение пакетов с помощью сценариев](../extending-packages-scripting/extending-packages-with-scripting.md)  
 Описывает способ расширения потока управления с помощью задачи «Скрипт» или потока данных с помощью компонента скрипта.  
  
 [Программное построение пакетов](../building-packages-programmatically/building-packages-programmatically.md)  
 Описывает создание, настройку, запуск, загрузку и сохранение пакетов служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] программным образом, а также программное выполнение других задач управления.  
  
![Значок служб Integration Services (маленький)](../media/dts-16.gif "значок служб Integration Services (маленький)")**оставаться до даты со службами Integration Services**<br /> Чтобы загрузить новейшую документацию, статьи, образцы и видеоматериалы корпорации Майкрософт, а также лучшие решения участников сообщества, посетите страницу служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] на сайте MSDN:<br /><br /> [Посетите страницу служб Integration Services на сайте MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Чтобы получать автоматические уведомления об этих обновлениях, подпишитесь на RSS-каналы, предлагаемые на этой странице.  
  
## <a name="see-also"></a>См. также  
 [Сравнение решений со скриптами и пользовательских объектов](../extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md)   
 [SQL Server Integration Services](../sql-server-integration-services.md)  
  
  
