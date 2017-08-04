---
title: "Редактор назначения обработки измерений (страница «Диспетчер соединений») | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.dimprocessingtransformation.connection.f1
helpviewer_keywords:
- Dimension Processing Destination Editor
ms.assetid: 44aab631-d62d-4895-8fc7-7f1f3b1b68ce
caps.latest.revision: 29
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 3e7ca96a91f35b88ea344fa2ad63f61f52fc95e7
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="dimension-processing-destination-editor-connection-manager-page"></a>Редактор назначения обработки измерений (страница «Диспетчер соединений»)
  Страница **Диспетчер соединений** в диалоговом окне **Редактор назначения обработки измерений** позволяет указать соединение с проектом служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] или с экземпляром служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
 Дополнительные сведения о назначении обработки измерений см. в разделе [Dimension Processing Destination](../../integration-services/data-flow/dimension-processing-destination.md).  
  
## <a name="options"></a>Параметры  
 **Connection manager**  
 Выберите из списка существующий диспетчер соединений или нажмите кнопку **Создать** , чтобы создать диспетчер соединений.  
  
 **Создать**  
 Создайте новое соединение, воспользовавшись диалоговым окном **Добавление диспетчера соединений со службами Analysis Services** .  
  
 **Список доступных измерений**  
 Выберите измерение для обработки.  
  
 **Метод обработки**  
 Выберите метод обработки, применяемый к выбранному в списке измерению. Значение этого параметра по умолчанию — **Полная**.  
  
|Значение|Description|  
|-----------|-----------------|  
|**Добавление (дополнительное)**|Выполнить добавочную обработку измерения.|  
|**Полная**|Выполнить полную обработку измерения.|  
|**Update**|Выполнить обновление обработки измерения.|  
  
## <a name="see-also"></a>См. также  
 [Справочник по сообщениям об ошибках служб Integration Services](../../integration-services/integration-services-error-and-message-reference.md)   
 [Редактор назначения обработки измерений &#40; Страница «сопоставления» &#41;](../../integration-services/data-flow/dimension-processing-destination-editor-mappings-page.md)   
 [Редактор назначения обработки измерений &#40; Страница "Дополнительно" &#41;](../../integration-services/data-flow/dimension-processing-destination-editor-advanced-page.md)  
  
  
