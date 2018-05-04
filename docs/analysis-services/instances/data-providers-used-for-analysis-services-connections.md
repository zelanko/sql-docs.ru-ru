---
title: Поставщики данных, используемые для соединений служб Analysis Services | Документы Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: ''
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7703bda267a7b646bf6ccbbfee98c7401599f3a0
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="client-libraries-data-providers-used-for-analysis-services-connections"></a>Клиентские библиотеки (поставщики данных) используется для соединений служб Analysis Services
[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

Службы Analysis Services предоставляют три клиентские библиотеки, также известный как **поставщики данных**, для сервера и доступа к данным из средства и клиентских приложений. Средства, такие как среда SSMS и SSDT и приложений, как Power BI Desktop и Excel подключаться к службам Analysis Services с помощью этих библиотек. Два клиентские библиотеки ADOMD.NET и Analysis Services управления объектов AMO, — это управляемый клиент библиотеки. Поставщик OLE DB служб Analysis Services (MSOLAP DLL) — это библиотека собственного клиента. Клиентские библиотеки для SQL Server Analysis Services и служб Azure Analysis Services одинаковы.
  
##  <a name="bkmk_downloadsite"></a> Где можно получить более новых версий  
 Версия, установленная на клиентском компьютере должен совпадать с основной версией сервера, поставляющего данные. Если установка сервера более новая, чем у поставщиков данных, установленных на рабочих станциях в сети, может потребоваться установить новые библиотеки.  

Клиентские библиотеки, включенных в более ранних пакеты дополнительных компонентов SQL Server соответствуют этой версии SQL; они не могут быть последней версии. Подключение к службам Analysis Services Azure может потребоваться более поздних версиях. Все версии обладают обратной совместимостью.

Чтобы получить последнюю версию, в разделе [клиентские библиотеки для подключения к службам Analysis Services Azure](https://docs.microsoft.com/azure/analysis-services/analysis-services-data-providers). 
  
## <a name="see-also"></a>См. также:  
 [Подключение к службам Analysis Services](../../analysis-services/instances/connect-to-analysis-services.md)  
  
  
