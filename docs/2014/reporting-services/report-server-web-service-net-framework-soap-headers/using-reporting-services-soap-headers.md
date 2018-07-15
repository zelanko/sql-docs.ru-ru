---
title: Использование заголовков SOAP служб Reporting Services | Документы Майкрософт
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
- Web service [Reporting Services], SOAP
- Report Server Web service, SOAP
- SOAP headers [Reporting Services]
- SOAP [Reporting Services], headers
- XML Web service [Reporting Services], SOAP
ms.assetid: 306d2c06-a25a-40f8-8a35-13dd32e8841e
caps.latest.revision: 38
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 7a8a563b9265fa53e55c8625fd5123aa90cda23b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37303644"
---
# <a name="using-reporting-services-soap-headers"></a>Использование заголовков SOAP служб Reporting Services
  Связь с методом веб-службы по протоколу SOAP имеет стандартный формат. Данные, закодированные в XML-документе, являются частью этого формата. XML-документ состоит из корневого элемента **Envelope**, который в свою очередь состоит из обязательного элемента **Body** и дополнительного элемента **Header**. Элемент **Body** содержит данные, соответствующие сообщению. Необязательный элемент **Header** может содержать дополнительную информацию, не связанную напрямую с конкретным сообщением. Каждый дочерний элемент **Header** называется заголовком SOAP.  
  
 Несмотря на то что заголовки SOAP могут содержать данные, связанные с сообщением, они в основном содержат информацию, обрабатываемую инфраструктурой веб-сервера.  
  
 Веб-службы сервера отчетов определяют несколько классов для использования в заголовке SOAP: <xref:ReportService2005.BatchHeader>, <xref:ReportService2010.ItemNamespaceHeader>, <xref:ReportService2010.ServerInfoHeader>, <xref:ReportService2010.TrustedUserHeader> и <xref:ReportExecution2005.ExecutionHeader>.  
  
## <a name="in-this-section"></a>в этом разделе  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Методы пакетной обработки](batching-methods.md)|Описывает, как объединять в пакет несколько операций в одну транзакцию с помощью класса <xref:ReportService2005.BatchHeader>.|  
|[Определение состояния выполнения](identifying-execution-state.md)|Описывает, как управлять состоянием сеанса в службах [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] с помощью **SessionHeader**.|  
|[Определение пространства имен элементов для метода GetProperties](setting-the-item-namespace-for-the-getproperties-method.md)|Описывает, как получить свойства, основанные либо на пути, либо на идентификаторе элемента, используя метод <xref:ReportService2010.ReportingService2010.GetProperties%2A> и заголовок SOAP <xref:ReportService2010.ItemNamespaceHeader>.|  
  
## <a name="see-also"></a>См. также  
 [Создание приложений с помощью веб-службы и .NET Framework](../report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [Технический справочник (службы SSRS)](../technical-reference-ssrs.md)  
  
  
