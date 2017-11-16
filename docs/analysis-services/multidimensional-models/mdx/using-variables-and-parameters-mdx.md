---
title: "Переменные и параметры (многомерные Выражения) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parameters [MDX]
- queries [MDX], variables
- queries [MDX], parameters
- variables [MDX]
ms.assetid: a4754d16-d9c4-49f6-9be0-392180b912e4
caps.latest.revision: 29
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 5ac634400b85e49cdaf9f57e683cc13fe781ed2b
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="using-variables-and-parameters-mdx"></a>Переменные и параметры (многомерные выражения)
  Службы [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]позволяют задавать параметры для инструкций многомерных выражений. Благодаря параметризации можно создавать универсальные инструкции, настраиваемые во время выполнения.  
  
 Имена параметров при создании параметризованных инструкций обозначаются префиксом «@». Например @Year будет допустимое имя параметра  
  
 В языке многомерных выражений поддерживаются только параметры для строковых и скалярных значений. Чтобы создать параметр, который ссылается на элемент, набор или кортеж, необходимо использовать функцию, например [StrToMember](../../../mdx/strtomember-mdx.md) или [StrToSet](../../../mdx/strtoset-mdx.md).  
  
 В следующем XML для аналитики (XMLA) примера @CountryName содержит страну, для какого клиента извлекаются данные параметра:  
  
```  
<Envelope xmlns="http://schemas.xmlsoap.org/soap/envelope/">  
  <Body>  
    <Execute xmlns="urn:schemas-microsoft-com:xml-analysis">  
      <Command>  
        <Statement>  
select [Measures].members on 0,   
       Filter(Customer.[Customer Geography].Country.members,   
              Customer.[Customer Geography].CurrentMember.Name =  
              @CountryName) on 1  
from [Adventure Works]  
</Statement>  
      </Command>  
      <Properties />  
      <Parameters>  
        <Parameter>  
          <Name>CountryName</Name>  
          <Value>'United Kingdom'</Value>  
        </Parameter>  
      </Parameters>  
    </Execute>  
  </Body>  
</Envelope>  
```  
  
 В OLE DB эти возможности доступны через интерфейс **ICommandWithParameters** . В ADOMD.Net для этого необходимо использовать коллекцию **AdomdCommand.Parameters** .  
  
## <a name="see-also"></a>См. также  
 [Основные принципы создания скриптов многомерных выражений (службы Analysis Services)](../../../analysis-services/multidimensional-models/mdx/mdx-scripting-fundamentals-analysis-services.md)  
  
  

