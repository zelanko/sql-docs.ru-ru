---
title: Передача аргументов метода веб-службы | Документы Майкрософт
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server-web-service
ms.suite: pro-bi
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- Report Server Web service, methods
- Web service [Reporting Services], methods
- methods [Reporting Services], arguments
- XML Web service [Reporting Services], methods
ms.assetid: f7b9ca05-fc4c-4b30-8e5d-172dd0f4a832
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 9177fa55532cb7c464679f43bab5ae63d5254c96
ms.sourcegitcommit: d96b94c60d88340224371926f283200496a5ca64
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/30/2018
ms.locfileid: "43270336"
---
# <a name="supplying-web-service-method-arguments"></a>Передача аргументов методу веб-службы
  Метод веб-службы сервера отчетов отправляет запрос в службу по заданному URL-адресу с помощью протокола SOAP по протоколу HTTP. Служба получает запрос, обрабатывает его, а затем возвращает ответное сообщение. Такие запросы и ответы на них имеют форму XML-документов.  
  
## <a name="optional-parameters"></a>Необязательные параметры  
 В некоторых случаях метод веб-службы может иметь необязательные входные параметры. Даже если входной параметр метода веб-службы является необязательным, его все равно нужно указать и установить для него значение **NULL** (**Nothing** в [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]). Если для параметра задать значение **NULL**, то элемент для этого параметра в SOAP-запросе также будет иметь значение **NULL**.  
  
 В следующем примере используется метод <xref:ReportService2010.ReportingService2010.CreateFolder%2A>, чтобы создать новую папку с именем Product Sales в папке Sales. Если для свойств папки задать значение **NULL**, то для папки не передаются пользовательские свойства:  
  
```  
// C#  
rs.CreateFolder("Product Sales", "/Sales", null);  
```  
  
## <a name="complex-data-types"></a>Сложные типы данных  
 Основным классом веб-службы сервера отчетов является <xref:ReportService2010.ReportingService2010>, который используется для вызова операций SOAP или веб-методов класса-посредника. Чтобы обеспечить поддержку этого класса и его методов, службы [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] включают определяемые пользователем сложные типы данных, относящиеся к входным и выходным параметрам методов веб-службы. Эти сложные типы данных являются частью создаваемого прокси-класса, который используется при разработке в среде [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].  
  
 Во время создания класса-посредника сложные типы данных, определенные в WSDL-файле, представляются классами-посредниками, которые включают свойства, соответствующие различным элементам SOAP в сложных типах данных. Последовательности таких типов данных становятся массивами объектов, которые можно перечислять в коде. Это устраняет необходимость непосредственной работы с XML-структурами, отправляемыми в сообщениях SOAP. Платформа [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] выполняет необходимые преобразования.  
  
## <a name="see-also"></a>См. также:  
 [Создание приложений с помощью веб-службы и .NET Framework](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [Веб-служба сервера отчетов](../../../reporting-services/report-server-web-service/report-server-web-service.md)   
 [Технический справочник (службы SSRS)](../../../reporting-services/technical-reference-ssrs.md)  
  
  
