---
title: "Передача моментальных снимков через FTP | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- snapshots [SQL Server replication], FTP snapshots
- FTP snapshots [SQL Server replication]
- snapshot replication [SQL Server], FTP
ms.assetid: 55c30791-cd2a-420b-8ba7-5700e005cb45
caps.latest.revision: "40"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4389eb11fae4e538b0f5ff5d98450738b6847ccd
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="transfer-snapshots-through-ftp"></a>Передача моментальных снимков через FTP
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] По умолчанию моментальные снимки сохраняются в папках, определенных как совместно используемые папки в формате UNC. Репликация также позволяет задать общий FTP-ресурс вместо общего UNC-ресурса. Для использования FTP необходимо настроить FTP-сервер, а затем настроить публикацию и одну или несколько подписок для использования FTP. Сведения о настройке FTP-сервера см. в документации по службам IIS (Internet Information Services). При задании сведений об FTP для публикации подписки на эту публикацию будут по умолчанию использовать FTP. Протокол FTP используется только при веб-синхронизации, когда компьютер, на котором запущены службы IIS, отделен от распространителя брандмауэром. В этом случае протокол FTP может использоваться для передачи моментального снимка с распространителя и компьютера, на котором выполняются службы IIS. (Моментальный снимок всегда передается подписчику по протоколу HTTPS.)  
  
> [!IMPORTANT]  
>  Рекомендуется использовать проверку подлинности [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows и общий UNC-ресурс вместо общего FTP-ресурса, поскольку пароли FTP необходимо сохранять, и они передаются с подписчика или с компьютера, на котором запущены службы IIS с использованием веб-синхронизации, на FTP-сервер без шифрования. Кроме этого, поскольку одна учетная запись управляет доступом к хранилищу моментального снимка, невозможно гарантировать, что подписчик на фильтруемую публикацию слиянием имеет доступ только к файлам моментальных снимков из своей секции данных.  
  
 Сведения о доставке моментальных снимков по протоколу FTP см. в разделе [Deliver a Snapshot Through FTP](../../relational-databases/replication/publish/deliver-a-snapshot-through-ftp.md).  
  
## <a name="see-also"></a>См. также:  
 [Веб-синхронизация для репликации слиянием](../../relational-databases/replication/web-synchronization-for-merge-replication.md)   
 [Инициализация подписки с помощью моментального снимка](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)   
 [Параметры моментального снимка](../../relational-databases/replication/snapshot-options.md)  
  
  
