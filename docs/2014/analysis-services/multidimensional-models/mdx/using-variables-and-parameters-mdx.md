---
title: Использование переменных и параметров (многомерные выражения) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- parameters [MDX]
- queries [MDX], variables
- queries [MDX], parameters
- variables [MDX]
ms.assetid: a4754d16-d9c4-49f6-9be0-392180b912e4
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: eeb258266c489056994d8f78f80a6856602a174a
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66073713"
---
# <a name="using-variables-and-parameters-mdx"></a>Переменные и параметры (многомерные выражения)
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] В [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]можно параметризовать инструкцию многомерных выражений. Благодаря параметризации можно создавать универсальные инструкции, настраиваемые во время выполнения.  
  
 Имена параметров при создании параметризованных инструкций обозначаются префиксом «@». Например, @Year является допустимым именем параметра.  
  
 В языке многомерных выражений поддерживаются только параметры для строковых и скалярных значений. Чтобы создать параметр, который ссылается на элемент, набор или кортеж, необходимо использовать функцию, например [StrToMember](/sql/mdx/strtomember-mdx) или [StrToSet](/sql/mdx/strtoset-mdx).  
  
 В следующем примере XML для аналитики (XMLA) @CountryName параметр будет содержать страну, для которой извлекаются данные клиента:  
  
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
  
 В OLE DB эти возможности доступны через интерфейс `ICommandWithParameters`. В ADOMD.Net для этого необходимо использовать коллекцию **AdomdCommand.Parameters** .  
  
## <a name="see-also"></a>См. также  
 [Основные принципы создания скриптов многомерных выражений (службы Analysis Services)](mdx-scripting-fundamentals-analysis-services.md)  
  
  
