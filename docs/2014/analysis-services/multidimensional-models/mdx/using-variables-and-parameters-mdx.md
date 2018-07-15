---
title: Использование переменных и параметров (многомерные Выражения) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- parameters [MDX]
- queries [MDX], variables
- queries [MDX], parameters
- variables [MDX]
ms.assetid: a4754d16-d9c4-49f6-9be0-392180b912e4
caps.latest.revision: 29
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 22adb713c5a75d4cf038e5683a6ddec8adbe836d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37266110"
---
# <a name="using-variables-and-parameters-mdx"></a>Переменные и параметры (многомерные выражения)
  Службы [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]позволяют задавать параметры для инструкций многомерных выражений. Благодаря параметризации можно создавать универсальные инструкции, настраиваемые во время выполнения.  
  
 Имена параметров при создании параметризованных инструкций обозначаются префиксом «@». Например @Year бы допустимое имя параметра  
  
 В языке многомерных выражений поддерживаются только параметры для строковых и скалярных значений. Чтобы создать параметр, который ссылается на элемент, набор или кортеж, необходимо использовать функцию, например [StrToMember](/sql/mdx/strtomember-mdx) или [StrToSet](/sql/mdx/strtoset-mdx).  
  
 В следующем XML для аналитики (XMLA) примера @CountryName параметр содержит страну, для какого клиента извлекаются данные:  
  
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
  
 Чтобы использовать эту функцию с помощью OLE DB, используйте `ICommandWithParameters` интерфейс. В ADOMD.Net для этого необходимо использовать коллекцию **AdomdCommand.Parameters** .  
  
## <a name="see-also"></a>См. также  
 [Основные принципы создания скриптов многомерных Выражений &#40;служб Analysis Services&#41;](mdx-scripting-fundamentals-analysis-services.md)  
  
  
