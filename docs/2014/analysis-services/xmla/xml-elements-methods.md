---
title: Методы (XMLA) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
- apinav
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#
helpviewer_keywords:
- methods [XML for Analysis]
- XML for Analysis, methods
- XMLA, methods
ms.assetid: c6768dd4-ca06-4a85-93b7-5fd5700886ad
caps.latest.revision: 30
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1baf254e9965153394a3a7b1367ced21c009a7f4
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37171425"
---
# <a name="methods-xmla"></a>Методы (XML для аналитики)
  Протокол XML для аналитики (XMLA) с помощью двух методов `Discover` и `Execute`, которые предлагают стандартный способ для приложений для доступа к информации в экземпляре [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Поскольку эти методы вызываются при помощи протокола SOAP, они получают входные данные и предоставляют результаты в формате XML. В службах [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] реализованы оба метода в соответствии со спецификацией XML для аналитики 1.1.  
  
## <a name="in-this-section"></a>в этом разделе  
 В следующих разделах описываются методы XML для аналитики, реализованные в службах [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
|Метод|Описание|  
|------------|-----------------|  
|[Метод Discover &#40;XML для Аналитики&#41;](xml-elements-methods-discover.md)|Получает сведения, такие как список доступных баз данных или подробные сведения о конкретном объекте, из экземпляра служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Данные, полученные с помощью метода `Discover`, зависят от значений параметров, переданных этому методу.|  
|[Метод Execute &#40;XML для Аналитики&#41;](xml-elements-methods-execute.md)|Отправляет команды XMLA на экземпляр служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Сюда входят запросы, связанные с передачей данных, например извлечение или обновление данных на сервере.|  
  
## <a name="see-also"></a>См. также  
 [XML-элементов &#40;XML для Аналитики&#41;](../dev-guide/xml-elements-xmla.md)   
 [Типы данных XML &#40;XML для Аналитики&#41;](xml-data-types/xml-data-types-xmla.md)   
 [XML-элементов &#40;XML для Аналитики&#41;](../dev-guide/xml-elements-xmla.md)  
  
  
