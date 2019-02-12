---
title: Использование защищенных методов веб-службы | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.topic: reference
helpviewer_keywords:
- SOAP [Reporting Services], secure connections
- Web service [Reporting Services], SOAP
- Report Server Web service, SOAP
- XML Web service [Reporting Services], SOAP
ms.assetid: 87329299-c2ea-4517-9148-d855726768a9
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: bedd007e7dabe1f96ac9f5fc22f565952c99d728
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/11/2019
ms.locfileid: "56018865"
---
# <a name="using-secure-web-service-methods"></a>Использование защищенных методов веб-службы
  При вызове некоторых из методов веб-служб сервера отчетов может потребоваться наличие безопасного соединения. То, для каких из методов требуется наличие безопасного соединения, определяется значением параметра `SecureConnectionLevel` в файле RSReportServer.config. Значение этого параметра должно быть целым числом и находиться в диапазоне от 0 и выше. Данные значения описываются в следующей таблице.  
  
|Level|Описание|  
|-----------|-----------------|  
|**0**|Небезопасный. Для вызовов к API SOAP служб Reporting Services не требуется безопасное соединение.|  
|Больше **0**|Безопасный уровень. Для всех вызовов к API-интерфейсу SOAP служб Reporting Services необходимо наличие безопасного соединения.|  
  
 Метод <xref:ReportExecution2005.ReportExecutionService.ListSecureMethods%2A> веб-службы можно использовать для возвращения списка всех методов веб-службы, для которых необходимо наличие безопасного соединения, в соответствии с текущей конфигурацией сервера отчетов. При работе с SSL пользователю необходимо оценить список методов, возвращаемых методом <xref:ReportExecution2005.ReportExecutionService.ListSecureMethods%2A>, и изменить имя схемы URI веб-службы на «https» или «http» в зависимости от вызываемого метода.  
  
## <a name="see-also"></a>См. также  
 [Создание приложений с помощью веб-службы и .NET Framework](building-applications-using-the-web-service-and-the-net-framework.md)   
 [Веб-службы сервера отчетов](../report-server-web-service.md)  
  
  
