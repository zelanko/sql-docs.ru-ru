---
title: Поставщики данных, используемые для соединений служб Analysis Services | Документация Майкрософт
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f5ba97f90b877896d68cd62598f11d0845fb698e
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38057852"
---
# <a name="client-libraries-data-providers-used-for-analysis-services-connections"></a>Клиентские библиотеки (поставщики данных), используемые для соединений служб Analysis Services
[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

Службы Analysis Services предоставляют три клиентские библиотеки, также известный как **поставщики данных**, для сервера и доступа к данным из клиентских приложений и средств. Средства, такие как SSMS и SSDT и приложения Power BI Desktop и Excel подключиться к службам Analysis Services с помощью этих библиотек. Два клиентских библиотек, ADOMD.NET и Analysis Services Management объекты AMO, — управляемые клиентские библиотеки. Поставщик OLE DB служб Analysis Services (MSOLAP DLL) — это библиотека собственного клиента. Клиентские библиотеки для SQL Server Analysis Services и служб Azure Analysis Services одинаковы.
  
##  <a name="bkmk_downloadsite"></a> Где можно получить более новые версии  
 Версия, установленная на клиентском компьютере должен соответствовать основному номеру версии сервера, поставляющего данные. Если установка сервера более новая, чем у поставщиков данных, установленных на рабочих станциях в сети, может потребоваться установить новые библиотеки.  

Клиентские библиотеки, которые включены в более ранние пакеты дополнительных компонентов SQL Server соответствуют до этой версии SQL; Тем не менее они могут быть не последней. Подключение к службам Azure Analysis Services может потребоваться более поздних версий. Все версии обладают обратной совместимостью.

Чтобы получить последнюю версию, см. в разделе [клиентские библиотеки для подключения к службам Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/analysis-services-data-providers). 
  
## <a name="see-also"></a>См. также  
 [Подключение к службам Analysis Services](../../analysis-services/instances/connect-to-analysis-services.md)  
  
  
