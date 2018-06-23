---
title: Редактор назначения обработки измерений (страница «Диспетчер соединений») | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.dimprocessingtransformation.connection.f1
helpviewer_keywords:
- Dimension Processing Destination Editor
ms.assetid: 44aab631-d62d-4895-8fc7-7f1f3b1b68ce
caps.latest.revision: 28
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 360810664d34244b95a6a36b20bc5c0a7098bfd3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36086928"
---
# <a name="dimension-processing-destination-editor-connection-manager-page"></a>Редактор назначения обработки измерений (страница «Диспетчер соединений»)
  Страница **Диспетчер соединений** в диалоговом окне **Редактор назначения обработки измерений** позволяет указать соединение с проектом служб [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] или с экземпляром служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
 Дополнительные сведения о назначении обработки измерений см. в разделе [Dimension Processing Destination](data-flow/dimension-processing-destination.md).  
  
## <a name="options"></a>Параметры  
 **Connection manager**  
 Выберите из списка существующий диспетчер соединений или нажмите кнопку **Создать** , чтобы создать диспетчер соединений.  
  
 **Создать**  
 Создайте новое соединение, воспользовавшись диалоговым окном **Добавление диспетчера соединений со службами Analysis Services** .  
  
 **Список доступных измерений**  
 Выберите измерение для обработки.  
  
 **Метод обработки**  
 Выберите метод обработки, применяемый к выбранному в списке измерению. Значение этого параметра по умолчанию — **Полная**.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**Добавление (дополнительное)**|Выполнить добавочную обработку измерения.|  
|**Полная**|Выполнить полную обработку измерения.|  
|**Update**|Выполнить обновление обработки измерения.|  
  
## <a name="see-also"></a>См. также  
 [Об ошибках служб Integration Services и справочник по сообщениям](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Редактор назначения обработки измерений &#40;страница «сопоставления»&#41;](../../2014/integration-services/dimension-processing-destination-editor-mappings-page.md)   
 [Редактор назначения обработки измерений &#40;страница «Дополнительно»&#41;](../../2014/integration-services/dimension-processing-destination-editor-advanced-page.md)  
  
  