---
title: Поддерживаемые обновления версий и выпусков | Документы Майкрософт
ms.custom: ''
ms.date: 10/26/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- components [SQL Server], adding to existing installations
- versions [SQL Server], upgrading
- upgrading SQL Server, upgrades supported
- cross-language support
ms.assetid: 702359c4-6ca9-42a8-860c-a95a802898a1
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 4a245aab71292e1482bd5a17bd32a27bded640ab
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62775227"
---
# <a name="supported-version-and-edition-upgrades"></a>Поддерживаемые обновления версий и выпусков
  Можно обновить версии [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]и [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]. В этом разделе приведены поддерживаемые пути обновления данных версий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и поддерживаемые обновления выпусков [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)].  
  
## <a name="pre-upgrade-checklist"></a>Контрольный список действий перед обновлением  
  
-   Перед началом обновления выпуска [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до новой версии проверьте, поддерживаются ли используемые функции в версии, до которой производится обновление.  
  
-   Перед обновлением [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]включите проверку подлинности Windows для агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и проверьте необходимые настройки конфигурации по умолчанию: является ли учетная запись службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] членом группы системных администраторов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Для обновления до версии [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]необходимо наличие поддерживаемой операционной системы. Дополнительные сведения см. в разделе [Hardware and Software Requirements for Installing SQL Server 2014](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md).  
  
-   Обновление будет заблокировано, если компьютер ожидает перезагрузки.  
  
-   Обновление будет заблокировано, если не запущена служба установщика Windows.  
  
## <a name="unsupported-scenarios"></a>Неподдерживаемые сценарии  
  
-   Многоверсионные экземпляры в [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] не поддерживаются. Компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)], а также службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]и [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] должны иметь один и тот же номер версии для одного экземпляра [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
-   Межплатформенное обновление не поддерживается. Невозможно обновить 32-разрядный экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] до стандартного 64-разрядного при помощи программы установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Но можно создать резервную копию или отсоединить базы данных от 32-разрядного экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], а затем восстановить их или присоединить к новому экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (64-разрядная версия), если базы данных не опубликованы в репликации. Необходимо повторно создать имена входа и другие объекты пользователя в системных базах данных master, msdb и model.  
  
-   Добавить новые компоненты в процессе обновления существующего экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]нельзя. После обновления экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] добавить новые компоненты можно при помощи программы установки [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Дополнительные сведения см. в разделе [Добавление компонентов в экземпляр SQL Server 2014 &#40;установки&#41;](add-features-to-an-instance-of-sql-server-setup.md).  
  
-   Кластеры отработки отказа не поддерживаются в режиме WOW.  
  
-   Обновление с выпуска Evaluation предыдущей версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не поддерживается.  
  
## <a name="upgrades-from-earlier-versions-to-includesssql14includessssql14-mdmd"></a>Обновление ранних версий до [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]  
  
> [!NOTE]  
>  Поддержка [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] более подробно рассматривается в следующем разделе «Поддержка[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] в [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]».  
  
-   32-разрядные версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно обновить до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] в 32-разрядной подсистеме (WOW64) 64-разрядного сервера.  
  
-   64-разрядные версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно обновить до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] только на 64-разрядном сервере.  
  
> [!NOTE]  
>  При обновлении до [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] из предыдущей версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise edition, выбирать Enterprise Edition: Лицензирование и Enterprise Edition. Эти выпуски Enterprise отличаются только в отношении режима лицензирования и максимального количества поддерживаемых ядер. Дополнительные сведения см. в разделе [Compute Capacity Limits by Edition of SQL Server](../../sql-server/compute-capacity-limits-by-edition-of-sql-server.md).  
  
 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] поддерживает обновление со следующих версий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
-   [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] с пакетом обновления 4 (SP4) или более поздней версии  
  
-   [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] с пакетом обновления 3 (SP3) или более поздней версии  
  
-   [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]с пакетом обновления 2 (SP2) или более поздней версии  
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] с пакетом обновления 1 (SP1) или более поздние версии.  
  
 В таблице, представленной ниже, перечислены поддерживаемые сценарии обновления предыдущих версий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] до [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)].  
  
