---
title: Методы (XMLA) | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f42c986f8ebb3be2126335663a0716049e908ab0
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="xml-elements---methods"></a>Элементы XML - методы
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Протокол XML для аналитики (XMLA) используется два метода, **Discover** и **Execute**, которые предлагают стандартный способ для приложений для доступа к данным в экземпляре [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Поскольку эти методы вызываются при помощи протокола SOAP, они получают входные данные и предоставляют результаты в формате XML. В службах [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] реализованы оба метода в соответствии со спецификацией XML для аналитики 1.1.  
  
## <a name="in-this-section"></a>В этом разделе  
 В следующих разделах описываются методы XML для аналитики, реализованные в службах [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
|Метод|Описание|  
|------------|-----------------|  
|[Метод Discover &#40;XML для Аналитики&#41;](../../analysis-services/xmla/xml-elements-methods-discover.md)|Получает сведения, такие как список доступных баз данных или подробные сведения о конкретном объекте, из экземпляра служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Данные, полученные с помощью метода **Discover** , зависят от значений параметров, переданных этому методу.|  
|[Метод Execute &#40;XML для Аналитики&#41;](../../analysis-services/xmla/xml-elements-methods-execute.md)|Отправляет команды XMLA на экземпляр служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Сюда входят запросы, связанные с передачей данных, например извлечение или обновление данных на сервере.|  
  
## <a name="see-also"></a>См. также  
 [XML-элементы & #40; XML для Аналитики & #41;](http://msdn.microsoft.com/library/40ab2360-efb6-4ba6-bf23-e84964e51008)   
 [Типы данных XML & #40; XML для Аналитики & #41;](../../analysis-services/xmla/xml-data-types/xml-data-types-xmla.md)   
 [XML-элементы & #40; XML для Аналитики & #41;](http://msdn.microsoft.com/library/40ab2360-efb6-4ba6-bf23-e84964e51008)  
  
  
