---
title: Конечные точки веб-службы сервера отчетов | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.topic: reference
helpviewer_keywords:
- management endpoints [Reporting Services]
- Web service [Reporting Services], endpoints
- endpoints [Reporting Services]
- execution endpoints [Reporting Services]
- Report Server Web service, endpoints
ms.assetid: f3f5d85f-9359-4508-bc5a-7f78a3cf7421
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: fae03147c4e5364ae7c41590c88c9b6791a6370c
ms.sourcegitcommit: 08b3de02475314c07a82a88c77926d226098e23f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49119991"
---
# <a name="report-server-web-service-endpoints"></a>Конечные точки веб-службы сервера отчетов
  Веб-служба сервера отчетов предоставляет несколько конечных точек для управления сервером отчетов, а также для выполнения отчетов и перемещения по ним.  
  
## <a name="the-management-endpoints"></a>Конечные точки управления  
 Для управления объектами на сервере отчетов доступны три конечные точки — <xref:ReportService2005>, <xref:ReportService2006> и <xref:ReportService2010>. Конечная точка <xref:ReportService2005> используется для управления объектами на сервере отчетов, настроенном для работы в собственном режиме. Конечная точка <xref:ReportService2006> используется для управления объектами на сервере отчетов, настроенном для работы в режиме интеграции с SharePoint. <xref:ReportService2010> Конечная точка объединяет функции <xref:ReportService2005> и <xref:ReportService2006> и может управлять объектами на сервере отчетов, для которых настроено собственном режиме или режиме интеграции с SharePoint.  
  
> [!IMPORTANT]  
>  Если сервер отчетов настроен для работы в режиме интеграции с SharePoint, API из пространства имен <xref:ReportService2005> будут возвращать ошибку `rsOperationNotSupportedSharePointMode`. Если сервер отчетов настроен для работы в собственном режиме, API из пространства имен <xref:ReportService2006> будут возвращать ошибку `rsOperationNotSupportedNativeMode`. Аналогично, если зависящие от режима API-интерфейсы в <xref:ReportService2010> используются в непредусмотренных режимах, они вернут соответствующие ошибки.  
  
> [!NOTE]  
>  Конечные точки <xref:ReportService2005> и <xref:ReportService2006> являются устаревшими в [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)]. Конечная точка <xref:ReportService2010> содержит функциональные возможности обеих конечных точек, а также содержит дополнительные функции управления.  
  
 Если сервер отчетов настроен для работы в собственном режиме или в режиме интеграции с SharePoint, WSDL-файл для управления конечной точкой доступен по одному из следующих URL-адресов:  
  
```  
http://<Server Name>/ReportServer/ReportService2010.asmx?wsdl  
```  
  
 Дополнительные сведения см. в разделе [Доступ к API-интерфейсу SOAP](../accessing-the-soap-api.md).  
  
## <a name="the-execution-endpoint"></a>Конечная точка выполнения  
 Конечная точка <xref:ReportExecution2005> упрощает для разработчиков настройку обработки отчетов и подготовку отчетов к просмотру с сервера отчетов, работающего в собственном режиме и в режиме интеграции с SharePoint. Эта конечная точка содержит классы и методы, которые существовали в прежних версиях веб-службы сервера отчетов. Кроме того, в веб-службу сервера отчетов было добавлено несколько новых классов и методов, доступных через конечную точку выполнения.  
  
 WSDL-файл для конечной точки управления доступен по следующему URL-адресу:  
  
```  
http://<Server Name>/ReportServer/ReportExecution2005.asmx?wsdl  
```  
  
 Если сервер отчетов настроен в режиме интеграции с SharePoint, WSDL-файл доступен по следующему URL-адресу:  
  
```  
http://<Server Name>/<Site Name>/_vti_bin/ReportServer/ReportExecution2005.asmx?wsdl  
```  
  
 Дополнительные сведения см. в разделе [Доступ к API-интерфейсу SOAP](../accessing-the-soap-api.md).  
  
## <a name="sharepoint-proxy-endpoints"></a>Конечные точки-посредники SharePoint  
 Если сервер отчетов настроен в режиме интеграции с SharePoint и установлена надстройка служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], то на сервере SharePoint устанавливается набор конечных точек-посредников. Конечные точки-посредники являются главным API для разработки решений отчетов, если сервер отчетов настроен для работы в режиме интеграции с SharePoint. Во время разработки на основе конечных точек-посредников надстройка служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] управляет обменом учетными данными между сервером SharePoint и сервером отчетов в режиме проверки подлинности с доверенной учетной записью. Во время разработки с использованием конечных точек сервера отчетов вызывающее приложение должно управлять обменом учетными данными в режиме проверки подлинности с доверенной учетной записью. В следующей таблице перечислены конечные точки, которые устанавливаются с надстройкой служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].  
  
|Конечная точка-посредник|Описание|  
|--------------------|-----------------|  
|<xref:ReportService2006>|Предоставляет интерфейсы API для управления сервером отчетов, настроенным для работы в режиме интеграции с SharePoint. **Примечание:** Эта конечная точка является устаревшей в [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)].|  
|<xref:ReportService2010>|Предоставляет API-интерфейсы для управления сервером отчетов, настроенным для работы в собственном режиме или в режиме интеграции с SharePoint.|  
|<xref:ReportExecution2005>|Предоставляет интерфейсы API для выполнения отчетов и перемещению по ним.|  
|<xref:ReportServiceAuthentication>|Предоставляет интерфейсы API для проверки подлинности пользователей на сервере отчетов, если веб-приложение SharePoint настроено для проверки подлинности с помощью форм.|  
  
 Далее приведены примеры URL-адресов для ссылок на конечные точки-посредники на сайте SharePoint.  
  
```  
http://<Server Name>/<Site Name>/_vti_bin/ReportServer/ReportService2010.asmx  
```  
  
```  
http://<Server Name>/<Site Name>/_vti_bin/ReportServer/ReportExecution2005.asmx  
```  
  
```  
http://<Server Name>/<Site Name>/_vti_bin/ReportServer/ReportServiceAuthentication.asmx  
```  
  
## <a name="see-also"></a>См. также  
 [Создание приложений с помощью веб-службы и .NET Framework](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md)  
  
  
