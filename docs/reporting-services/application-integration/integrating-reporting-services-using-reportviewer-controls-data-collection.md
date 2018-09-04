---
title: Сбор данных в элементе управления ReportViewer 2016 | Документы Майкрософт
ms.date: 09/06/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: application-integration
ms.suite: pro-bi
ms.topic: reference
ms.assetid: 112e0240-351d-46a9-98c7-2be09f26ac60
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 782888c9946fd09d9c711a6eda2a8f77fd18c3ba
ms.sourcegitcommit: d96b94c60d88340224371926f283200496a5ca64
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/30/2018
ms.locfileid: "43267409"
---
# <a name="integrating-reporting-services-using-reportviewer-controls---data-collection"></a>Интеграция служб Reporting Services с помощью элементов управления ReportViewer — сбор данных
По умолчанию элемент управления ReportViewer собирает анонимные сведения об использовании, на основании которых корпорация Майкрософт может лучше понять, каким образом клиенты используют элемент управления. Нужные сведения о развертывании и использовании элемента управления просмотра помогут сконцентрироваться на внесении улучшений для повышения эффективности работы пользователей.

Описание методик сбора и использования данных в выпусках Microsoft SQL Server 2016, а также в других продуктах и службах см. в [заявлении о конфиденциальности]((http://go.microsoft.com/fwlink/?LinkID=868444)).

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
## <a name="see-also"></a>См. также раздел

[Использование элемента управления WebForms ReportViewer](../../reporting-services/application-integration/using-the-webforms-reportviewer-control.md)  
[Интеграция служб Reporting Services с помощью элементов управления ReportViewer](../../reporting-services/application-integration/integrating-reporting-services-using-reportviewer-controls.md) 



