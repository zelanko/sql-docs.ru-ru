---
title: "Сбор данных в элементе управления ReportViewer 2016 | Документы Майкрософт"
ms.custom: 
ms.date: 09/06/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.service: 
ms.component: application-integration
ms.reviewer: 
ms.suite: pro-bi
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
ms.openlocfilehash: 6249d0a0b8b13c47479130c1f981b6756989c4c7
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2017
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
## <a name="see-also"></a>См. также

[Использование элемента управления WebForms ReportViewer](../../reporting-services/application-integration/using-the-webforms-reportviewer-control.md)  
[Интеграция служб Reporting Services с помощью элементов управления ReportViewer](../../reporting-services/application-integration/integrating-reporting-services-using-reportviewer-controls.md) 



