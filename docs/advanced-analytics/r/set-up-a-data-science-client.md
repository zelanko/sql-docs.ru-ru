---
title: "Настройка клиента обработки и анализа данных | Документация Майкрософт"
ms.custom: 
ms.date: 02/10/2017
ms.prod: r-server
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d15ee956-918f-40e0-b986-2bf929ef303a
caps.latest.revision: 14
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 0661b2fcf9b23d3c81cb0d80f0424d87dbde7ef8
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="set-up--a-data-science-client"></a>Set Up  a Data Science Client
  После настройки экземпляра [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] путем установки **служб R (в базе данных)**необходимо настроить среду разработки R, которая может подключиться к серверу для удаленного выполнения и развертывания. 
  
  Эта среда должна включать пакеты ScaleR, а также может содержать клиентскую среду разработки.
  
 ## <a name="where-to-get-scaler"></a>Как получить ScaleR 
  
  Клиентская среда должна содержать Microsoft R Open, а также дополнительные пакеты RevoScaleR, поддерживающие распределенное выполнение R в SQL Server.  Эти пакеты можно установить несколькими способами.
  
+ Установите [клиент Microsoft R](http://aka.ms/rclient/download). Дополнительные инструкции по установке описаны в статье по [началу работы с Microsoft R Client](https://msdn.microsoft.com/microsoft-r/r-client-get-started).
+ Установите Microsoft R Server. Вы можете получить Microsoft R Server с помощью программы установки SQL Server или нового автономного установщика Windows. Дополнительные сведения см. в статье о [создании изолированного сервера R Server](../../advanced-analytics/r-services/create-a-standalone-r-server.md). Также ознакомьтесь с [обзором Microsoft R Server](https://msdn.microsoft.com/microsoft-r/rserver).

Если у вас есть лицензионное соглашение R Server, мы рекомендуем использовать Microsoft R Server (изолированную версию), чтобы избежать ограничений потоков обработки R и данных в памяти.


## <a name="how-to-set-up-the-r-development-environment"></a>Как настроить среду разработки R

Вы можете использовать любую среду разработки R, совместимую с Windows. 

+ Средства R для Visual Studio поддерживают интеграцию с Microsoft R Open.
+ RStudio является популярной бесплатной средой.  

После установки вам необходимо будет повторно настроить среду, чтобы по умолчанию использовать библиотеки Microsoft R Open. Если этого не сделать, у вас не будет доступа к библиотекам ScaleR. Дополнительные сведения см. в статье с [обзором Microsoft R Client](http://msdn.microsoft.com/microsoft-r/r-client-get-started).
 
## <a name="more-resources"></a>Дополнительные ресурсы
  
 Подробное пошаговое руководство по подключению к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для удаленного выполнения кода R см. в следующем учебнике: [Глубокое погружение в обработку и анализ данных: использование пакетов RevoScaleR](../../advanced-analytics/r-services/data-science-deep-dive-using-the-revoscaler-packages.md).  
 

Чтобы начать использовать Microsoft R Client и пакеты ScaleR с SQL Server, ознакомьтесь со статьей [Get started with ScaleR and data analysis (Microsoft R)](https://msdn.microsoft.com/microsoft-r/scaler-getting-started#) (Приступая к работе с анализом данных и ScaleR (Microsoft R)).  
  
## <a name="see-also"></a>См. также:  
 [Установка служб SQL Server R Services &#40;в базе данных&#41;](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md)  
  
  

