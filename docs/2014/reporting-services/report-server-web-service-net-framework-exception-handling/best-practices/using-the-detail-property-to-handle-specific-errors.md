---
title: Использование свойства Detail для обработки определенных ошибок | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- exceptions [Reporting Services], Detail property
- Detail property
- InnerText property
ms.assetid: 4392633d-b46b-41e6-bc12-efb64e166704
caps.latest.revision: 29
author: douglaslM
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 08f109483a1b9aa39046316920ac84dbd8022438
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36189684"
---
# <a name="using-the-detail-property-to-handle-specific-errors"></a>Использование свойства Detail для обработки определенных ошибок
  В ходе дальнейшей классификации исключений службы [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] возвращают дополнительные сведения об ошибках в свойстве **InnerText** дочерних элементов свойства **Detail** исключения SOAP. Так как свойство **Detail** является объектом **XmlNode**, с помощью приведенного ниже кода можно обращаться к внутреннему тексту дочернего элемента **Message**.  
  
 Список всех доступных дочерних элементов в свойстве **Detail** см. в разделе [Свойство Detail](../soapexception-class/detail-property.md). Дополнительные сведения см. в разделе "Свойство Detail" в документации по пакету SDK [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].  
  
```vb  
Try  
' Code for accessing the report server  
Catch ex As SoapException  
   ' The exception is a SOAP exception, so use  
   ' the Detail property's Message element.  
   Console.WriteLine(ex.Detail("Message").InnerXml)  
End Try  
```  
  
```csharp  
try  
{  
   // Code for accessing the report server  
}  
catch (SoapException ex)  
{  
   // The exception is a SOAP exception, so use  
   // the Detail property's Message element.  
   Console.WriteLine(ex.Detail["Message"].InnerXml);  
}  
```  
  
```vb  
Try  
' Code for accessing the report server  
Catch ex As SoapException  
   If ex.Detail("ErrorCode").InnerXml = "rsInvalidItemName" Then  
   End If ' Perform an action based on the specific error code  
End Try  
```  
  
```csharp  
try  
{  
   // Code for accessing the report server  
}  
catch (SoapException ex)  
{  
   if (ex.Detail["ErrorCode"].InnerXml == "rsInvalidItemName")  
   {  
      // Perform an action based on the specific error code  
   }  
}  
```  
  
 Приведенная ниже строка кода выводит на консоль конкретный код ошибки, возвращенный в исключении SOAP. Можно также вычислить код ошибки и выполнить соответствующие действия.  
  
```vb  
Console.WriteLine(ex.Detail("ErrorCode").InnerXml)  
```  
  
```csharp  
Console.WriteLine(ex.Detail["ErrorCode"].InnerXml);  
```  
  
## <a name="see-also"></a>См. также  
 [Введение в обработку исключений в службах Reporting Services](../introducing-exception-handling-in-reporting-services.md)   
 [Класс SoapException в службах Reporting Services](../soapexception-class/reporting-services-soapexception-class.md)   
 [Таблица ошибок SoapException](../soapexception-class/soapexception-errors-table.md)  
  
  