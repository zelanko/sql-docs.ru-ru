---
title: Управление базами данных DQS | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: data-quality-services
ms.service: ''
ms.component: data-quality-services
ms.reviewer: ''
ms.suite: sql
ms.technology:
- data-quality-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 655a67aa-d662-42f2-b982-c6217125ada8
caps.latest.revision: 14
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5187411325c00feaf15cfd18809473788e31f105
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="manage-dqs-databases"></a>Manage DQS Databases

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  В этом разделе приведены сведения о действиях по управлению базами данных, которые можно выполнять с базами данных DQS, например резервное копирование и восстановление или отсоединение и присоединение.  
  
##  <a name="BackupRestore"></a> Резервное копирование и восстановление баз данных DQS  
 Резервное копирование и восстановление базы данных SQL Server — это основные операции, выполняемые администратором базы данных для предотвращения потери данных в случае аварии при помощи восстановленных данных из резервной копии базы данных по журналу. [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] в основном реализуется двумя базами данных SQL Server: DQS_MAIN и DQS_PROJECTS. Процедуры резервного копирования и восстановления базы данных [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) аналогичны этим процедурам для любой другой базой данных SQL Server. Есть три проблемы, связанные с резервным копированием и восстановлением базы данных DQS.  
  
-   Операции резервного копирования и восстановления баз данных DQS должны быть синхронизированы. В противном случае восстановленный [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] не будет работать.  
  
-   Две базы данных DQS, DQS_MAIN и DQS_PROJECTS, помимо простых объектов базы данных, например таблиц и хранимых процедур, содержат сборки и другие сложные объекты.  
  
-   Есть несколько сущностей вне модели базы данных DQS, которые должны существовать для базы данных DQS, функционирующей в качестве [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)], а именно два имени входа SQL Server (##MS_dqs_db_owner_login## и ##MS_dqs_service_login##) и хранимые процедуры инициализации (DQInitDQS_MAIN) в базе данных master.  
  
 Дополнительные сведения о резервном копировании и восстановлении в SQL Server см. в разделе [Резервное копирование и восстановление баз данных SQL Server](../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md).  
  
### <a name="default-autogrowth-size-and-recovery-model-for-the-dqs-databases"></a>Используемый по умолчанию размер автоувеличения и модель восстановления для баз данных DQS  
 Чтобы предотвратить неограниченный рост баз данных DQS и журналов транзакций с потенциальным заполнением жесткого диска, заданы следующие условия.  
  
-   Размер **Автоувеличение** для баз данных DQS по умолчанию имеет значение 10 %.  
  
-   Модель восстановления для баз данных DQS по умолчанию имеет значение **Простая**. В простой модели восстановления ведется минимальное протоколирование транзакций, и усечение журнала выполняется автоматически после завершения транзакции, чтобы освободить место в журнале транзакций (LDF-файле). Подробные сведения о простой модели восстановления см. в разделе [Полные резервные копии баз данных &#40;SQL Server&#41;](../relational-databases/backup-restore/full-database-backups-sql-server.md).  
  
> [!IMPORTANT]  
>  -   В простой модели восстановления, если записи журнала остаются активными в течение длительного времени (например, в продолжительной транзакции), усечение журнала может откладываться, в результате журнал транзакций будет заполняться. Кроме того, усечение журнала не приводит к уменьшению размера физического файла журнала (LDF-файла). Для уменьшения размера физического файла журнала необходимо выполнить его сжатие. Сведения об устранении неполадок с журналом транзакций см. в разделе [Журнал транзакций (SQL Server)](../relational-databases/logs/the-transaction-log-sql-server.md) или в статье службы поддержки Майкрософт по адресу [http://go.microsoft.com/fwlink/?LinkId=237446](http://go.microsoft.com/fwlink/?LinkId=237446).  
> -   Необходимо регулярно выполнять полное или разностное резервное копирование баз данных DQS, а также создавать резервную копию журнала транзакций, чтобы выполнять восстановление данных на момент времени. Дополнительные сведения см. в разделах [Полные резервные копии баз данных &#40;SQL Server&#41;](../relational-databases/backup-restore/full-database-backups-sql-server.md) и [Создание резервной копии журнала транзакций &#40;SQL Server&#41;](../relational-databases/backup-restore/back-up-a-transaction-log-sql-server.md).  
  
##  <a name="DetachAttach"></a> Присоединение и отсоединение баз данных DQS  
 Файлы данных и журналов транзакций баз данных DQS можно отсоединять, а затем снова присоединять базы данных к этому же или другому экземпляру SQL Server, если требуется перенести базы данных DQS на другой экземпляр SQL Server, размещенный на этом же компьютере или переместить базу данных.  
  
 Подробные сведения о том, что следует учитывать при отсоединении и присоединении баз данных в SQL Server, см. в разделе [Присоединение и отсоединение баз данных &#40;SQL Server&#41;](../relational-databases/databases/database-detach-and-attach-sql-server.md).  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Описание задачи|Раздел|  
|----------------------|-----------|  
|Описывает создание резервных копий и восстановление базы данных DQS.|[Резервное копирование и восстановление баз данных DQS](../data-quality-services/backing-up-and-restoring-dqs-databases.md)|  
|Описывает, как отсоединять и присоединять базы данных DQS.|[Присоединение и отсоединение баз данных DQS](../data-quality-services/detaching-and-attaching-dqs-databases.md)|  
  
## <a name="see-also"></a>См. также:  
 [Администрирование DQS](../data-quality-services/dqs-administration.md)  
  
  