|Исходная версия|Поддерживаемые варианты обновления|  
|------------------|----------------------------|  
|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Enterprise с пакетом обновления 4 (SP4)|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence|  
|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Developer с пакетом обновления 4 (SP4)|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Developer|  
|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Standard с пакетом обновления 4 (SP4)|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Standard|  
|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Workgroup с пакетом обновления 4 (SP4)|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Standard|  
|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Express с пакетом обновления 4 (SP4),<br /><br /> [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Express с инструментами, пакетом обновления 4 (SP4) и<br /><br /> [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Express с дополнительными службами и пакетом обновления 4 (SP4)|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Standard<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Web<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Express|  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Enterprise с пакетом обновления 3 (SP3)|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence|  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Developer с пакетом обновления 3 (SP3)|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Developer|  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Standard с пакетом обновления 3 (SP3)|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Standard|  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Small Business|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Standard|  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Web с пакетом обновления 3 (SP3)|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Standard<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Web|  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Workgroup с пакетом обновления 3 (SP3)|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Standard|  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Express с пакетом обновления 3 (SP3),<br /><br /> [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Express с инструментами, пакетом обновления 3 (SP3) и<br /><br /> [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Express с дополнительными службами и пакетом обновления 3 (SP3)|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Standard<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Web<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Express|  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] Datacenter с пакетом обновления 2 (SP2)|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence|  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] Enterprise с пакетом обновления 2 (SP2)|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence|  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] Developer с пакетом обновления 2 (SP2)|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Developer|  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] Small Business с пакетом обновления 2 (SP2)|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Standard|  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] Standard с пакетом обновления 2 (SP2)|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Standard|  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] Web с пакетом обновления 2 (SP2)|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Standard<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Web|  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] Workgroup с пакетом обновления 2 (SP2)|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Standard|  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] Express с пакетом обновления 2 (SP2),<br /><br /> [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] Express с инструментами, пакетом обновления 2 (SP2) и<br /><br /> [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] Express с дополнительными службами и пакетом обновления 2 (SP2)|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Standard<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Web<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Express|  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Enterprise с пакетом обновления 1 (SP1)|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence|  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Developer с пакетом обновления 1 (SP1)|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Developer|  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Standard с пакетом обновления 1 (SP1)|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Standard|  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Web с пакетом обновления 1 (SP1)|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Standard<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Web|  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Express с пакетом обновления 1 (SP1),<br /><br /> [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP1 Express с инструментами, пакетом обновления 1 (SP1) и<br /><br /> [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Express Management Studio с пакетом обновления 1 (SP1) и<br /><br /> [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Express с дополнительными службами и пакетом обновления 1 (SP1)|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Standard<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Web<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Express|  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Business Intelligence с пакетом обновления 1 (SP1)|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence|  
  
### <a name="includesssql14includessssql14-mdmd-support-for-includessversion2005includesssversion2005-mdmd"></a>Поддержка [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] для [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]  
 В этом разделе описывается поддержка [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] для [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. В [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]вы сможете выполнить следующие действия.  
  
-   Обновить экземпляр Database Engine [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] до [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] , запустив программу установки [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] с помощью мастера установки или из командной строки.  
  
-   Присоединить базу данных служб [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] (файлы MDF и LDF) к экземпляру [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] компонента Database Engine.  
  
-   Восстановить базу данных [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] в экземпляре [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] компонента Database Engine.  
  
-   Обновить пакет [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] до [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]. Выполнить пакеты с автоматическим обновлением на месте.  
  
-   Обновить [!INCLUDE[ssASversion2005](../../includes/ssasversion2005-md.md)] до [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] , запустив программу установки [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] .  
  
-   Создать резервную копию куба [!INCLUDE[ssASversion2005](../../includes/ssasversion2005-md.md)] и восстановить его в [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)].  
  
-   Обновить [!INCLUDE[ssRSversion2005](../../includes/ssrsversion2005-md.md)] до [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] , запустив программу установки [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] .  
  
-   Подключитесь к [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]с помощью [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 2014.  
  
 Когда база данных [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] обновляется до версии [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], уровень совместимости базы данных будет изменен с 90 на 100. (В [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], допустимыми значениями уровня совместимости базы данных являются 100, 110 и 120.) В разделе [Уровень совместимости инструкции ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level) представлены сведения о том, как изменение уровня совместимости может повлиять на приложения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Все сценарии, не указанные в списке выше, не поддерживаются, включая в том числе следующие:  
  
-   Установка [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] на одном компьютере (параллельно).  
  
-   Использование экземпляра [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] в качестве члена топологии репликации, включающего экземпляр [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] .  
  
-   Зеркальное отображение базы данных между экземплярами [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] и [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] .  
  
-   Резервное копирование журнала транзакций с доставкой журналов между экземплярами [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] и [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] .  
  
-   Настройка связанных серверов между экземплярами [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] и [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] .  
  
-   Управление экземпляром [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] из среды [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Management Studio.  
  
-   Подключение куба [!INCLUDE[ssASversion2005](../../includes/ssasversion2005-md.md)] в [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Management Studio.  
  
-   Подключение к [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] в [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Management Studio.  
  
-   Управление службами [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] в [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Management Studio.  
  
-   Поддержка компонентов служб Integration Services [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] сторонних разработчиков, например выполнение и обновление.  
  
## <a name="includesssql14includessssql14-mdmd-edition-upgrade"></a>[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Обновление выпуска  
 В следующей таблице перечислены поддерживаемые сценарии обновлений в [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)].  
  
 Пошаговые инструкции по обновлению выпуска см. в разделе [обновить до разных выпуска SQL Server 2014 &#40;установки&#41;](upgrade-to-a-different-edition-of-sql-server-setup.md).  
  
|Исходная версия|Обновленная версия|  
|------------------|----------------|  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise (Server + CAL и Core) <sup>2</sup>|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence|  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise (лицензия Server+CAL или Core)|  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Evaluation Enterprise <sup>2</sup>|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise (лицензия Server+CAL или Core)<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Standard<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Developer<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Web<br /><br /> Обновление с переходом от Evaluation Enterprise (бесплатного выпуска) на любой из платных выпусков поддерживается для изолированных установок, но не поддерживается для кластеризованных установок.|  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Стандартный <sup>2</sup>|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise (лицензия Server+CAL или Core)|  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Разработчик <sup>2</sup>|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise (лицензия Server+CAL или Core)<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Web<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Standard|  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Web|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise (лицензия Server+CAL или Core)<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Standard|  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Express <sup>1</sup>|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise (лицензия Server+CAL или Core)<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Business Intelligence<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Developer<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Standard<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Web|  
  
 Кроме того, можно выполнить обновление выпуска между выпусками [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise (лицензия Server+CAL) и [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise (лицензия Core).  
  
|Обновление выпуска c|Обновление выпуска до|  
|--------------------------|------------------------|  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise (лицензия Server + CAL) <sup>2</sup>|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise (лицензия Core)|  
|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise (лицензия Core)|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Enterprise (лицензия Server+CAL)|  
  
 <sup>1</sup> также применяется к [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Express с инструментами и [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Express with Advanced Services.  
  
 <sup>2</sup> изменения выпуска [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] отказоустойчивого кластера ограничено. Следующие сценарии не поддерживаются для кластеров отработки отказа [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] .  
  
-   SQL Server 2014 Enterprise до SQL Server 2014 Developer, Standard и Enterprise Evaluation.  
  
-   SQL Server 2014 Developer до SQL Server 2014 Standard и Enterprise Evaluation.  
  
-   SQL Server 2014 Standard до SQL Server 2014 Enterprise Evaluation.  
  
-   SQL Server 2014 Enterprise Evaluation до SQL Server 2014 Standard.  
  
## <a name="see-also"></a>См. также  
 [Функции, поддерживаемые различными выпусками SQL Server 2014](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)   
 [Оборудованию и программному обеспечению для установки SQL Server 2014](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)   
 [Обновление до SQL Server 2014](upgrade-sql-server.md)   
 [Использование помощника по обновлению для подготовки к обновлениям](../../../2014/sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md)  
  
  
