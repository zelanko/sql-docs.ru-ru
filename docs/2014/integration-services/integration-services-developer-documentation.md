---
title: Разработчик&#39;руководство (службы Integration Services) | Документация Майкрософт
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Integration Services, programming
- SSIS, programming
- SQL Server Integration Services, programming
- packages [Integration Services], programming
ms.assetid: 60fe148b-a7c4-4289-ae3e-2e949fc1886c
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 6e18e1d1e2219dd33fe6eea241d50ff6b077fe62
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/13/2018
ms.locfileid: "53361406"
---
# <a name="developer39s-guide-integration-services"></a>Разработчик&#39;руководство (службы Integration Services)
  Службы [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] включают полностью переписанную модель объектов, которая была улучшена многими функциями, позволяющими упростить расширение и программирование пакетов и сделать их более гибкими и более мощными. Разработчики могут расширять и программировать пакеты служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] почти в любом аспекте.  
  
 Разработчик служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] может воспользоваться двумя фундаментальными подходами при программировании служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].  
  
-   Можно расширять пакеты путем создания компонентов, которые становятся доступными в конструкторе служб [!INCLUDE[ssIS](../includes/ssis-md.md)], чтобы предоставить пользовательскую функциональность в пакете.  
  
-   Можно создавать, настраивать и выполнять пакеты программным путем из собственных приложений.  
  
 Если обнаруживается, что встроенные компоненты в службах [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] не соответствуют конкретным требованиям, можно расширить возможности служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], разработав собственные модули. Этот подход подразделяется на два отдельных способа.  
  
-   Для нерегламентированного использования в одном пакете можно создать пользовательскую задачу, написав код в задаче «Скрипт», или разработать пользовательский компонент потока данных, написав код в компоненте скрипта, который можно настроить как источник, преобразование или назначение. Эти мощные оболочки сами создают инфраструктурный код для разработчика и позволяют ему сосредоточиться исключительно на создании пользовательской функциональности. Однако при этом сложно создать повторно используемый код.  
  
-   Для использования в нескольких пакетах можно создать пользовательские модули служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], такие как диспетчеры соединений, задачи, перечислители, регистраторы и компоненты потока данных. Управляемая модель объектов служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] содержит базовые классы, которые предоставляют исходную точку и позволяют разрабатывать пользовательские модули проще, чем когда-либо.  
  
 Если требуется создавать пакеты динамически или управлять и запускать пакеты служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] за пределами среды разработки, можно воспользоваться возможностью управлять пакетами программным путем. Можно загружать, изменять и запускать существующие пакеты или создавать и запускать полностью новые пакеты программным путем. Этот подход предлагает следующий набор вариантов.  
  
-   Загрузка и выполнение существующего пакета без изменения.  
  
-   Загрузка существующего пакета, изменение его конфигурации (например, указание другого источника данных) и выполнение пакета.  
  
-   Создание нового пакета, добавление и настройка компонентов, изменение одного объекта за другим и одного свойства за другим, сохранение пакета, а затем выполнение.  
  
 Эти подходы к программированию служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] описаны в этом разделе и демонстрируются на примерах.  
  
## <a name="in-this-section"></a>в этом разделе  
 [Общие сведения о программировании служб Integration Services](integration-services-programming-overview.md)  
 Описывает роли потока управления и потока данных в разработке служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].  
  
 [Основные сведения о синхронных и асинхронных преобразованиях](understanding-synchronous-and-asynchronous-transformations.md)  
 Описывает важное различие между синхронными и асинхронными выходами, а также описывает компоненты, в которых используются эти выходы в потоке данных.  
  
 [Работа с диспетчерами соединений программным образом](working-with-connection-managers-programmatically.md)  
 Описывает диспетчеры соединений, которые можно использовать из управляемого кода, а также значения, возвращаемые диспетчерами при вызове метода `AcquireConnection` из кода.  
  
 [Расширение пакетов с помощью сценариев](extending-packages-scripting/extending-packages-with-scripting.md)  
 Показывает, как расширить поток управления с помощью задачи «Скрипт» или поток данных с помощью компонента скрипта.  
  
 [Расширение пакетов с помощью пользовательских объектов](extending-packages-custom-objects/extending-packages-with-custom-objects.md)  
 Показывает, как создавать и программировать пользовательские задачи, компоненты потока данных и другие объекты пакета для применения в нескольких пакетах.  
  
 [Программное построение пакетов](building-packages-programmatically/building-packages-programmatically.md)  
 Показывает, как создавать, настраивать и сохранять пакеты служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] программным путем.  
  
 [Выполнение пакетов и управление пакетами программным образом](run-manage-packages-programmatically/running-and-managing-packages-programmatically.md)  
 Показывает, как перечислять, запускать пакеты служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] и управлять ими программным путем.  
  
## <a name="reference"></a>Ссылка  
 [Справочник по сообщениям об ошибках служб Integration Services](integration-services-error-and-message-reference.md)  
 Содержит список стандартных кодов ошибок служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] с символическими именами и описаниями.  
  
## <a name="related-sections"></a>См. также  
 [Инструменты устранения неполадок при разработке пакета](troubleshooting/troubleshooting-tools-for-package-development.md)  
 Описывает возможности и инструментальные средства служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], предназначенные для устранения неполадок в пакетах в процессе разработки.  
  
## <a name="external-resources"></a>Внешние ресурсы  
  
-   Образцы CodePlex, [Образцы продуктов служб Integration Services](https://go.microsoft.com/fwlink/?LinkID=131204)на сайте www.codeplex.com/MSFTISProdSamples  
  
## <a name="see-also"></a>См. также  
 [службы SQL Server Integration Services](sql-server-integration-services.md)  
  
  
