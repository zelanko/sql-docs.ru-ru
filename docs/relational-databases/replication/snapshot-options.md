---
title: "Параметры моментального снимка | Документация Майкрософт"
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
- snapshot replication [SQL Server], options
- snapshots [SQL Server replication], options
ms.assetid: 759fab42-66c7-4541-a7a3-bb6fb868493c
caps.latest.revision: "28"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 9b5c6fc564df5fef3034b6ed7cb9d32734ce5fcc
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="snapshot-options"></a>Параметры моментального снимка
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] При инициализации подписки с помощью моментального снимка есть несколько возможностей:  
  
-   Указать другое расположение папки моментальных снимков вместо папки по умолчанию или в дополнение к ней. Дополнительные сведения см. в статье [Alternate Snapshot Folder Locations](../../relational-databases/replication/alternate-snapshot-folder-locations.md).  
  
-   Сжать моментальные снимки для хранения на съемном носителе или для передачи по медленной сети. Дополнительные сведения см. в разделе [Compressed Snapshots](../../relational-databases/replication/compressed-snapshots.md).  
  
-   Выполнить скрипты [!INCLUDE[tsql](../../includes/tsql-md.md)] до или после применения моментального снимка. Дополнительные сведения см. в статье [Выполнение скриптов до и после применения моментального снимка](../../relational-databases/replication/execute-scripts-before-and-after-the-snapshot-is-applied.md).  
  
-   Передать файлы моментальных снимков с помощью протокола передачи файлов (FTP). Дополнительные сведения см. в статье [Передача моментальных снимков через FTP](../../relational-databases/replication/transfer-snapshots-through-ftp.md).  
  
## <a name="see-also"></a>См. также:  
 [Инициализация подписки с помощью моментального снимка](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)  
  
  
