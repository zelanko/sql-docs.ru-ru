---
title: "SQL Server Integration Services (SSIS) для горизонтального масштабирования | Документы Microsoft"
ms.custom: 
ms.date: 07/18/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dcfbd1c5-c001-4fb7-b9ae-916e49ab6a96
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: ce7fb96901e8af4da74392fe0a0a85c6e2ec05a4
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="integration-services-ssis-scale-out"></a>Масштабное развертывание служб Integration Services (SSIS)
Масштабное развертывание [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] обеспечивает высокопроизводительное выполнение пакетов путем распределения выполнения по нескольким компьютерам. Можно отправить запрос для выполнения нескольких пакетов в SQL Server Management Studio. Эти пакеты будут выполняться параллельно в режиме масштабного развертывания.  

[!INCLUDE[ssIS_md](../../includes/ssis-md.md)]Масштабное развертывание состоит из [!INCLUDE[ssIS_md](../../includes/ssis-md.md)] шкалы Out главного и один или несколько [!INCLUDE[ssIS_md](../../includes/ssis-md.md)] шкалы ожидания рабочих процессов. Главная роль масштабного развертывания отвечает за управление масштабным развертыванием и получает запросы на выполнение пакетов от пользователей. Рабочие роли масштабного развертывания получают задачи на выполнение от главной роли и осуществляют выполнение пакетов. Дополнительные сведения см. в разделах [Scale Out Master](integration-services-ssis-scale-out-master.md) (Главная роль масштабного развертывания), [Scale Out Worker](integration-services-ssis-scale-out-worker.md) (Рабочая роль масштабного развертывания).

[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]Масштабное развертывание можно настроить на одном компьютере, где Master Out шкалы и шкалы Out рабочих настраиваются side-by-side, на компьютере. Кроме того, масштабное развертывание может выполняться на нескольких компьютерах, где каждая рабочая роль масштабного развертывания находится на отдельном компьютере.
- [Пошаговое руководство. Настройка масштабного развертывания Integration Services](walkthrough-set-up-integration-services-scale-out.md)

Масштабное развертывание поддерживает параллельное выполнение нескольких пакетов в каталоге SSISDB. Дополнительные сведения см. в разделе [Выполнение пакетов в масштабном развертывании](run-packages-in-integration-services-ssis-scale-out.md).

