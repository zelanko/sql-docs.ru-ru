---
title: Разработка компонентов скрипта определенных типов | Документы Майкрософт
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- Script component [Integration Services], examples
ms.assetid: dfbbe959-6b4e-4b47-b9dd-bcc31929482d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d98a0a0293114e1b701ecd90f4a7b1ab058b0aa4
ms.sourcegitcommit: e8af8cfc0bb51f62a4f0fa794c784f1aed006c71
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2019
ms.locfileid: "71296411"
---
# <a name="developing-specific-types-of-script-components"></a>Разработка компонентов скрипта определенных типов

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Компонент скрипта является настраиваемым средством, которое можно использовать в потоке данных пакета, чтобы выполнить практическое любое требование, которое не удается выполнить с помощью источников, преобразований и назначений, входящих в состав служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. В этом разделе содержатся образцы кода компонента скрипта, с помощью которых демонстрируются четыре варианта настройки компонента скрипта:  
  
-   В качестве источника.  
  
-   В качестве преобразования с синхронными выходами.  
  
-   В качестве преобразования с асинхронными выходами.  
  
-   В качестве назначения.  
  
 Дополнительные примеры компонента скрипта, см. в разделе [Дополнительные примеры компонента скрипта](../../integration-services/extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md).  
  
## <a name="in-this-section"></a>в этом разделе  
 [Создание источника с помощью компонента скрипта](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-source-with-the-script-component.md)  
 Поясняет и демонстрирует, как создать источник потока данных с помощью компонента скрипта.  
  
 [Создание синхронного преобразования с помощью компонента скрипта](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md)  
 Поясняет и демонстрирует, как создать преобразование потока данных с синхронными выходами с помощью компонента скрипта. При подобном преобразовании строки данных изменяются на месте по мере их обработки компонентом.  
  
 [Создание асинхронного преобразования с помощью компонента скрипта](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md)  
 Поясняет и демонстрирует, как создать преобразование потока данных с асинхронными выходами с помощью компонента скрипта. При таком преобразовании необходимо считать все строки данных, прежде чем добавить к данным, обрабатываемым компонентом, дополнительные сведения, например, вычисляемое статистическое выражение.  
  
 [Создание назначения с помощью компонента скрипта](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md)  
 Поясняет и демонстрирует, как создать назначение потока данных с помощью компонента скрипта.  
  
## <a name="see-also"></a>См. также:  
 [Сравнение решений со скриптами и пользовательских объектов](../../integration-services/extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md)   
 [Разработка компонентов потока данных определенных типов](../../integration-services/extending-packages-custom-objects-data-flow-types/developing-specific-types-of-data-flow-components.md)  
  
  
