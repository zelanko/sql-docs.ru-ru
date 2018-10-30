---
title: Сбор данных в элементе управления ReportViewer 2016 | Документы Майкрософт
ms.date: 09/18/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: application-integration
ms.topic: reference
ms.assetid: 112e0240-351d-46a9-98c7-2be09f26ac60
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 69cc665274d7463982cdfddd32d2b979e25a156e
ms.sourcegitcommit: 3daacc4198918d33179f595ba7cd4ccb2a13b3c0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/25/2018
ms.locfileid: "50028153"
---
# <a name="integrating-reporting-services-using-reportviewer-controls---data-collection"></a>Интеграция служб Reporting Services с помощью элементов управления ReportViewer — сбор данных

Элемент управления собирает анонимные данные, которые позволяют лучше понять, как клиенты используют продукт. Данные об использовании позволяют улучшать продукт в будущем.

Описание методик сбора и использования данных Microsoft SQL Server и средства просмотра отчетов приведено в [заявлении о конфиденциальности](https://go.microsoft.com/fwlink/?LinkID=868444).

## <a name="opting-out-of-data-collection"></a>Отказ от сбора данных

Сбор данных об использовании можно отключить с помощью свойства ```EnableTelemetry```.

```
<rsweb:ReportViewer ID="ReportViewer1" runat="server" EnableTelemetry="false">
</rsweb:ReportViewer>
```

Кроме того, это можно сделать программным способом перед настройкой элемента управления.
    
```
protected void Page_Load(object sender, EventArgs e)
{
    ReportViewer1.EnableTelemetry = false;
}
```
## <a name="see-also"></a>См. также раздел

[Using the WebForms ReportViewer Control](../../reporting-services/application-integration/using-the-webforms-reportviewer-control.md) (Использование элемента управления средства просмотра отчетов WebForms)  
[Интеграция служб Reporting Services с помощью элементов управления средства просмотра отчетов](../../reporting-services/application-integration/integrating-reporting-services-using-reportviewer-controls.md) 



