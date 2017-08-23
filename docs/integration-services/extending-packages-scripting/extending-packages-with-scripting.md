---
title: "Расширение пакетов с помощью сценариев | Документы Microsoft"
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
helpviewer_keywords:
- SQL Server Integration Services, scripting
- SSIS, scripting
- scripts [Integration Services], about scripting
ms.assetid: 67fe18ef-f3aa-41d4-9b9d-5defd4618c4b
caps.latest.revision: 40
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 8ed9de3849d0c68af740d6256c53307f1606822a
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="extending-packages-with-scripting"></a>Расширение пакетов с помощью сценариев
  Если встроенные компоненты служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] не соответствуют требованиям, их можно расширить, создав собственные программные расширения служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Существует два варианта расширения пакетов: можно написать код с использованием возможностей многофункциональных оболочек, предоставляемых задачей «Скрипт» и компонентом скрипта или самостоятельно создать пользовательские расширения служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], используя классы, производные от базовых классов, предоставляемых объектной моделью служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 В этом разделе рассматривается самый простой способ — расширение пакетов с помощью скриптов.  
  
 С помощью задачи «Скрипт» и компонента скрипта можно, написав минимум кода, расширить как поток управления, так и поток данных пакета служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Оба объекта используют [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] средства среды разработки приложений (VSTA) и [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic или [!INCLUDE[msCoName](../../includes/msconame-md.md)] языков программирования Visual C#, а также все возможности, предоставляемые [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] библиотеки классов, а также пользовательские сборки. Задача «Скрипт» и компонент скрипта дают разработчику возможность создавать пользовательскую функциональность без написания всего инфраструктурного кода для пользовательской задачи или пользовательского компонента потока данных.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Сравнение задачи «скрипт» и компоненте скрипта](../../integration-services/extending-packages-scripting/comparing-the-script-task-and-the-script-component.md)  
 Рассматриваются сходства и различия задачи «Скрипт» и компонента скрипта.  
  
 [Сравнение решений со сценариями и пользовательских объектов](../../integration-services/extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md)  
 Рассматриваются критерии, которые должны использоваться при выборе между решением с написанием скрипта и разработкой пользовательского объекта.  
  
 [Ссылки на другие сборки в решениях со сценариями](../../integration-services/extending-packages-scripting/referencing-other-assemblies-in-scripting-solutions.md)  
 Рассматриваются шаги, необходимые для ссылки на внешние сборки и пространства имен и использования их в проекте скрипта.  
  
 [Расширение пакетов с помощью задачи «скрипт»](../../integration-services/extending-packages-scripting/task/extending-the-package-with-the-script-task.md)  
 Рассматривается создание пользовательских задач с помощью задачи «Скрипт». Обычно задача вызывается один раз за время выполнения пакета или один раз для каждого источника данных, открытого пакетом.  
  
 [Расширение потока данных с помощью компонента скрипта](../../integration-services/extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md)  
 Рассматривается создание пользовательских источников потоков данных, преобразований и назначений с использованием компонента скрипта. Компонент потока данных обычно вызывается один раз для каждой обрабатываемой строки данных.  
  
## <a name="reference"></a>Справочник  
 [Об ошибках служб Integration Services и справочник по сообщениям](../../integration-services/integration-services-error-and-message-reference.md)  
 Содержится список стандартных кодов ошибок служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] с символическими именами и описаниями.  
  
## <a name="related-sections"></a>См. также  
 [Расширение пакетов с помощью пользовательских объектов](../../integration-services/extending-packages-custom-objects/extending-packages-with-custom-objects.md)  
 Описываются вопросы программирования пользовательских задач, компонентов потока данных и других объектов пакета, используемых в нескольких пакетах.  
  
 [Программное построение пакетов](../../integration-services/building-packages-programmatically/building-packages-programmatically.md)  
 Описывает создание, настройку, запуск, загрузку и сохранение пакетов служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] программным образом, а также программное выполнение других задач управления.  
  
## <a name="see-also"></a>См. также:  
 [SQL Server Integration Services](../../integration-services/sql-server-integration-services.md)  
  
  
