---
title: "SQL Server Integration Services (SSIS) Scale Out | Документы Майкрософт"
ms.custom: 
ms.date: 07/18/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: scale-out
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dcfbd1c5-c001-4fb7-b9ae-916e49ab6a96
caps.latest.revision: "6"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 0277d312ce4dab14e7ba64529e3eb2251a0d2d02
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="integration-services-ssis-scale-out"></a>Масштабное развертывание служб Integration Services (SSIS)
Масштабное развертывание [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] обеспечивает высокопроизводительное выполнение пакетов путем распределения выполнения по нескольким компьютерам. Вы можете отправить запрос на несколько выполнений пакетов в SQL Server Management Studio. Эти пакеты будут выполняться параллельно в режиме масштабного развертывания.  

[!INCLUDE[ssIS_md](../../includes/ssis-md.md)] Scale Out состоит из мастера [!INCLUDE[ssIS_md](../../includes/ssis-md.md)] Scale Out и одной или нескольких рабочих ролей [!INCLUDE[ssIS_md](../../includes/ssis-md.md)] Scale Out. Главная роль масштабного развертывания отвечает за управление масштабным развертыванием и получает запросы на выполнение пакетов от пользователей. Рабочие роли масштабного развертывания получают задачи на выполнение от главной роли и осуществляют выполнение пакетов. Дополнительные сведения см. в разделах [Scale Out Master](integration-services-ssis-scale-out-master.md) (Главная роль масштабного развертывания), [Scale Out Worker](integration-services-ssis-scale-out-worker.md) (Рабочая роль масштабного развертывания).

[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Scale Out может настраиваться на одном компьютере, где мастер и рабочая роль Scale Out работают параллельно. Кроме того, масштабное развертывание может выполняться на нескольких компьютерах, где каждая рабочая роль масштабного развертывания находится на отдельном компьютере.
- [Пошаговое руководство. Настройка масштабного развертывания Integration Services](walkthrough-set-up-integration-services-scale-out.md)

Масштабное развертывание поддерживает параллельное выполнение нескольких пакетов в каталоге SSISDB. Дополнительные сведения см. в разделе [Выполнение пакетов в масштабном развертывании](run-packages-in-integration-services-ssis-scale-out.md).
