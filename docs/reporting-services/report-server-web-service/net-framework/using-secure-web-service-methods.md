---
title: Использование защищенных методов веб-службы | Документы Майкрософт
ms.date: 03/06/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server-web-service
ms.topic: reference
helpviewer_keywords:
- SOAP [Reporting Services], secure connections
- Web service [Reporting Services], SOAP
- Report Server Web service, SOAP
- XML Web service [Reporting Services], SOAP
ms.assetid: 87329299-c2ea-4517-9148-d855726768a9
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 4f5b9e7f53b13c32557aec92907767600707141c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47734112"
---
# <a name="using-secure-web-service-methods"></a>Использование защищенных методов веб-службы
  При вызове некоторых из методов веб-служб сервера отчетов может потребоваться наличие безопасного соединения. То, для каких из методов требуется безопасное соединение, определяется значением параметра **SecureConnectionLevel** в файле RSReportServer.config. Значение этого параметра должно быть целым числом и находиться в диапазоне от 0 и выше. Данные значения описываются в следующей таблице.  
  
|Level|Описание|  
|-----------|-----------------|  
|**0**|Небезопасный. Для вызовов к API SOAP служб Reporting Services не требуется безопасное соединение.|  
|Больше **0**|Безопасный уровень. Для всех вызовов к API-интерфейсу SOAP служб Reporting Services необходимо наличие безопасного соединения.|  
  
 Метод <xref:ReportExecution2005.ReportExecutionService.ListSecureMethods%2A> веб-службы можно использовать для возвращения списка всех методов веб-службы, для которых необходимо наличие безопасного соединения, в соответствии с текущей конфигурацией сервера отчетов. При работе с SSL пользователю необходимо оценить список методов, возвращаемых методом <xref:ReportExecution2005.ReportExecutionService.ListSecureMethods%2A>, и изменить имя схемы URI веб-службы на «https» или «http» в зависимости от вызываемого метода.  
  
## <a name="see-also"></a>См. также:  
 [Создание приложений с помощью веб-службы и .NET Framework](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [Веб-службы сервера отчетов](../../../reporting-services/report-server-web-service/report-server-web-service.md)  
  
  
