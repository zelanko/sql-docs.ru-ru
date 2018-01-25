---
title: "Поставщики данных, используемые для соединений служб Analysis Services | Документы Microsoft"
ms.custom: 
ms.date: 01/23/2018
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 128f6dde-409d-4c12-9820-3305bab57b75
caps.latest.revision: "19"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 816919b48f77a4462e8d0f0f04d0bb621a2d2058
ms.sourcegitcommit: 3206a31870f8febab7d1718fa59fe0590d4d45db
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/24/2018
---
# <a name="client-libraries-data-providers-used-for-analysis-services-connections"></a>Клиентские библиотеки (поставщики данных) используется для соединений служб Analysis Services
[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

Службы Analysis Services предоставляют три клиентские библиотеки, также известный как **поставщики данных**, для сервера и доступа к данным из средства и клиентских приложений. Средства, такие как среда SSMS и SSDT и приложений, как Power BI Desktop и Excel подключаться к службам Analysis Services с помощью этих библиотек. Два клиентские библиотеки ADOMD.NET и Analysis Services управления объектов AMO, — это управляемый клиент библиотеки. Поставщик OLE DB служб Analysis Services (MSOLAP DLL) — это библиотека собственного клиента. Клиентские библиотеки для SQL Server Analysis Services и служб Azure Analysis Services одинаковы.
  
##  <a name="bkmk_downloadsite"></a>Где можно получить более новых версий  
 Версия, установленная на клиентском компьютере должен совпадать с основной версией сервера, поставляющего данные. Если установка сервера более новая, чем у поставщиков данных, установленных на рабочих станциях в сети, может потребоваться установить новые библиотеки.  

Клиентские библиотеки, включенных в более ранних пакеты дополнительных компонентов SQL Server соответствуют этой версии SQL; они не могут быть последней версии. Подключение к службам Analysis Services Azure может потребоваться более поздних версиях. Все версии обладают обратной совместимостью.

Чтобы получить последнюю версию, в разделе [клиентские библиотеки для подключения к службам Analysis Services Azure](https://docs.microsoft.com/azure/analysis-services/analysis-services-data-providers). 
  
## <a name="see-also"></a>См. также:  
 [Подключение к службам Analysis Services](../../analysis-services/instances/connect-to-analysis-services.md)  
  
  
