---
title: "Включение инициализации из резервной копии для публикаций транзакций | Документация Майкрософт"
ms.custom: 
ms.date: 03/07/2017
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
- manual subscription initialization [SQL Server replication]
- subscriptions [SQL Server replication], initializing
- initializing subscriptions [SQL Server replication], without snapshots
- transactional replication, backup and restore
- backups [SQL Server replication], transactional replication
ms.assetid: 9df00514-aa9d-4ac6-9766-d226c9958175
caps.latest.revision: "30"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f6840a9eddbdf15b75a19d7b04615cffc44a0d3e
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="enable-initialization-with-backup-for-transactional-publications"></a>Включение инициализации из резервной копии для публикаций транзакций
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Для инициализации подписки на публикацию транзакций из резервной копии сначала активизируйте публикацию, чтобы разрешить инициализацию из резервной копии, а затем, создавая подписку, укажите сведения о резервной копии:  
  
-   Включите публикацию на странице **Параметры подписки** диалогового окна **Свойства публикации — \<публикация>**. Дополнительные сведения о доступе к этому диалоговому окну см. в разделе [View and Modify Publication Properties](../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
-   Укажите сведения о резервной копии с помощью хранимой процедуры [sp_addsubscription (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Дополнительные сведения о параметрах **sp_addsubscription** можно найти в статье [Инициализация транзакционной подписки из резервной копии (программирование репликации на языке Transact-SQL)](../../relational-databases/replication/initialize-a-transactional-subscription-from-a-backup.md).  
  
### <a name="to-enable-initialization-with-a-backup"></a>Включение инициализации с помощью резервной копии  
  
1.  На странице **Параметры подписки** диалогового окна **Свойства публикации — \<Публикация>** установите значение **True** для параметра **Разрешать инициализацию из файлов резервных копий**.  
  
## <a name="see-also"></a>См. также:  
 [Инициализация транзакционной подписки без моментального снимка](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md)  
  
  
