---
title: Передача моментальных снимков через FTP | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- snapshots [SQL Server replication], FTP snapshots
- FTP snapshots [SQL Server replication]
- snapshot replication [SQL Server], FTP
ms.assetid: 55c30791-cd2a-420b-8ba7-5700e005cb45
caps.latest.revision: 39
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: a634b0cf961d922ea3169f5c44aa7c87f3ec42fe
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36194685"
---
# <a name="transfer-snapshots-through-ftp"></a>Передача моментальных снимков через FTP
  По умолчанию моментальные снимки сохраняются в папках, определенных как совместно используемые папки в формате универсального соглашения об именовании (UNC). Репликация также позволяет задать общий FTP-ресурс вместо общего UNC-ресурса. Для использования FTP необходимо настроить FTP-сервер, а затем настроить публикацию и одну или несколько подписок для использования FTP. Сведения о настройке FTP-сервера см. в документации по службам IIS (Internet Information Services). При задании сведений об FTP для публикации подписки на эту публикацию будут по умолчанию использовать FTP. Протокол FTP используется только при веб-синхронизации, когда компьютер, на котором запущены службы IIS, отделен от распространителя брандмауэром. В этом случае протокол FTP может использоваться для передачи моментального снимка с распространителя и компьютера, на котором выполняются службы IIS. (Моментальный снимок всегда передается подписчику по протоколу HTTPS.)  
  
> [!IMPORTANT]  
>  Рекомендуется использовать проверку подлинности [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows и общий UNC-ресурс вместо общего FTP-ресурса, поскольку пароли FTP необходимо сохранять, и они передаются с подписчика или с компьютера, на котором запущены службы IIS с использованием веб-синхронизации, на FTP-сервер без шифрования. Кроме этого, поскольку одна учетная запись управляет доступом к хранилищу моментального снимка, невозможно гарантировать, что подписчик на фильтруемую публикацию слиянием имеет доступ только к файлам моментальных снимков из своей секции данных.  
  
 Сведения о доставке моментальных снимков по протоколу FTP см. в разделе [Deliver a Snapshot Through FTP](publish/deliver-a-snapshot-through-ftp.md).  
  
## <a name="see-also"></a>См. также  
 [Веб-синхронизация для репликации слиянием](web-synchronization-for-merge-replication.md)   
 [Инициализация подписки с помощью моментального снимка](initialize-a-subscription-with-a-snapshot.md)   
 [Параметры моментального снимка](snapshot-options.md)  
  
  