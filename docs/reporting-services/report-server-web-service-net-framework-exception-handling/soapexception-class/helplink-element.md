---
title: Элемент HelpLink | Документы Майкрософт
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server-web-service-net-framework-exception-handling
ms.topic: reference
helpviewer_keywords:
- HelpLink element
- SoapException class
ms.assetid: a4489103-a874-44c2-8f75-95cb238928ed
author: markingmyname
ms.author: maghan
ms.openlocfilehash: b11acfb91190aa4f6d1b49e603954c53bbcd86e5
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47737682"
---
# <a name="helplink-element"></a>Элемент HelpLink
  Элемент **HelpLink** свойства **Detail** представляет строку с URL-адресом, которая создается сервером отчетов. Этот URL-адрес ссылается на веб-страницу, управляемую центром справки и поддержки [!INCLUDE[msCoName](../../../includes/msconame-md.md)], которая предоставляет дополнительную справку и статьи базы значений, посвященные ошибкам, происходящим в службах [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]. URL-адрес имеет следующий синтаксис:  
  
 **http://** www.microsoft.com**/** products**/** ee**/** transform.aspx **?EvtSrc**=v*alue***&EvtID**=* value ***&ProdName**=* value***&ProdVer**=* value*  
  
 В следующей таблице перечислены аргументы URL-адреса **HelpLink**.  
  
|Аргумент|Значение|  
|--------------|-----------|  
|**EvtSrc**|Microsoft.ReportingServices.Diagnostics.ErrorStrings.resources.Strings.|  
|**EvtID**|Код ошибки сервера отчетов, например rsReservedItem.|  
|**ProdName**|«Microsoft SQL%20Server%20Reporting%20Services». Значение названия продукта кодируется по правилам URL-адресов.|  
|**ProdVer**|Номер версии служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]. Значение "8.00" соответствует службам [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].|  
  
 В следующем примере показан URL-адрес **HelpLink**, который возвращается для кода ошибки **rsReservedItem**. Эта ошибка происходит, когда пользователь выполняет попытку изменить или удалить зарезервированный элемент в службах [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]:  
  
```  
http://www.microsoft.com/products/ee/transform.aspx?  
EvtSrc=Microsoft.ReportingServices.Diagnostics.ErrorStrings.resources.Strings  
&EvtID=rsReservedItem&ProdName=Microsoft%20SQL%20Server%20Reporting%20Services&ProdVer=8.00  
```  
  
 Доступ к элементу **HelpLink** можно получить из программного кода с помощью класса **SoapException**.  
  
```vb  
Try  
   rs.DeleteItem("/Report1")  
  
Catch e As SoapException  
   Console.WriteLine(e.Detail("HelpLink").InnerXml)  
End Try  
```  
  
```csharp  
try  
{  
   rs.DeleteItem("/Report1");  
}  
  
catch (SoapException e)  
{  
   Console.WriteLine(e.Detail["HelpLink"].InnerXml);  
}  
```  
  
## <a name="see-also"></a>См. также:  
 [Введение в обработку исключений в службах Reporting Services](../../../reporting-services/report-server-web-service-net-framework-exception-handling/introducing-exception-handling-in-reporting-services.md)   
 [Класс SoapException в службах Reporting Services](../../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/reporting-services-soapexception-class.md)   
 [Использование свойства Detail для обработки определенных ошибок](../../../reporting-services/report-server-web-service-net-framework-exception-handling/best-practices/using-the-detail-property-to-handle-specific-errors.md)  
  
  
