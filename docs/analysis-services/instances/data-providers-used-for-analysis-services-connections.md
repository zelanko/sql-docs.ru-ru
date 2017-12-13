---
title: "Поставщики данных, используемые для соединений служб Analysis Services | Документы Microsoft"
ms.custom: 
ms.date: 12/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 128f6dde-409d-4c12-9820-3305bab57b75
caps.latest.revision: "19"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 10f2596b6a2111fac89fc996bf6be521d7158f5d
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2017
---
# <a name="client-libraries-data-providers-used-for-analysis-services-connections"></a>Клиентские библиотеки (поставщики данных) используется для соединений служб Analysis Services
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]

Службы Analysis Services предоставляют три клиентские библиотеки, также известный как **поставщики данных**, для сервера и доступа к данным из средства и клиентских приложений. Средства, такие как среда SSMS и SSDT и приложений, как Power BI Desktop и Excel подключаться к службам Analysis Services с помощью этих библиотек. Два клиентские библиотеки ADOMD.NET и Analysis Services управления объектов AMO, — это управляемый клиент библиотеки. Поставщик OLE DB служб Analysis Services (MSOLAP DLL) — это библиотека собственного клиента. 
  
##  <a name="bkmk_downloadsite"></a>Где можно получить более новых версий  
 Версия, установленная на клиентском компьютере, должна совпадать с основной версией сервера, поставляющего данные. Если установка сервера более новая, чем у поставщиков данных, установленных на рабочих станциях в сети, может потребоваться установить новые библиотеки.  

Клиентские библиотеки, включенных в более ранних пакеты дополнительных компонентов SQL Server соответствуют этой версии SQL; они не могут быть последней версии. Подключение к службам Analysis Services Azure может потребоваться более поздних версиях. Все версии обладают обратной совместимостью.

Чтобы получить последнюю версию, в разделе [клиентские библиотеки для подключения к службам Analysis Services Azure](https://docs.microsoft.com/azure/analysis-services/analysis-services-data-providers). 
  
## <a name="see-also"></a>См. также  
 [Подключение к службам Analysis Services](../../analysis-services/instances/connect-to-analysis-services.md)  
  
  
