---
title: Расширение пакетов с помощью скриптов | Документы Майкрософт
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
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
ms.openlocfilehash: bb567bffe0c184907ca61bd583eb5666948a0f03
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "78176188"
---
# <a name="extending-packages-with-scripting"></a>Расширение пакетов с помощью сценариев
  Если встроенные компоненты служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] не соответствуют требованиям, их можно расширить, создав собственные программные расширения служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Существует два варианта расширения пакетов: можно написать код с использованием возможностей многофункциональных оболочек, предоставляемых задачей «Скрипт» и компонентом скрипта или самостоятельно создать пользовательские расширения служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], используя классы, производные от базовых классов, предоставляемых объектной моделью служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].

 В этом разделе рассматривается самый простой способ — расширение пакетов с помощью скриптов.

 С помощью задачи «Скрипт» и компонента скрипта можно, написав минимум кода, расширить как поток управления, так и поток данных пакета служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Оба объекта используют среду разработки набора средств [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools для работы с приложениями (VSTA) и язык программирования [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic или [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual С#, а также все возможности, предоставляемые библиотекой классов платформы [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] и настраиваемыми сборками. Задача «Скрипт» и компонент скрипта дают разработчику возможность создавать пользовательскую функциональность без написания всего инфраструктурного кода для пользовательской задачи или пользовательского компонента потока данных.

## <a name="in-this-section"></a>в этом разделе
 [Сравнение задачи «Скрипт» и компонента «Скрипт»](../extending-packages-scripting/comparing-the-script-task-and-the-script-component.md) Обсуждаются сходства и различия между задачей «Скрипт» и компонентом скрипта.

 [Сравнение решений со скриптами и пользовательских объектов](comparing-scripting-solutions-and-custom-objects.md) Описывает критерии, используемые при выборе между решением сценариев и разработкой пользовательского объекта.

 [Создание ссылок на другие сборки в решениях сценариев](referencing-other-assemblies-in-scripting-solutions.md) Описывает шаги, необходимые для ссылки и использования внешних сборок и пространств имен в проекте скриптов.

 [Расширение пакета с помощью задачи «Скрипт»](../extending-packages-scripting/task/extending-the-package-with-the-script-task.md) Описывает создание пользовательских задач с помощью задачи «Скрипт». Обычно задача вызывается один раз за время выполнения пакета или один раз для каждого источника данных, открытого пакетом.

 [Расширение потока данных с помощью компонента скрипта](data-flow-script-component/extending-the-data-flow-with-the-script-component.md) Описывает, как создавать пользовательские источники потока данных, преобразования и назначения с помощью компонента скрипта. Компонент потока данных обычно вызывается один раз для каждой обрабатываемой строки данных.

## <a name="reference"></a>Справочник
 [Справочник по ошибкам и сообщениям Integration Services](../integration-services-error-and-message-reference.md) Список стандартных [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] кодов ошибок со своими символическими именами и описаниями.

## <a name="related-sections"></a>Связанные разделы
 [Расширение пакетов с помощью пользовательских объектов](../extending-packages-custom-objects/extending-packages-with-custom-objects.md) Описывает создание пользовательских задач, компонентов потока данных и других объектов пакета для использования в нескольких пакетах.

 [Программное создание пакетов](../building-packages-programmatically/building-packages-programmatically.md) Описывает, как создавать, настраивать, запускать, загружать, сохранять пакеты и управлять [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ими программно.

![Значок Integration Services (маленький)](../media/dts-16.gif "Значок служб Integration Services (маленький)")  **следит за обновлениями Integration Services**<br /> Чтобы загрузить новейшую документацию, статьи, образцы и видеоматериалы [!INCLUDE[msCoName](../../includes/msconame-md.md)], а также лучшие решения участников сообщества, посетите страницу служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] на сайте MSDN:<br /><br /> [Посетить страницу «Службы Integration Services» на сайте MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Чтобы получать автоматические уведомления об этих обновлениях, подпишитесь на RSS-каналы, предлагаемые на этой странице.

## <a name="see-also"></a>См. также:
 [SQL Server Integration Services](../sql-server-integration-services.md)


