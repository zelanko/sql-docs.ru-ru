---
title: "Принудительный опрос главного сервера целевым сервером | Документация Майкрософт"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: ssms-agent
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- forcing master server polling
- polling master servers [SQL Server]
- master servers [SQL Server], polling
- target servers [SQL Server], polling the master server
ms.assetid: f1189a47-5ac3-45e2-9c5f-847810672279
caps.latest.revision: "4"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 52f3c9f930d257f5c29b9440adab755fba6c121b
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2017
---
# <a name="force-a-target-server-to-poll-the-master-server"></a>Force a Target Server to Poll the Master Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] В этом подразделе описана реализация принудительного опроса главного сервера целевым сервером. Целевой сервер должен быть зарегистрирован на главном.  
  
Задание — это указанная последовательность действий, выполняемых агентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] . Многосерверное задание — это задание, которое главный сервер выполняет на одном или нескольких целевых серверах. На каждом целевом сервере может одновременно выполняться только один экземпляр одного и того же задания. Каждый целевой сервер периодически опрашивает главный сервер, загружает копию новых назначенных ему заданий и отключается. Целевой сервер выполняет задание локально, а затем снова подключается к главному серверу, чтобы передать результирующее состояние задания.  
  
> [!NOTE]  
> Если главный сервер недоступен в момент, когда целевой сервер пытается передать состояние задания, то сведения о состоянии задания помещаются в очередь, пока главный сервер не станет доступен.  
  
-   **Перед началом:**  [Ограничения](#Restrictions), [Безопасность](#Security)  
  
-   **Для принудительного опроса главного сервера целевым сервером используется:** [Среда SQL Server Management Studio](#SSMS)  
  
## <a name="BeforeYouBegin"></a>Перед началом  
  
### <a name="Restrictions"></a>Ограничения  
Целевой сервер должен быть зарегистрирован на главном. Инструкции, приведенные в этом разделе, необходимо запускать с главного сервера.  
  
### <a name="Security"></a>Безопасность  
Дополнительные сведения см. в разделах [Implement SQL Server Agent Security](../../ssms/agent/implement-sql-server-agent-security.md) и [Choose the Right SQL Server Agent Service Account for Multiserver Environments](../../ssms/agent/choose-the-right-sql-server-agent-service-account-for-multiserver-environments.md).  
  
## <a name="SSMS"></a>Использование среды SQL Server Management Studio  
**Принудительный опрос главного сервера целевым сервером**  
  
1.  В **Обозревателе объектов**разверните главный сервер.  
  
2.  Щелкните правой кнопкой мыши элемент **Агент SQL Server**, укажите пункт **Администрирование нескольких серверов**, а затем выберите пункт **Управление целевыми серверами**.  
  
3.  Щелкните целевой сервер, а затем нажмите кнопку **Опрос**.  
  
