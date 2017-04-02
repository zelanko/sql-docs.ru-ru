---
title: "Настройка клиента обработки и анализа данных | Microsoft Docs"
ms.custom: ""
ms.date: "02/10/2017"
ms.prod: "r-server"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d15ee956-918f-40e0-b986-2bf929ef303a
caps.latest.revision: 14
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 10
---
# Настройка клиента обработки и анализа данных
  После настройки экземпляра [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] путем установки **служб R (в базе данных)** необходимо настроить среду разработки R, которая может подключиться к серверу для удаленного выполнения и развертывания. 
  
  Клиентская среда должна содержать Microsoft R Open, а также дополнительные пакеты RevoScaleR, поддерживающие распределенное выполнение R в SQL Server.  Эти пакеты можно установить несколькими способами.
  
+ Установите [клиент Microsoft R](http://aka.ms/rclient/download).
+ Установите Microsoft R Server. Microsoft R Server можно получить из программы установки SQL Server или из автономного установщика. Дополнительные сведения см. в разделе [Создание изолированного сервера R Server](../../advanced-analytics/r-services/create-a-standalone-r-server.md) или [Введение в R Server](https://msdnstage.redmond.corp.microsoft.com/en-us/microsoft-r/rserver?branch=r-server-nov16-dev).

 Дополнительные сведения об использовании клиента Microsoft R для подключения к SQL Server с помощью пакетов ScaleR см. в разделе [Начало работы со ScaleR](https://msdn.microsoft.com/microsoft-r/scaler-getting-started#).  
  
 Подробное пошаговое руководство по подключению к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для удаленного выполнения кода R см. в следующем учебнике: [Глубокое погружение в обработку и анализ данных: использование пакетов RevoScaleR](../../advanced-analytics/r-services/data-science-deep-dive-using-the-revoscaler-packages.md).  
  
## <a name="see-also"></a>См. также:  
 [Установка служб SQL Server R Services &#40;в базе данных&#41;](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md)  
  
  