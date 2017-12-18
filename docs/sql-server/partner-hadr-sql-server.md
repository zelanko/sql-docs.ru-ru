---
title: "Высокий уровень доступности и аварийное восстановление SQL Server | Документация Майкрософт"
description: "Списки сторонних партнеров, предлагающих решения для мониторинга сервера."
services: sql-server
documentationcenter: NA
author: MikeRayMSFT
manager: jhubbard
editor: 
ms.assetid: 
ms.service: database-engine
ms.component: 
ms.suite: sql
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: sql-server
ms.custom: 
ms.date: 09/17/2017
ms.prod: sql-server
ms.prod_service: sql-non-specified
ms.author: mikeray
ms.openlocfilehash: 0234e7966cc326edf2ce5a85ce03f8e38143f5b5
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="sql-server-high-availability-and-disaster-recovery-partners"></a>Партнеры в области высокой доступности и аварийного восстановления SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] В отрасли доступно множество передовых средств, позволяющих обеспечить высокую доступность и аварийное восстановление для служб SQL Server.  В этой статье указаны партнеры корпорации Майкрософт, которые предлагают решения по обеспечению высокой доступности и аварийного восстановления, поддерживающие Microsoft SQL Server.

## <a name="our-high-availability-and-disaster-recovery-partners"></a>Наши партнеры в области высокой доступности и аварийного восстановления
<!--
|![PartnerShortName][1] |**PartnerShortName**<br>PartnerShortName Brief description of the type of products that partner provides. <br><br>List of supported versions of SQL Server, OS, OS platforms/distros  Server 2005 SP4 – SQL Server 2016 on Windows |[Datasheet][PartnerShortName_datasheet]<br>[Marketplace][PartnerShortName_marketplace]<br>[Website][PartnerShortName_website]<br>[Twitter][PartnerShortName_twitter]<br>[Video][PartnerShortName_youtube]|[![veem_video](./media/partner-hadr-sql-server/PartnerShortName_video.png)](https://www.youtube.com/channel/**************)
-->

| Партнер | Description | Ссылки | 
| --- | --- | --- |
|![azure][5] |**Azure Site Recovery**<br>Site Recovery реплицирует рабочие нагрузки, выполняемые на виртуальных машинах или физических серверах, чтобы они оставались доступными во вторичном расположении, когда первичный сайт недоступен. Вы можете выполнять репликацию и переход на другой ресурс для виртуальных машин SQL Server из локального центра обработки данных в Azure или другой локальный центр обработки данных, а также из одного центра обработки данных Azure в другой.<br><br> Выпуски Enterprise и Standard продуктов SQL Server 2008 R2–SQL Server 2016|[Веб-сайт][azure_website]<br>[Marketplace][azure_marketplace]<br>[Таблица данных][azure_datasheet]<br>[Twitter][azure_twitter]<br>[Видео][azure_youtube]|
|![dh2i][2] |**DH2i**<br>DxEnterprise — это ПО смарт-доступности для Windows, Linux и Docker, которое помогает добиться почти нулевого запланированного и незапланированного простоя, позволяет реализовать огромный потенциал для экономии на расходах, значительно упрощает управление и обеспечивает как физическую, так и логическую консолидацию.<br><br>SQL Server 2005+, Windows Server 2008R2+, Ubuntu 16+, RHEL 7+, CentOS 7+|[Веб-сайт][dh2i_website]<br>[Таблица данных][dh2i_datasheet]<br>[Twitter][dh2i_twitter]<br>[Видео][dh2i_youtube]|
|![hpe][4] |**HPE Serviceguard**<br>HPE Serviceguard for Linux (SGLX) помогает вам защитить критические рабочие нагрузки SQL Server 2017 на базе Linux® от незапланированных и запланированных простоев, вызванных множеством ошибок инфраструктуры и приложений в физических и виртуальных средах любой удаленности. В рамках программы бета-версии HPE SGL X предлагает варианты контекстного мониторинга и восстановления для экземпляра отказоустойчивого кластера и рабочих нагрузок групп доступности AlwaysOn SQL Server. С помощью HPE SGLX вы можете обеспечить максимальное время доступности, не жертвуя целостностью данных и производительностью.<br><br>SQL Server 2017 на базе Linux — RedHat 7.3, 7.4, SuSE 12 с пакетами обновлений 2 (SP2) и 3 (SP3)|[Веб-сайт][hpe_website]<br>[Таблица данных][hpe]<br>[Скачать][hpe_download]<br>[Twitter][hpe_twitter]
|![idera][3]|**IDERA**<br>SQL Safe Backup — это высокопроизводительное решение резервного копирования и восстановления для SQL Server, которое экономит средства за счет уменьшения времени резервного копирования базы данных и размера получаемых при этом файлов, а также предоставления мгновенного доступа на чтение и запись к базам данных в резервных копиях.<br><br>Microsoft SQL Server: 2005 с пакетом обновления 1 SP1) или более поздней версии, 2008, 2008 R2, 2012, 2014, 2016; все выпуски |[Веб-сайт][idera_website]|
|![portworx][6] |**Portworx**<br>Portworx — это решение для использования контейнеров с отслеживанием состояния в рабочей среде. С помощью Portworx пользователи могут управлять любой базой данных или службой с отслеживанием состояния в любой инфраструктуре, используя любой планировщик контейнеров, включая Kubernetes, Mesosphere DC/OS и Docker Swarm. Portworx решает пять основных проблем, с которыми команды DevOps сталкиваются при использовании контейнерных баз данных и других служб с отслеживанием состояния в рабочей среде: сохраняемость, высокая доступность, автоматизация данных, поддержка нескольких хранилищ данных и соответствующей инфраструктуры, а также безопасность.<br><br>SQL Server 2017 с Docker |[Веб-сайт][portworx_website]<br>[Документация][portworx_docs]<br>[Видео][portworx_youtube]|
|![veeam][1] |**Veeam**<br>Veeam Backup & Replication — это производительное, недорогое и удобное решение для обеспечения резервного копирования и доступности. Оно обеспечивает быстрое, гибкое и надежное восстановление виртуализованных приложений и данных, объединяя функции резервного копирования и репликации виртуальных машин. Решение обладает отмеченной наградами поддержкой виртуальных сред VMware vSphere и Microsoft Hyper-V.<br><br>SQL Server 2005 с пакетом обновления 4 (SP4) – SQL Server 2016 на базе Windows |[Веб-сайт][veeam_website]<br>[Таблица данных][veeam_datasheet]<br>[Twitter][veeam_twitter]<br>[Видео][veeam_youtube]|



