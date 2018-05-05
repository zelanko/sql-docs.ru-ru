---
title: Элемент detach | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- Detach command
ms.assetid: adbc7920-2a4a-4842-9e6f-37006fa19ff8
caps.latest.revision: 11
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 5aed9169968a1aa5c2a8f08f1f3663a3cb70859e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="detach-element"></a>Элемент Detach
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Отсоединяет [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] базы данных в текущем экземпляре сервера.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Command>  
   <Detach>  
      <Object>...</Object>  
      <Password>...</Password>  
   </Detach>  
</Command>  
  
```  
  
## <a name="element-characteristics"></a>Характеристики элемента  
  
|Характеристика|Описание|  
|--------------------|-----------------|  
|Тип данных и длина|None|  
|Значение по умолчанию|None|  
|Количество элементов|от 0 до n: необязательный элемент, который может встречаться несколько раз.|  
  
## <a name="element-relationships"></a>Связи элемента  
  
|Связь|Элемент|  
|------------------|-------------|  
|Родительские элементы|[Command](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|Дочерние элементы|[Объект](../../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md)<br /><br /> [Пароль](../../../analysis-services/xmla/xml-elements-properties/password-element-xmla.md)|  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.AnalysisServices.Database.Detach%2A>   
 [Элемент Attach](../../../analysis-services/xmla/xml-elements-commands/attach-element.md)   
 [Присоединение и отсоединение баз данных служб Analysis Services](../../../analysis-services/multidimensional-models/attach-and-detach-analysis-services-databases.md)   
 [Перемещение базы данных служб Analysis Services](../../../analysis-services/multidimensional-models/move-an-analysis-services-database.md)   
 [Режимы ReadWriteModes базы данных](../../../analysis-services/multidimensional-models/database-readwritemodes.md)   
 [Переключение базы данных служб Analysis Services между режимами ReadOnly и ReadWrite](../../../analysis-services/multidimensional-models/switch-an-analysis-services-database-between-readonly-and-readwrite-modes.md)  
  
  
