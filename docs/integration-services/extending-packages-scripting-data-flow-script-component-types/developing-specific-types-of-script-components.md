---
title: "Разработка компонентов скрипта определенных типов | Документы Microsoft"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: extending-packages-scripting-data-flow-script-component-types
ms.reviewer: 
ms.suite: sql
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- Script component [Integration Services], examples
ms.assetid: dfbbe959-6b4e-4b47-b9dd-bcc31929482d
caps.latest.revision: 13
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 458ba4be689ed976a5948380d35f38020f7dd4dd
ms.contentlocale: ru-ru
ms.lasthandoff: 09/26/2017

---
# <a name="developing-specific-types-of-script-components"></a>Разработка компонентов скрипта определенных типов
  Компонент скрипта является настраиваемым средством, которое можно использовать в потоке данных пакета, чтобы выполнить практическое любое требование, которое не удается выполнить с помощью источников, преобразований и назначений, входящих в состав служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. В этом разделе содержатся образцы кода компонента скрипта, с помощью которых демонстрируются четыре варианта настройки компонента скрипта:  
  
-   В качестве источника.  
  
-   В качестве преобразования с синхронными выходами.  
  
-   В качестве преобразования с асинхронными выходами.  
  
-   В качестве назначения.  
  
 Дополнительные примеры компонента скрипта см. в разделе [Дополнительные примеры компонента скрипта](../../integration-services/extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md).  
  
## <a name="in-this-section"></a>В этом разделе  
 [Создание источника с помощью компонента скрипта](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-source-with-the-script-component.md)  
 Поясняет и демонстрирует, как создать источник потока данных с помощью компонента скрипта.  
  
 [Создание синхронного преобразования с помощью компонента скрипта](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md)  
 Поясняет и демонстрирует, как создать преобразование потока данных с синхронными выходами с помощью компонента скрипта. При подобном преобразовании строки данных изменяются на месте по мере их обработки компонентом.  
  
 [Создание асинхронного преобразования с помощью компонента скрипта](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md)  
 Поясняет и демонстрирует, как создать преобразование потока данных с асинхронными выходами с помощью компонента скрипта. При таком преобразовании необходимо считать все строки данных, прежде чем добавить к данным, обрабатываемым компонентом, дополнительные сведения, например, вычисляемое статистическое выражение.  
  
 [Создание назначения с помощью компонента скрипта](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md)  
 Поясняет и демонстрирует, как создать назначение потока данных с помощью компонента скрипта.  
  
## <a name="see-also"></a>См. также:  
 [Сравнение решений со сценариями и пользовательских объектов](../../integration-services/extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md)   
 [Компоненты потока данных разработки определенных типов](../../integration-services/extending-packages-custom-objects-data-flow-types/developing-specific-types-of-data-flow-components.md)  
  
  

