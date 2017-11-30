---
title: "Сбор данных в элементе управления ReportViewer 2016 | Документы Майкрософт"
ms.custom: 
ms.date: 09/06/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 112e0240-351d-46a9-98c7-2be09f26ac60
caps.latest.revision: "2"
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: b2f5f4743b838598aeb5f74271fa063af9bb60f3
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="integrating-reporting-services-using-reportviewer-controls---data-collection"></a>Интеграция служб Reporting Services с помощью элементов управления ReportViewer — сбор данных
По умолчанию элемент управления ReportViewer собирает анонимные сведения об использовании, на основании которых корпорация Майкрософт может лучше понять, каким образом клиенты используют элемент управления. Нужные сведения о развертывании и использовании элемента управления просмотра помогут сконцентрироваться на внесении улучшений для повышения эффективности работы пользователей.

Описание методик сбора и использования данных в выпусках Microsoft SQL Server 2016, а также в других продуктах и службах см. в [заявлении о конфиденциальности компании Майкрософт](https://www.microsoft.com/EN-US/privacystatement/SQLServer/Default.aspx).

## <a name="opting-out-of-telemetry"></a>Отказ от телеметрии

Телеметрию можно отключить программным способом с помощью "EnableTelemetry". Это можно сделать, изменив страницу ASPX, где находится элемент управления.

```
\<rsweb:ReportViewer ID="ReportViewer1" runat="server" EnableTelemetry="false">
\</rsweb:ReportViewer>
```

Или можно воспользоваться программным способом до отрисовки элемента управления, например при вызове Page_Load страницы размещения.
    
```
protected void Page_Load(object sender, EventArgs e)
{
    ReportViewer1.EnableTelemetry = false;
}
```
## <a name="see-also"></a>См. также:

[Использование элемента управления WebForms ReportViewer](../../reporting-services/application-integration/using-the-webforms-reportviewer-control.md)  
[Интеграция служб Reporting Services с помощью элементов управления ReportViewer](../../reporting-services/application-integration/integrating-reporting-services-using-reportviewer-controls.md) 



