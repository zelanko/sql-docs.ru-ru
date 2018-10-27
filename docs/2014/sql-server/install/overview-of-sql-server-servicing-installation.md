---
title: Общие сведения об обслуживании установки SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 6a9fd19b-2367-4908-b638-363b1e929e1e
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ab2ef4879ae4c29c43bfa07c0ccf314eae51ff39
ms.sourcegitcommit: 9f2edcdf958e6afce9a09fb2e572ae36dfe9edb0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/25/2018
ms.locfileid: "50100215"
---
# <a name="overview-of-sql-server-servicing-installation"></a>Общие сведения об обслуживании установки SQL Server
  Можно обновить любой установленный компонент [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], применив сервисное обновление [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Если версия существующего компонента [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] новее, чем версия обновления, то программа установки исключит этот компонент из списка обновления. Дополнительные сведения о применении сервисного обновления, см. в разделе [установить SQL Server 2014 обновлений для обслуживания](../../database-engine/install-windows/install-sql-server-servicing-updates.md).  
  
 При установке обновлений для [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] необходимо учитывать следующие соображения.  
  
-   Все компоненты, которые принадлежат одному экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], должны обновляться одновременно. Например, если обновляется компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)], также необходимо обновить службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] и [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], если они установлены в качестве части того же экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Общие компоненты, такие как средства управления, среда [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] и службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], всегда должны быть обновлены до самой последней версии. Если компонент или экземпляр не выбран в дереве компонентов, то он не будет обновлен.  
  
-   По умолчанию [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] файлы журнала обновления сохраняются в папку % Program Files %\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\LOG\\.  
  
-   Теперь в программе установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обновление может быть интегрировано с исходным носителем, что позволяет выполнять обновление одновременно с запуском исходного носителя. Дополнительные сведения см. в разделе [новые возможности установки SQL Server](../../../2014/sql-server/install/what-s-new-in-sql-server-installation.md).  
  
-   Прежде чем применять сервисное обновление [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , рекомендуется создать резервную копию данных.  
  
-   Обновления [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] доступны через Центр обновления [!INCLUDE[msCoName](../../includes/msconame-md.md)]. Чтобы поддерживать надлежащий уровень обновления и защищенности экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], рекомендуется регулярно проверять наличие обновлений. Пакет обновления [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 1 (SP1) предоставляется как полная установка [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. В этом выпуске вместо пакета обновления в стандартном выполняемом пакете обновления для экземпляров [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] RTM предоставляется установочный пакет, состоящий из двух файлов. При его выполнении будет установлен новый экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с предустановленным пакетом обновления 1 (SP1).  
  
## <a name="requirements-and-known-issues"></a>Требования и известные проблемы  
 Для загрузки и извлечения пакета рекомендуется, чтобы объем свободного места на диске превышал размер пакета примерно в 2,5 раза. После установки пакета обновления загруженный пакет можно удалить с компьютера. Любые временные файлы будут удалены автоматически.  
  
 **Ознакомьтесь с известными проблемами.** Дополнительные сведения об известных проблемах текущего выпуска см. в соответствующем разделе заметок о выпуске: [Заметки о выпуске SQL Server](http://msdn.microsoft.com/f617a0af-92dd-47aa-82c3-f51b1346bcd8).  
  
## <a name="installation-overview"></a>Общие сведения об установке  
 В этом разделе описывается установка накопительных обновлений и пакетов обновлений для [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], включая описание следующих действий:  
  
-   подготовка к установке обновлений для [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)];  
  
-   установка обновлений [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
-   перезапуск служб и приложений  
  
### <a name="prepare-for-a-includesscurrentincludessscurrent-mdmd-update-installation"></a>подготовка к установке обновлений для [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
 Настоятельно рекомендуется до установки обновлений [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] выполнить следующие действия.  
  
-   **Резервное копирование вашей [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] системных баз данных** — перед установкой [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] обновления, резервное копирование `master`, `msdb`, и `model` баз данных. При установке обновления [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] эти базы данных изменяются, при этом они становятся несовместимыми с более ранними версиями [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Резервные копии этих баз данных понадобятся в случае, если будет принято решение переустановить [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] без этих обновлений.  
  
     Разумно также создать резервные копии пользовательских баз данных.  
  
    > [!IMPORTANT]  
    >  Перед установкой обновлений для экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], участвующих в топологии репликации, необходимо создать резервные копии реплицируемых баз данных наряду с системными базами данных.  
  
-   **Резервное копирование баз данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], файла конфигурации и репозитория** — перед обновлением экземпляра служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] создайте резервные копии следующих объектов.  
  
    -   Базы данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. По умолчанию они устанавливаются в C:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSAS12.\< Ид_экземпляра > \OLAP\Data\\. Для установок WOW по умолчанию путь — C:\ProgramFiles (x86) \ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSAS12.\< Ид_экземпляра > \OLAP\Data\\.  
  
    -   Параметр конфигурации служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в файле конфигурации msmdsrv.ini. По умолчанию этот файл находится в папке C:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSAS12.\< InstanceID > \OLAP\Config\ каталога.  
  
    -   База данных, содержащая репозиторий служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] (необязательно). Этот шаг необходим только в случае, если службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] были настроены для работы с библиотекой объектов DSO.  
  
    > [!NOTE]  
    >  Если не создать резервные копии файла конфигурации, репозитория и баз данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , вернуть обновленный экземпляр служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] к более ранней версии будет невозможно.  
  
