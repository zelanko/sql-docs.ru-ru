---
title: "Устаревшая резервная копия | Документация Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 307a4ad0-675a-4f97-9a3c-cedd61bdfae5
caps.latest.revision: 11
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 94f220565078ceddac2aa43eb8e88f9895c27e9d
ms.contentlocale: ru-ru
ms.lasthandoff: 04/11/2017

---
# <a name="outdated-backup"></a>Устаревшая резервная копия
  Это правило обеспечивает наличие последних резервных копий. Регулярное создание резервных копий предохраняет базу данных от потери данных и различных сбоев. Частоту создания резервных копий разумно выбирать в зависимости от модели восстановления базы данных, частоты ее обновления и потребностей организации в отношении возможной потери данных. В часто обновляемой базе данных относительно быстро растет объем рабочих данных, которые не защищены между моментами создания резервных копий.  
  
## <a name="best-practices-recommendations"></a>Рекомендации  
 Рекомендуется достаточно часто создавать резервные копии, чтобы защитить базу данных от потери данных.  
  
 Создавать резервные копии данных необходимо и в простой модели восстановления, и в модели полного восстановления. В любой модели восстановления полные резервные копии можно дополнять разностными резервными копиями. Это позволяет дополнительно снизить риск потери данных.  
  
 Для базы данных, использующей модель полного восстановления, рекомендуется достаточно часто создавать резервные копии журналов. Для рабочих баз данных, содержащих важные сведения, интервал создания резервных копий журналов обычно колеблется от одной до пятнадцати минут.  
  
> [!NOTE]  
>  Для создания расписания резервного копирования рекомендуется пользоваться планом обслуживания базы данных.  
  
## <a name="for-more-information"></a>Дополнительные сведения см. в разделе  
 [Резервное копирование и восстановление системных баз данных (SQL Server)](../../relational-databases/backup-restore/back-up-and-restore-of-system-databases-sql-server.md)  
  
 [Модели восстановления (SQL Server)](../../relational-databases/backup-restore/recovery-models-sql-server.md)  
  
 [Создание разностной резервной копии базы данных (SQL Server)](../../relational-databases/backup-restore/create-a-differential-database-backup-sql-server.md)  
  
 [Создание полной резервной копии базы данных (SQL Server)](../../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md)  
  
 [Планы обслуживания](../../relational-databases/maintenance-plans/maintenance-plans.md)  
  
 [Резервные копии журналов транзакций (SQL Server)](../../relational-databases/backup-restore/transaction-log-backups-sql-server.md)  
  
## <a name="see-also"></a>См. также:  
 [Наблюдение с помощью управления на основе политик и принудительное применение рекомендаций с помощью управления на основе политик](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
