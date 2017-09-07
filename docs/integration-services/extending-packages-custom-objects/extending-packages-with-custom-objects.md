---
title: "Расширение пакетов с помощью пользовательских объектов | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: 26616eb8-9e80-434d-b22a-ece1b00f449d
caps.latest.revision: 36
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: e10fbab75eca8556e36734c1c0ad3828b8b09404
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="extending-packages-with-custom-objects"></a>Расширение пакетов с помощью пользовательских объектов
  Если встроенные компоненты служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] не отвечают требованиям, их можно расширить, создав собственные программные расширения служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Существует два варианта расширения пакетов: можно написать код с использованием возможностей многофункциональных оболочек, предоставляемых задачей «Скрипт» и компонентом скрипта или самостоятельно создать пользовательские расширения служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], используя классы, производные от базовых классов, предоставляемых объектной моделью служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 В этом разделе подробно рассматривается расширение пакетов с помощью пользовательских объектов — вариант, предоставляющий более широкие возможности.  
  
 Если пользовательское решение служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] требует большей гибкости, чем обеспечивает задача или компонент «Скрипт», или если есть необходимость использования компонента, применение которого возможно в нескольких пакетах, модель объектов служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] позволяет создавать с нуля пользовательские задачи, компоненты потока данных и другие объекты пакета в управляемом коде.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Разработка пользовательских объектов для служб Integration Services](../../integration-services/extending-packages-custom-objects/developing-custom-objects-for-integration-services.md)  
 Описывает пользовательские объекты, которые можно создать для работы со службами [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], включая необходимые шаги и настройки.  
  
 [Сохранение пользовательских объектов](../../integration-services/extending-packages-custom-objects/persisting-custom-objects.md)  
 Описывает механизм сохраняемости по умолчанию пользовательских объектов и процесс реализации пользовательской сохраняемости.  
  
 [Сборка, развертывание и отладка пользовательских объектов](../../integration-services/extending-packages-custom-objects/building-deploying-and-debugging-custom-objects.md)  
 Описывает общие подходы к построению, развертыванию и тестированию различных типов пользовательских объектов.  
  
 [Разработка пользовательской задачи](../../integration-services/extending-packages-custom-objects/task/developing-a-custom-task.md)  
 Описывает процесс программирования пользовательской задачи.  
  
 [Разработка пользовательского диспетчера соединений](../../integration-services/extending-packages-custom-objects/connection-manager/developing-a-custom-connection-manager.md)  
 Описывает процесс программирования пользовательского диспетчера соединений.  
  
 [Разработка пользовательского регистратора](../../integration-services/extending-packages-custom-objects/log-provider/developing-a-custom-log-provider.md)  
 Описывает процесс программирования пользовательского регистратора.  
  
 [Разработка пользовательских перечислитель](../../integration-services/extending-packages-custom-objects/foreach-enumerator/developing-a-custom-foreach-enumerator.md)  
 Описывает процесс программирования пользовательского перечислителя.  
  
 [Разработка пользовательского компонента потока данных](../../integration-services/extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md)  
 Описывает вопросы программирования пользовательских источников, преобразований и назначений потока данных.  
  
## <a name="reference"></a>Справочник  
 [Об ошибках служб Integration Services и справочник по сообщениям](../../integration-services/integration-services-error-and-message-reference.md)  
 Содержится список стандартных кодов ошибок служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] с символическими именами и описаниями.  
  
## <a name="related-sections"></a>См. также  
 [Расширение пакетов с помощью сценариев](../../integration-services/extending-packages-scripting/extending-packages-with-scripting.md)  
 Описывает способ расширения потока управления с помощью задачи «Скрипт» или потока данных с помощью компонента скрипта.  
  
 [Программное построение пакетов](../../integration-services/building-packages-programmatically/building-packages-programmatically.md)  
 Описывает создание, настройку, запуск, загрузку и сохранение пакетов служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] программным образом, а также программное выполнение других задач управления.  
  
## <a name="see-also"></a>См. также:  
 [Сравнение решений со сценариями и пользовательских объектов](../../integration-services/extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md)   
 [SQL Server Integration Services](../../integration-services/sql-server-integration-services.md)  
  
  