-   **Убедитесь в наличии достаточного свободного места в системных базах данных** — Если не выбран параметр автоувеличения для `master` и `msdb` системных баз данных, эти базы данных каждый должен иметь минимум 500 КБ свободного места. Чтобы убедиться, что в базах данных достаточно свободного пространства, запустите системную хранимую процедуру `sp_spaceused` в базах данных `master` и `msdb`. Если размер свободного места в какой-либо из этих баз данных составляет менее 500 КБ, увеличьте ее размер.  
  
-   **Остановка служб и приложений**. Чтобы избежать перезапуска системы, остановите все приложения и службы, которые устанавливают соединения с обновляемыми экземплярами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], прежде чем устанавливать обновления для [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Это также касается среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] и [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Дополнительные сведения см. в статье [Запуск, остановка, приостановка, возобновление и перезапуск ядра СУБД, агента SQL Server и обозревателя SQL Server](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md).  
  
    > [!NOTE]  
    >  В среде с отказоустойчивым кластером нельзя останавливать службы. Дополнительные сведения см. в подразделе, посвященном установке отказоустойчивого кластера, далее в этом разделе.  
  
-   Чтобы устранить необходимость в перезагрузке компьютера после установки обновления, программа установки отобразит список процессов, блокирующих файлы. Если программе установки обновления необходимо остановить работу службы во время установки, эта служба будет перезапущена после завершения установки.  
  
-   Если программа установки обнаруживает заблокированные файлы во время установки, может возникнуть необходимость в перезагрузке компьютера после завершения установки. При необходимости программа установки предложит пользователю перезагрузить компьютер.  
  
### <a name="install-includesscurrentincludessscurrent-mdmd-updates"></a>Установка обновлений [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
 В этом разделе описан процесс установки.  
  
> [!IMPORTANT]  
>  Обновления для [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] должны запускаться от имени учетной записи, обладающей правами администратора на компьютере, где устанавливаются обновления. Для локальных установок необходимо запускать программу установки с правами администратора. При установке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] из удаленной общей папки необходимо использовать учетную запись домена с разрешениями на чтение и выполнение для удаленной общей папки.  
  
