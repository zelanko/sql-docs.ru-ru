---
title: Разработка компонентов потока данных определенных типов | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data flow task [Integration Services], components
- components [Integration Services], data flow
- data flow [Integration Services], components
ms.assetid: 348e219a-b8ff-425e-b9c6-811880101c54
caps.latest.revision: 41
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d1cf79980bfd6c9e0b9c66038f1748e99db1c828
ms.sourcegitcommit: de5e726db2f287bb32b7910831a0c4649ccf3c4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/12/2018
ms.locfileid: "35333048"
---
# <a name="developing-specific-types-of-data-flow-components"></a>Разработка компонентов потока данных определенных типов
  Этот раздел описывает специфические особенности разработки компонентов источника, компонентов преобразования с синхронными выходами компонентов преобразования с асинхронными выходами и компоненты назначения.  
  
 Общие сведения о разработке компонентов см. в разделе [Разработка пользовательского компонента потока данных](../../integration-services/extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md).  
  
## <a name="in-this-section"></a>в этом разделе  
 [Разработка пользовательского компонента источника](../../integration-services/extending-packages-custom-objects-data-flow-types/developing-a-custom-source-component.md)  
 Содержит сведения о разработке компонента, осуществляющего доступ к данным внешнего источника данных и поставляющего их компонентам, расположенным ниже в потоке данных.  
  
 [Разработка пользовательского компонента преобразования с синхронными выходами](../../integration-services/extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-synchronous-outputs.md)  
 Содержит сведения о разработке компонента преобразования, выходы которого синхронизированы с входами. Эти компоненты не добавляют данные в поток данных, но обрабатывают проходящие через них данные.  
  
 [Разработка пользовательского компонента преобразования с асинхронными выходами](../../integration-services/extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-asynchronous-outputs.md)  
 Содержит сведения о разработке компонента преобразования, выходы которого не синхронизированы с входами. Эти компоненты получают данные от вышестоящих компонентов, а также добавляют данные в поток.  
  
 [Разработка пользовательского компонента назначения](../../integration-services/extending-packages-custom-objects-data-flow-types/developing-a-custom-destination-component.md)  
 Содержит сведения о разработке компонента, получающего строки от вышестоящих компонентов в потоке данных и записывающего их во внешний источник данных.  
  
## <a name="reference"></a>Справочник  
 <xref:Microsoft.SqlServer.Dts.Pipeline>  
 Содержит классы и интерфейсы, используемые для создания пользовательских компонентов потока данных.  
  
 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper>  
 Содержит неуправляемые классы и интерфейсы задачи потока данных. Разработчик использует их и управляемое пространство имен <xref:Microsoft.SqlServer.Dts.Pipeline> при программном построении потока данных или создании пользовательских компонентов потока данных.  
  
## <a name="see-also"></a>См. также:  
 [Сравнение решений со скриптами и пользовательских объектов](../../integration-services/extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md)   
 [Разработка компонентов скрипта определенных типов](../../integration-services/extending-packages-scripting-data-flow-script-component-types/developing-specific-types-of-script-components.md)  
  
  