## <a name="next-steps"></a>Следующие шаги
Дополнительные сведения о некоторых других партнерах см. в разделах, посвященных [мониторингу][mon_partners], [партнерам по управлению][management_partners] и [партнерам по разработке][dev_partners].

<!--Image references-->
[1]: ./media/partner-hadr-sql-server/Veeam_green_logo.png
[2]: ./media/partner-hadr-sql-server/dh2i_logo.png
[3]: ./media/partner-hadr-sql-server/idera_logo.png
[4]: ./media/partner-hadr-sql-server/hpe_pri_grn_pos_rgb.png
[5]: ./media/partner-hadr-sql-server/azure_logo.png
[6]: ./media/partner-hadr-sql-server/portworx_logo.png

<!--Article links-->
[mon_partners]: ./partner-monitor-sql-server.md
[management_partners]: ./partner-management-sql-server.md
[dev_partners]: ./partner-dev-sql-server.md

<!--Website links -->
[veeam_website]:https://www.veeam.com/
[dh2i_website]:http://dh2i.com
[idera_website]:https://www.idera.com/productssolutions/sqlserver
[hpe_website]: https://www.hpe.com/us/en/product-catalog/detail/pip.376220.html
[azure_website]: http://docs.microsoft.com/azure/site-recovery/site-recovery-sql
[portworx_website]: https://portworx.com/

<!--Get Started Links-->

<!--Datasheet Links-->
[veeam_datasheet]:https://www.veeam.com/veeam_backup_9_5_datasheet_en_ds.pdf
[dh2i_datasheet]:http://dh2i.com/wp-content/uploads/DxE-Win-QuickFacts.pdf
[hpe]:https://www.hpe.com/h20195/v2/default.aspx?cc=us&lc=en&oid=376220
[azure_datasheet]: http://docs.microsoft.com/azure/site-recovery/site-recovery-sql#site-recovery-support

<!--Marketplace Links -->
[azure_marketplace]: https://azuremarketplace.microsoft.com/marketplace/apps?search=site%20recovery&page=1
<!--Press links-->
<!--[veeam_press]:-->

<!--YouTube links-->
[veeam_youtube]:https://www.youtube.com/user/YouVeeam
[dh2i_youtube]:https://www.youtube.com/user/dh2icompany 
[idera_youtube]:https://www.idera.com/resourcecentral/videos/sql-safe-overview
[azure_youtube]: https://mva.microsoft.com/en-US/training-courses/is-your-lack-of-a-disaster-recovery-site-keeping-you-up-at-night-8680?l=oF7YrFH1_7504984382
[portworx_youtube]: https://www.youtube.com/channel/UCSexpvQ9esSRgiS_Q9_3mLQ 

<!--Twitter links-->
[veeam_twitter]:https://twitter.com/veeam
[dh2i_twitter]:https://twitter.com/dh2i
[hpe_twitter]:https://twitter.com/hpe
[azure_twitter]: https://twitter.com/hashtag/azuresiterecovery

<!--Docs links>-->
[portworx_docs]: http://docs.portworx.com/

<!--Download links-->
[hpe_download]: http://downloads.linux.hpe.com/SDR/project/sglx/sglx-beta/
