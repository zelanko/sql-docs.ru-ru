---
title: Разработка компонентов потока данных определенных типов | Документы Майкрософт
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
- data flow task [Integration Services], components
- components [Integration Services], data flow
- data flow [Integration Services], components
ms.assetid: 348e219a-b8ff-425e-b9c6-811880101c54
author: janinezhang
ms.author: janinez
ms.openlocfilehash: bfca6453c68ecafcc4d0b375965f7f35c0cc84df
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84968886"
---
# <a name="developing-specific-types-of-data-flow-components"></a>Разработка компонентов потока данных определенных типов
  Этот раздел описывает специфические особенности разработки компонентов источника, компонентов преобразования с синхронными выходами компонентов преобразования с асинхронными выходами и компоненты назначения.  
  
 Общие сведения о разработке компонентов см. в разделе [Разработка пользовательского компонента потока данных](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md).  
  
## <a name="in-this-section"></a>в этом разделе  
 [Разработка пользовательского компонента источника](../extending-packages-custom-objects-data-flow-types/developing-a-custom-source-component.md)  
 Содержит сведения о разработке компонента, осуществляющего доступ к данным внешнего источника данных и поставляющего их компонентам, расположенным ниже в потоке данных.  
  
 [Разработка пользовательского компонента преобразования с синхронными выходами](../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-synchronous-outputs.md)  
 Содержит сведения о разработке компонента преобразования, выходы которого синхронизированы с входами. Эти компоненты не добавляют данные в поток данных, но обрабатывают проходящие через них данные.  
  
 [Разработка пользовательского компонента преобразования с асинхронными выходами](../extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-asynchronous-outputs.md)  
 Содержит сведения о разработке компонента преобразования, выходы которого не синхронизированы с входами. Эти компоненты получают данные от вышестоящих компонентов, а также добавляют данные в поток.  
  
 [Разработка пользовательского компонента назначения](../extending-packages-custom-objects-data-flow-types/developing-a-custom-destination-component.md)  
 Содержит сведения о разработке компонента, получающего строки от вышестоящих компонентов в потоке данных и записывающего их во внешний источник данных.  
  
## <a name="reference"></a>Справочник  
 <xref:Microsoft.SqlServer.Dts.Pipeline>  
 Содержит классы и интерфейсы, используемые для создания пользовательских компонентов потока данных.  
  
 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper>  
 Содержит неуправляемые классы и интерфейсы задачи потока данных. Разработчик использует их и управляемое пространство имен <xref:Microsoft.SqlServer.Dts.Pipeline> при программном построении потока данных или создании пользовательских компонентов потока данных.  
  
![Значок Integration Services (маленький)](../media/dts-16.gif "Значок служб Integration Services (маленький)")  **следит за обновлениями Integration Services**<br /> Чтобы загрузить новейшую документацию, статьи, образцы и видеоматериалы корпорации Майкрософт, а также лучшие решения участников сообщества, посетите страницу служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] на сайте MSDN:<br /><br /> [Посетить страницу «Службы Integration Services» на сайте MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Чтобы получать автоматические уведомления об этих обновлениях, подпишитесь на RSS-каналы, предлагаемые на этой странице.  
  
## <a name="see-also"></a>См. также:  
 [Сравнение решений со скриптами и пользовательских объектов](../extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md)   
 [Разработка компонентов скрипта определенных типов](../extending-packages-scripting-data-flow-script-component-types/developing-specific-types-of-script-components.md)  
  
  