#### <a name="starting-a-includesscurrentincludessscurrent-mdmd-update"></a>Начало обновления [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
 Чтобы установить обновление [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , запустите файл самоизвлекающегося пакета.  
  
 Накопительный пакет обновления (CU): \<SQLServer2014 > - KBxxxxxx -*PPP*.exe  
  
 Пакет обновления (PCU): \<SQLServer2014 >\<SPx > - KBxxxxxx-PPP-LLL.exe  
  
-   x указывает номер пакета обновления.  
  
-   PPP указывает конкретную платформу.  
  
-   LLL обозначает буквенный код языка [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Например, LLL для английского языка ― ENU.  
  
 Сведения об установке обновлений для компонентов [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , входящих в состав кластера отработки отказа, см. в подразделе по установке кластера отработки отказа. Дополнительные сведения об установке обновлений в автоматическом режиме см. в разделе [Установка SQL Server 2014 из командной строки](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md).  
  
####  <a name="Slipstream"></a> Обновления продуктов в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] установки  
 Обновление продукта — это функция в программе установки [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] . Она интегрирует последние обновления продукта в основную установку продукта, чтобы он и все применимые обновления устанавливались одновременно. Функция обновления продукта может искать применимые обновления в центре обновления [!INCLUDE[msCoName](../../includes/msconame-md.md)], в службах Windows Server Update Services (WSUS), в локальной папке или в сетевой папке.  Когда программа установки обнаруживает последние версии соответствующих обновлений, эти обновления загружаются и интегрируются в текущую процедуру установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Функция обновления продукта может включить в установку пакет обновления, накопительное обновление или и то и другое. Функция обновления продукта является расширением функции Slipstream, которая была доступна в [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] PCU1.  
  
## <a name="updating-a-prepared-image-of-includessnoversionincludesssnoversion-mdmd"></a>Обновление подготовленного образа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 Можно применить обновление к ненастроенному подготовленному экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] без завершения настройки подготовленного экземпляра. Различные способы обновления подготовленного экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] приведены далее.  
  
-   Обновление ранее подготовленного экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
     Обновления к подготовленному экземпляру можно применить до настройки. Пакет обновления обнаруживает, что экземпляр находится в состоянии подготовки, и применяет обновление к подготовленному экземпляру, не завершая настройку.  
  
-   Обновления подготовленного экземпляра с помощью Центра обновления [!INCLUDE[msCoName](../../includes/msconame-md.md)]:  
  
     Обновления можно применять к подготовленному экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью Центра обновления [!INCLUDE[msCoName](../../includes/msconame-md.md)]. Пакет обновления Центра обновления [!INCLUDE[msCoName](../../includes/msconame-md.md)] обнаруживает, что экземпляр находится в состоянии подготовки и применяет обновление к подготовленному экземпляру, не завершая настройку.  
  
 При обновлении подготовленного образа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] необходимо указать параметр InstanceID. Дополнительные сведения и примеры синтаксиса см. в разделе [Установка обновлений из командной строки](../../database-engine/install-windows/installing-updates-from-the-command-prompt.md).  
  
## <a name="updating-a-completed-image-of-includessnoversionincludesssnoversion-mdmd"></a>Обновление завершенного образа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 Обновление завершенного и настроенного экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполняется аналогично, с использованием тех же процессов, что и обновление других установленных экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="rebuilding-a-includesscurrentincludessscurrent-mdmd-failover-cluster-node"></a>Перестроение узла кластера отработки отказа [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
 Если после установки обновлений необходимо перестроить узел в кластере отработки отказа, выполните следующие действия.  
  
1.  Перестройте узел в отказоустойчивом кластере. Дополнительные сведения о перестроении узла см. в разделе [Восстановление по журналу после сбоя экземпляра кластера отработки отказа](../failover-clusters/windows/recover-from-failover-cluster-instance-failure.md).  
  
2.  Запустите исходную программу установки [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], чтобы установить [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] на узле кластера отработки отказа.  
  
3.  Запустите программу установки обновлений для [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] на добавленном узле.  
  
## <a name="restart-services-and-applications"></a>перезапуск служб и приложений  
 После завершения установки может появиться запрос на перезагрузку компьютера. После перезагрузки системы или после завершения программы установки без запроса на перезагрузку используйте на панели управления средство **Службы**, чтобы перезапустить службы, остановленные перед установкой обновлений для [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. В частности, к их числу относятся координатор распределенных транзакций и служба поиска [!INCLUDE[msCoName](../../includes/msconame-md.md)] или их эквиваленты для данного экземпляра.  
  
 Перезапустите приложения, закрытые перед запуском программы установки обновлений для [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Можно также создать дополнительные резервные копии обновленных баз данных `master`, `msdb` и `model` сразу после успешной установки.  
  
## <a name="uninstalling-updates-from-includesscurrentincludessscurrent-mdmd"></a>Удаление обновлений из [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
 Удаление накопительных обновлений и пакетов обновлений для [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] можно выполнить через элемент на панели управления **Установка и удаление программ** . Чтобы просмотреть список установленных обновлений, откройте диалоговое окно "Установленные обновления". Для этого нажмите кнопку **Пуск** , выберите **Панель управления**, **Программы**, затем в разделе **Программы и компоненты** **Просмотр установленных обновлений**. Каждое накопительное обновление указывается отдельной строкой. Однако если установлен пакет обновления, версия которого выше накопительного обновления, то элементы накопительного обновления будут скрыты и станут доступными только при удалении пакета обновления.  
  
 Удаление обновлений и пакетов обновления производят от самого последнего примененного на экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и к более ранним. В каждом и приведенных ниже примеров после удаления всех обновлений и пакетов обновления на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] остается только с накопительным обновлением 1.  
  
-   У экземпляра [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с установленным накопительным обновлением 1 и пакетом обновления 1 (SP1) удалите пакет обновления 1 (SP1).  
  
-   У экземпляра [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с накопительным обновлением 1, пакетом обновления 1 (SP1) и накопительным обновлением 2 удалите сначала накопительное обновление 2, затем пакет обновления 1 (SP1).  
  
## <a name="see-also"></a>См. также  
 [Установка SQL Server 2014 из командной строки](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md)   
 [Установка обновлений обслуживания SQL Server 2014](../../database-engine/install-windows/install-sql-server-servicing-updates.md)   
 [Проверка установки SQL Server](../../database-engine/install-windows/validate-a-sql-server-installation.md)   
 [Просмотр и чтение файлов журналов программы установки SQL Server](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)  
  
  
