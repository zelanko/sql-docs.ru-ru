---
title: Переменные и параметры (многомерные Выражения) | Документы Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: mdx
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 039668b719a2c6c715139682496117b8239425aa
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="using-variables-and-parameters-mdx"></a>Переменные и параметры (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Службы [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] позволяют задавать параметры для инструкций многомерных выражений. Благодаря параметризации можно создавать универсальные инструкции, настраиваемые во время выполнения.  
  
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
 [Основные понятия о сценариях многомерных Выражений & #40; Службы Analysis Services & #41;](../../../analysis-services/multidimensional-models/mdx/mdx-scripting-fundamentals-analysis-services.md)  
  
  
