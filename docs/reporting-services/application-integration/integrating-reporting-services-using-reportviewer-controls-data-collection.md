---
title: "Сбор данных в 2016 элемента управления ReportViewer | Документы Microsoft"
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
caps.latest.revision: 2
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 4e8b0226c27380bd2089acf8d2d6c8d7b27c7c5b
ms.contentlocale: ru-ru
ms.lasthandoff: 08/09/2017

---
# <a name="integrating-reporting-services-using-reportviewer-controls---data-collection"></a>Интеграция служб Reporting Services с помощью элементов управления ReportViewer — сбор данных
По умолчанию элемент управления ReportViewer собирает сведения об использовании в порядке корпорации Майкрософт, чтобы лучше понять, каким образом customers, производимых использование элемента управления. Создавая лучшего понимания того, как развертывание и использование средства просмотра элемента управления клиентов, будущих разработок может иметь фокус на усовершенствований, которые обеспечивают наиболее клиентам.

Описание методик сбора и использования данных в выпусках Microsoft SQL Server 2016, а также в других продуктах и службах см. в [заявлении о конфиденциальности компании Майкрософт](https://www.microsoft.com/EN-US/privacystatement/SQLServer/Default.aspx).

## <a name="opting-out-of-telemetry"></a>Отказ от телеметрии

Данные телеметрии можно отключить программно с помощью «EnableTelemetry». Это можно сделать, изменив страницу ASPX, размещение элемента управления

```
\<rsweb:ReportViewer ID="ReportViewer1" runat="server" EnableTelemetry="false">
\</rsweb:ReportViewer>
```

Кроме того, pragmatically прежде, чем элемент управления отрисовывается, например как при вызове Page_Load размещения страницы.
    
```
protected void Page_Load(object sender, EventArgs e)
{
    ReportViewer1.EnableTelemetry = false;
}
```
## <a name="see-also"></a>См. также:

[Использование элемента управления WebForms ReportViewer](../../reporting-services/application-integration/using-the-webforms-reportviewer-control.md)  
[Интеграция служб Reporting Services с помощью элементов управления ReportViewer](../../reporting-services/application-integration/integrating-reporting-services-using-reportviewer-controls.md) 




