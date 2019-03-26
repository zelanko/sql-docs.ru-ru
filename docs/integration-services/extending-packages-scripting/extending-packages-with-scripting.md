---
title: Расширение пакетов с помощью скриптов | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- SQL Server Integration Services, scripting
- SSIS, scripting
- scripts [Integration Services], about scripting
ms.assetid: 67fe18ef-f3aa-41d4-9b9d-5defd4618c4b
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 8d2825a7822f4500f8905810262567be95de68f3
ms.sourcegitcommit: 7ccb8f28eafd79a1bddd523f71fe8b61c7634349
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2019
ms.locfileid: "58289000"
---
# <a name="extending-packages-with-scripting"></a>Расширение пакетов с помощью сценариев
  Если встроенные компоненты служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] не соответствуют требованиям, их можно расширить, создав собственные программные расширения служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Существует два варианта расширения пакетов: можно написать код с использованием возможностей многофункциональных оболочек, предоставляемых задачей «Скрипт» и компонентом скрипта или самостоятельно создать пользовательские расширения служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], используя классы, производные от базовых классов, предоставляемых объектной моделью служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 В этом разделе рассматривается самый простой способ — расширение пакетов с помощью скриптов.  
  
 С помощью задачи «Скрипт» и компонента скрипта можно, написав минимум кода, расширить как поток управления, так и поток данных пакета служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Оба объекта используют среду разработки набора средств [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools для работы с приложениями (VSTA) и язык программирования [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic или [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual С#, а также все возможности, предоставляемые библиотекой классов платформы [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] и настраиваемыми сборками. Задача «Скрипт» и компонент скрипта дают разработчику возможность создавать пользовательскую функциональность без написания всего инфраструктурного кода для пользовательской задачи или пользовательского компонента потока данных.  
  
## <a name="in-this-section"></a>в этом разделе  
 [Сравнение задачи «Скрипт» и компонента скрипта](../../integration-services/extending-packages-scripting/comparing-the-script-task-and-the-script-component.md)  
 Рассматриваются сходства и различия задачи «Скрипт» и компонента скрипта.  
  
 [Сравнение решений со сценариями и пользовательских объектов](../../integration-services/extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md)  
 Рассматриваются критерии, которые должны использоваться при выборе между решением с написанием скрипта и разработкой пользовательского объекта.  
  
 [Ссылки на другие сборки в решениях со сценариями](../../integration-services/extending-packages-scripting/referencing-other-assemblies-in-scripting-solutions.md)  
 Рассматриваются шаги, необходимые для ссылки на внешние сборки и пространства имен и использования их в проекте скрипта.  
  
 [Расширение пакета с помощью задачи «Скрипт»](../../integration-services/extending-packages-scripting/task/extending-the-package-with-the-script-task.md)  
 Рассматривается создание пользовательских задач с помощью задачи «Скрипт». Обычно задача вызывается один раз за время выполнения пакета или один раз для каждого источника данных, открытого пакетом.  
  
 [Расширение потока данных с помощью компонента скрипта](../../integration-services/extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md)  
 Рассматривается создание пользовательских источников потоков данных, преобразований и назначений с использованием компонента скрипта. Компонент потока данных обычно вызывается один раз для каждой обрабатываемой строки данных.  
  
## <a name="reference"></a>Справочник  
 [Справочник по сообщениям об ошибках служб Integration Services](../../integration-services/integration-services-error-and-message-reference.md)  
 Содержится список стандартных кодов ошибок служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] с символическими именами и описаниями.  
  
## <a name="related-sections"></a>См. также  
 [Расширение пакетов с помощью пользовательских объектов](../../integration-services/extending-packages-custom-objects/extending-packages-with-custom-objects.md)  
 Описываются вопросы программирования пользовательских задач, компонентов потока данных и других объектов пакета, используемых в нескольких пакетах.  
  
 [Программное построение пакетов](../../integration-services/building-packages-programmatically/building-packages-programmatically.md)  
 Описывает создание, настройку, запуск, загрузку и сохранение пакетов служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] программным образом, а также программное выполнение других задач управления.  
  
## <a name="see-also"></a>См. также:  
 [службы SQL Server Integration Services](../../integration-services/sql-server-integration-services.md)  
  
  
