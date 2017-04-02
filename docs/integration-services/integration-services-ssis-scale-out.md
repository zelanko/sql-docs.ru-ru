---
title: "Масштабное развертывание служб Integration Services (SSIS) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: dcfbd1c5-c001-4fb7-b9ae-916e49ab6a96
caps.latest.revision: 6
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 6
---
# Масштабное развертывание служб Integration Services (SSIS)
Масштабное развертывание [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] обеспечивает высокопроизводительное выполнение пакетов путем распределения выполнения по нескольким компьютерам. Вы можете отправить запрос на несколько выполнений пакетов в SQL Server Management Studio. Эти пакеты будут выполняться параллельно в режиме масштабного развертывания.  


## <a name="ssis-scale-out-master-and-scale-out-worker"></a>Главная роль масштабного развертывания и рабочая роль масштабного развертывания SQL Server Integration Services
Масштабное развертывание [!INCLUDE[ssIS_md](../includes/ssis-md.md)] состоит из главной роли масштабного развертывания [!INCLUDE[ssIS_md](../includes/ssis-md.md)] и нескольких рабочих ролей масштабного развертывания [!INCLUDE[ssIS_md](../includes/ssis-md.md)]. Главная роль масштабного развертывания отвечает за управление масштабным развертыванием и получает запросы на выполнение пакетов от пользователей. Рабочие роли масштабного развертывания получают задачи на выполнение от главной роли и осуществляют выполнение пакетов. Дополнительные сведения см. в разделах [Scale Out Master](../integration-services/integration-services-ssis-scale-out-master.md) (Главная роль масштабного развертывания), [Scale Out Worker](../integration-services/integration-services-ssis-scale-out-worker.md) (Рабочая роль масштабного развертывания).


## <a name="how-to-set-up-scale-out"></a>Настройка масштабного развертывания
Масштабное развертывание [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] может выполняться на одном компьютере, где главная и рабочая роли масштабного развертывания работают параллельно. Кроме того, масштабное развертывание может выполняться на нескольких компьютерах, где каждая рабочая роль масштабного развертывания находится на отдельном компьютере.
- [Пошаговое руководство. Настройка масштабного развертывания Integration Services](../integration-services/walkthrough-set-up-integration-services-scale-out.md)


## <a name="run-packages-in-scale-out"></a>Выполнение пакетов в масштабном развертывании
Масштабное развертывание поддерживает параллельное выполнение нескольких пакетов в каталоге SSISDB. Дополнительные сведения см. в разделе [Выполнение пакетов в масштабном развертывании](../integration-services/run-packages-in-integration-services-ssis-scale-out.md).

