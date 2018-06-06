---
title: Требования к оборудованию и программному обеспечению для установки SQL Server 2016 | Документация Майкрософт
ms.custom: ''
ms.date: 08/23/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: install
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Setup [SQL Server], software
- software [SQL Server]
- installing SQL Server, software
- operating systems [SQL Server], SQL Server requirements
- Setup [SQL Server], cross-language support
- operating systems [SQL Server], cross-language support
- network connections [SQL Server], requirements
- disk space [SQL Server], SQL Server installations
- WOW [SQL Server]
- Setup [SQL Server], hardware
- dependencies [SQL Server], SQL Server installations
- cluster hardware requirements [SQL Server]
- endpoints [SQL Server], SQL Server installations
- Internet [SQL Server], SQL Server installations
- hardware [SQL Server]
- Windows on Windows [SQL Server]
- installing SQL Server, hardware
- Setup Configuration Checker
- SCC [SQL Server]
- operating systems [SQL Server]
- space [SQL Server], SQL Server installations
- system configuration checker
- installing SQL Server, cross-language support
- Internet [SQL Server]
- space [SQL Server]
- extended system support [SQL Server]
- 64-bit edition [SQL Server]
- failover clustering [SQL Server]
- failover clustering [SQL Server], hardware requirements
- 32-bit edition [SQL Server]
- locales [SQL Server], SQL Server installations
- cross-language support
- disk space [SQL Server]
- localized SQL Server versions
ms.assetid: 09bcf20b-0a40-4131-907f-b61479d5e4d8
caps.latest.revision: 333
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: aef7f10021c179b8ab6a6498bbe251159b8bfe7a
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2018
ms.locfileid: "34773190"
---
# <a name="hardware-and-software-requirements-for-installing-sql-server"></a>Требования к оборудованию и программному обеспечению для установки SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этой статье приведены минимальные требования к оборудованию и программному обеспечению, необходимым для установки и запуска [!INCLUDE[ssNoVer](../../includes/ssnoversion-md.md)] в операционной системе Windows. 

В [!INCLUDE[sscurrent](../../includes/sssqlv14-md.md)] введена поддержка [!INCLUDE[ssNoVer](../../includes/ssnoversion-md.md)] в Linux. Дополнительные сведения см. в разделе [Требования к оборудованию и программному обеспечению для установки [!INCLUDE[ssNoVersion](../../includes/ssNoVersion_md.md)] в Linux](../../linux/sql-server-linux-setup.md#system). 

> Эта статья относится к [!INCLUDE[ss2016](../../includes/sssql15-md.md)] и более поздним версиям. Содержимое, связанное с предыдущих версий SQL Server, см. в разделе [Требования к оборудованию и программному обеспечению для установки SQL Server 2014](https://msdn.microsoft.com/library/ms143506(v=sql.120).aspx). 
  
**Попробуйте продукт:**  
  
-   Скачайте SQL Server в [**Центре Evaluation Center**.](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2016) 
  
-    Запустите виртуальную машину с уже установленным [**SQL Server 2016**](https://azure.microsoft.com/en-us/services/virtual-machines/sql-server/?wt.mc_id=sqL16_vm) .  
  
 **Следующие аспекты применяются ко всем выпускам.**  
  
-   Рекомендуется запускать [!INCLUDE[ssCurrent](../../includes/ssnoversion-md.md)] на компьютерах с файловой системой NTFS или ReFS. Установка [!INCLUDE[ssCurrent](../../includes/ssnoversion-md.md)] в файловой системе FAT32 поддерживается, но не рекомендуется, поскольку эта система менее защищена, чем NTFS или ReFS.  
  
-   Программа установки[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] заблокирует установку на диски со сжатием, сетевые диски и диски, доступные только для чтения.  
  
-   Установку не удастся выполнить, если запустить программу установки через удаленный рабочий стол, но носитель при этом будет расположен на клиенте RDC. Чтобы выполнить установку удаленно, установочный носитель должен быть расположен на общем сетевом ресурсе или в локальной папке физической или виртуальной машины. Установочный носитель[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может быть расположен на общем сетевом ресурсе, сопоставленном диске, локальном диске, или он может быть представлен в виде ISO-образа на виртуальной машине.  
  
-   Для установки [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] требуется платформа .NET 4.6.1. Платформа .NET 4.6.1 устанавливается автоматически, если выбран компонент [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] .  
  
-   Программа установки[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] устанавливает следующие компоненты, необходимые для продукта:  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Файлы поддержки программы установки  
  
-   Минимальные требования к версиям для установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в [!INCLUDE[win8srv](../../includes/win8srv-md.md)] или [!INCLUDE[win8](../../includes/win8-md.md)] см. в разделе [Установка SQL Server в Windows Server 2012 и Windows 8](http://support.microsoft.com/kb/2681562) (http://support.microsoft.com/kb/2681562).  
  
##  <a name="hwswr"></a> Требования к оборудованию и программному обеспечению  
Следующие требования относятся ко всем видам установки.  
  
|Компонент|Требование|  
|---------------|-----------------|  
|.NET Framework|Для установки[!INCLUDE[sql2016](../../includes/sssql15-md.md)] RC1 и более поздних версий требуется [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 4.6 для следующих компонентов: ядро СУБД, Master Data Services и репликация. Во время установки[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016 автоматически установится [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]. Также вы можете вручную установить [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] со страницы [Microsoft .NET Framework 4.6 (веб-установщик) для Windows](http://support.microsoft.com/kb/3045560).<br/><br/> Дополнительные сведения, рекомендации и руководство для платформы [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 4.6 см. в статье [Руководство по развертыванию .NET Framework для разработчиков](http://msdn.microsoft.com/library/ee942965\(v=vs.110\).aspx).<br/><br/>В[!INCLUDE[winblue_client_2](../../includes/winblue-client-2-md.md)]и [!INCLUDE[winblue_server_2](../../includes/winblue-server-2-md.md)] нужно установить обновление [KB2919355](http://support.microsoft.com/kb/2919355) перед установкой [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 4.6.|  
|Сетевое программное обеспечение|Поддерживаемые операционные системы для [!INCLUDE[ssCurrent](../../includes/ssnoversion-md.md)] содержат встроенное сетевое программное обеспечение. Именованные экземпляры и экземпляры по умолчанию изолированной установки поддерживают следующие сетевые протоколы: общая память, именованные каналы, TCP/IP и VIA.<br/><br/> Примечание. Общая память и протокол VIA не поддерживаются в отказоустойчивых кластерах.<br/><br/> Также стоит отметить, что протокол VIA является устаревшим. [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]<br/><br/> <br/><br/> Дополнительные сведения о сетевых протоколах и сетевых библиотеках см. в разделе [Network Protocols and Network Libraries](../../sql-server/install/network-protocols-and-network-libraries.md).|  
|Жесткий диск|Для[!INCLUDE[ssCurrent](../../includes/ssnoversion-md.md)] требуется как минимум 6 ГБ свободного места на диске.<br/><br/> Требования к месту на диске определяются набором устанавливаемых компонентов [!INCLUDE[ssCurrent](../../includes/ssnoversion-md.md)] . Дополнительные сведения см. в разделе [Требования к месту на диске](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md#HardDiskSpace) далее в этой статье. Сведения о поддерживаемых типах хранилищ для файлов данных см. в разделе [Storage Types for Data Files](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md#StorageTypes).|  
|Диск|Для установки с DVD-диска необходим соответствующий дисковод.|  
|Монитор|Для[!INCLUDE[ssCurrent](../../includes/ssnoversion-md.md)] требуется монитор Super VGA с разрешением 800x600 пикселей или более высоким.|  
|Интернет|Для поддержки функциональных средств Интернета требуется доступ к Интернету (могут применяться дополнительные тарифы).|  
  
 Примечание. Система [!INCLUDE[ssCurrent](../../includes/ssnoversion-md.md)] , будет работать медленнее на виртуальной машине, чем на физическом компьютере. Это связано с необходимостью поддержки виртуализации.  
  
 Для компонента PolyBase существуют дополнительные аппаратные и программные требования. Дополнительные сведения см. в разделе [Приступая к работе с PolyBase](../../relational-databases/polybase/get-started-with-polybase.md).  
  
##  <a name="pmosr"></a> Требования к процессору, памяти и операционной системе  
 Следующие требования к памяти и процессору применяются ко всем выпускам [!INCLUDE[ssCurrent](../../includes/ssnoversion-md.md)]:  
  
|Компонент|Требование|  
|---------------|-----------------|  
|Память *|**Минимальные:**<br/><br/> Экспресс-выпуски: 512 МБ<br/><br/> Все другие выпуски: 1 ГБ<br/><br/> **Рекомендуемые:**<br/><br/> Экспресс-выпуски: 1 ГБ<br/><br/> Все другие выпуски: для обеспечения оптимальной производительности требуется не менее 4 ГБ с последующим увеличением по мере роста размера базы данных.|  
|Быстродействие процессора|**Минимум** : процессор x64 с тактовой частотой 1,4 ГГц<br/><br/> **Рекомендуется:** 2,0 ГГц или выше|  
|Тип процессора|Процессор x64: AMD Opteron, AMD Athlon 64, Intel Xeon с поддержкой Intel EM64T, Intel Pentium IV с поддержкой EM64T.|  
  
> [!NOTE]  
>  Установка [!INCLUDE[ssCurrent](../../includes/ssnoversion-md.md)] поддерживается только для процессоров x64. Процессоры x86 больше не поддерживаются.  
  
 \* Минимальный объем оперативной памяти, необходимый для установки компонента [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] в [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] (DQS), составляет 2 ГБ. Это значение отличается от требований, предъявляемых к минимальному объему памяти [!INCLUDE[ssCurrent](../../includes/ssnoversion-md.md)]. Подробные сведения об установке DQS см. в разделе [Install Data Quality Services](../../data-quality-services/install-windows/install-data-quality-services.md).  
  
 **Поддержка WOW64:**  
  
 WOW64 (32-разрядная Windows в 64-разрядной Windows) — это компонент 64-разрядных выпусков Windows, который позволяет выполнять 32-разрядные приложения в собственном 32-разрядном режиме. Приложения работают в 32-разрядном режиме даже в случае, если базовая операционная система является 64-разрядной. Режим WOW64 не поддерживается для установок [!INCLUDE[ssCurrent](../../includes/ssnoversion-md.md)] . Тем не менее в режиме WOW64 могут работать средства управления.  
  
 **Поддержка операционных систем:**  
  
 Выпуски [!INCLUDE[ssCurrent](../../includes/ssnoversion-md.md)] классифицируются следующим образом:  
  
-   [Основные выпуски](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md#TOP_Principal)  
  
-   [Дополнительные выпуски](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md#TOP_Breadth)  
  
> [!NOTE]  
>  Поддержка операционных систем, указанных в этом разделе, не распространяется на следующие компоненты бизнес-аналитики для SQL Server 2016 и более ранних версий. Эти компоненты можно установить на Windows Server 2008 R2 с пакетом обновления 1 (SP1) или более поздней версии.  
>  
>-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] — SharePoint  
> 
>-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Надстройка для продуктов SharePoint  
  
### <a name="features-supported-on-32-bit-client-operating-systems"></a>Функции, поддерживаемые в 32-разрядных клиентских операционных системах  
 Клиентские операционные системы Windows, такие как Windows 10 и Windows 8.1, могут иметь 32-разрядную или 64-разрядную архитектуру.   Полная поддержка всех функций SQL Server доступна только в 64-разрядных операционных системах. В поддерживаемых 32-разрядных операционных системах Microsoft поддерживаются следующие функции:  
  
-   Клиент Data Quality  
  
-   Средства связи клиентских средств  
  
-   Службы Integration Services  
  
-   Обратная совместимость клиентских средств  
  
-   Пакет SDK клиентских средств  
  
-   Компоненты документации  
  
-   Компоненты распределенного воспроизведения  
  
-   Контроллер распределенного воспроизведения  
  
-   Клиент распределенного воспроизведения  
  
-   Пакет SDK для подключения клиентов SQL  
  
 [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] и серверные операционные системы более поздней версии не поддерживают 32-разрядную архитектуру. Все поддерживаемые серверные операционные системы доступны только с 64-разрядной архитектурой. Полная поддержка всех функций доступна только в 64-разрядных серверных операционных системах.  
  
###  <a name="TOP_Principal"></a> Principal Editions of [!INCLUDE[ssCurrent](../../includes/ssnoversion-md.md)]  
 В следующей таблице перечислены требования к операционной системе для основных выпусков [!INCLUDE[ssCurrent](../../includes/ssnoversion-md.md)]:  
  
|Выпуск[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] |Поддерживаемые операционные системы|  
|---------------------------------------|--------------------------------|  
|[!INCLUDE[ssEnterprise](../../includes/ssenterprise-md.md)]|[!INCLUDE[winserver2016_datacenter_md](../../includes/winserver2016-datacenter-md.md)]<br/><br/>[!INCLUDE[winserver2016_standard_md](../../includes/winserver2016-standard-md.md)]<br/><br/>[!INCLUDE[winserver2016_essentials_md](../../includes/winserver2016-essentials-md.md)]* <br/><br/>[!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Datacenter<br/><br/>[!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Standard<br/><br/>[!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Essentials<br/><br/>[!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Foundation<br/><br/>[!INCLUDE[win8srv](../../includes/win8srv-md.md)] Datacenter<br/><br/>[!INCLUDE[win8srv](../../includes/win8srv-md.md)] Standard<br/><br/>[!INCLUDE[win8srv](../../includes/win8srv-md.md)] Essentials<br/><br/>[!INCLUDE[win8srv](../../includes/win8srv-md.md)] Foundation|  
|[!INCLUDE[ssStandard](../../includes/ssstandard-md.md)]|[!INCLUDE[winserver2016_datacenter_md](../../includes/winserver2016-datacenter-md.md)]<br/><br/>[!INCLUDE[winserver2016_standard_md](../../includes/winserver2016-standard-md.md)]<br/><br/>[!INCLUDE[winserver2016_essentials_md](../../includes/winserver2016-essentials-md.md)]* <br/><br/>[!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Datacenter<br/><br/>[!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Standard<br/><br/>[!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Essentials<br/><br/>[!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Foundation<br/><br/>[!INCLUDE[win8srv](../../includes/win8srv-md.md)] Datacenter<br/><br/>[!INCLUDE[win8srv](../../includes/win8srv-md.md)] Standard<br/><br/>[!INCLUDE[win8srv](../../includes/win8srv-md.md)] Essentials<br/><br/>[!INCLUDE[win8srv](../../includes/win8srv-md.md)] Foundation<br/><br/> Windows 10 Домашняя<br/><br/> Windows 10 Профессиональная<br/><br/> Windows 10 Корпоративная<br/><br/>Windows 10 IoT Корпоративная<br/><br/>[!INCLUDE[winblue_client_2](../../includes/winblue-client-2-md.md)]<br/><br/>[!INCLUDE[winblue_client_pro_2](../../includes/winblue-client-pro-2-md.md)]<br/><br/>[!INCLUDE[winblue_client_ent_2](../../includes/winblue-client-ent-2-md.md)]<br/><br/>[!INCLUDE[win8](../../includes/win8-md.md)]<br/><br/>[!INCLUDE[win8_client_pro_2](../../includes/win8-client-pro-2-md.md)]<br/><br/>[!INCLUDE[win8_client_ent_2](../../includes/win8-client-ent-2-md.md)]|  
|[!INCLUDE[ssWeb](../../includes/ssweb-md.md)]|[!INCLUDE[winserver2016_datacenter_md](../../includes/winserver2016-datacenter-md.md)]<br/><br/>[!INCLUDE[winserver2016_standard_md](../../includes/winserver2016-standard-md.md)]<br/><br/>[!INCLUDE[winserver2016_essentials_md](../../includes/winserver2016-essentials-md.md)]* <br/><br/>[!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Datacenter<br/><br/>[!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Standard<br/><br/>[!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Essentials<br/><br/>[!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Foundation<br/><br/>[!INCLUDE[win8srv](../../includes/win8srv-md.md)] Datacenter<br/><br/>[!INCLUDE[win8srv](../../includes/win8srv-md.md)] Standard<br/><br/>[!INCLUDE[win8srv](../../includes/win8srv-md.md)] Essentials<br/><br/>[!INCLUDE[win8srv](../../includes/win8srv-md.md)] Foundation|  
  
\* Не поддерживается для [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].
  
###  <a name="TOP_Breadth"></a> Дополнительные выпуски [!INCLUDE[ssCurrent](../../includes/ssnoversion-md.md)]  
 В следующей таблице перечислены требования к операционной системе для дополнительных выпусков [!INCLUDE[ssCurrent](../../includes/ssnoversion-md.md)]:  
  
|Выпуск[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] |Поддерживаемые операционные системы|  
|---------------------------------------|--------------------------------|  
|[!INCLUDE[ssDeveloper](../../includes/ssdeveloper-md.md)]|[!INCLUDE[winserver2016_datacenter_md](../../includes/winserver2016-datacenter-md.md)]<br/><br/>[!INCLUDE[winserver2016_standard_md](../../includes/winserver2016-standard-md.md)]<br/><br/>[!INCLUDE[winserver2016_essentials_md](../../includes/winserver2016-essentials-md.md)]* <br/><br/>[!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Datacenter<br/><br/>[!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Standard<br/><br/>[!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Essentials<br/><br/>[!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Foundation<br/><br/>[!INCLUDE[win8srv](../../includes/win8srv-md.md)] Datacenter<br/><br/>[!INCLUDE[win8srv](../../includes/win8srv-md.md)] Standard<br/><br/>[!INCLUDE[win8srv](../../includes/win8srv-md.md)] Essentials<br/><br/>[!INCLUDE[win8srv](../../includes/win8srv-md.md)] Foundation<br/><br/> Windows 10 Домашняя<br/><br/> Windows 10 Профессиональная<br/><br/> Windows 10 Корпоративная<br/><br/>Windows 10 IoT Корпоративная<br/><br/>[!INCLUDE[winblue_client_2](../../includes/winblue-client-2-md.md)]<br/><br/>[!INCLUDE[winblue_client_pro_2](../../includes/winblue-client-pro-2-md.md)]<br/><br/>[!INCLUDE[winblue_client_ent_2](../../includes/winblue-client-ent-2-md.md)]<br/><br/>[!INCLUDE[win8](../../includes/win8-md.md)]<br/><br/>[!INCLUDE[win8_client_pro_2](../../includes/win8-client-pro-2-md.md)]<br/><br/>[!INCLUDE[win8_client_ent_2](../../includes/win8-client-ent-2-md.md)]|  
|[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]|[!INCLUDE[winserver2016_datacenter_md](../../includes/winserver2016-datacenter-md.md)]<br/><br/>[!INCLUDE[winserver2016_standard_md](../../includes/winserver2016-standard-md.md)]<br/><br/>[!INCLUDE[winserver2016_essentials_md](../../includes/winserver2016-essentials-md.md)]* <br/><br/>[!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Datacenter<br/><br/>[!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Standard<br/><br/>[!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Essentials<br/><br/>[!INCLUDE[win8srv](../../includes/win8srv-md.md)] R2 Foundation<br/><br/>[!INCLUDE[win8srv](../../includes/win8srv-md.md)] Datacenter<br/><br/>[!INCLUDE[win8srv](../../includes/win8srv-md.md)] Standard<br/><br/>[!INCLUDE[win8srv](../../includes/win8srv-md.md)] Essentials<br/><br/>[!INCLUDE[win8srv](../../includes/win8srv-md.md)] Foundation<br/><br/> Windows 10 Домашняя<br/><br/> Windows 10 Профессиональная<br/><br/> Windows 10 Корпоративная<br/><br/>Windows 10 IoT Корпоративная<br/><br/>[!INCLUDE[winblue_client_2](../../includes/winblue-client-2-md.md)]<br/><br/>[!INCLUDE[winblue_client_pro_2](../../includes/winblue-client-pro-2-md.md)]<br/><br/>[!INCLUDE[winblue_client_ent_2](../../includes/winblue-client-ent-2-md.md)]<br/><br/>[!INCLUDE[win8](../../includes/win8-md.md)]<br/><br/>[!INCLUDE[win8_client_pro_2](../../includes/win8-client-pro-2-md.md)]<br/><br/>[!INCLUDE[win8_client_ent_2](../../includes/win8-client-ent-2-md.md)]|  

\* Не поддерживается для [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].
  
##  <a name="CrossLanguageSupport"></a> Поддержка версий на разных языках  
 Дополнительные сведения о поддержке версий на разных языках и рекомендации по установке локализованных версий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] см. в разделе [Версии SQL Server на местных языках](../../sql-server/install/local-language-versions-in-sql-server.md).  
  
##  <a name="HardDiskSpace"></a> Требования к месту на диске  
 Во время установки [!INCLUDE[ssCurrent](../../includes/ssnoversion-md.md)]установщик Windows создает временные файлы на системном диске. Прежде чем запускать программу для установки или обновления версии до [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], проверьте, что на системном диске доступно не менее 6,0 ГБ свободного места для устанавливаемых файлов. Это требование должно быть выполнено даже в том случае, если компоненты [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] устанавливаются на диск, отличный от предложенного по умолчанию.  
  
 Фактические требования к объему свободного места на диске зависят от конфигурации системы, а также от набора устанавливаемых компонентов. В следующей таблице представлены требования к свободному месту на диске для компонентов [!INCLUDE[ssCurrent](../../includes/ssnoversion-md.md)] .  
  
|**Компонент**|**Свободное место на диске**|  
|-----------------|--------------------------------|  
|Компонент[!INCLUDE[ssDE](../../includes/ssde-md.md)] и файлы данных, репликация, полнотекстовый поиск и службы Data Quality Services|1480 МБ|  
|[!INCLUDE[ssDE](../../includes/ssde-md.md)] (как описано выше) со службами R Services (в базе данных)|2744 МБ|  
|[!INCLUDE[ssDE](../../includes/ssde-md.md)] (как описано выше) со службой запросов PolyBase для внешних данных|4194 МБ|  
|Службы[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] и файлы данных|698 МБ|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|967 МБ|  
|[!INCLUDE[rsql_platform](../../includes/rsql-platform-md.md)] (автономный)|280 МБ|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] — SharePoint|1203 МБ|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Надстройка для продуктов SharePoint|325 МБ|  
|[!INCLUDE[ssDQSClient](../../includes/ssdqsclient-md.md)]|121 МБ|  
|Средства связи клиентских средств|328 МБ|  
|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]|306 МБ|  
|Клиентские компоненты (кроме компонентов электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и служб Integration Services)|445 МБ|  
|[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]|280 МБ|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Компоненты электронной документации для просмотра и управления содержимым справки*|27 МБ|  
|Все компоненты|8030 МБ|  
  
 *Требование к месту на диске для загружаемого содержимого электронной документации — 200 МБ.  
  
##  <a name="StorageTypes"></a> Типы хранилищ для файлов данных  
 Для файлов данных поддерживаются следующие типы хранилищ.  
  
-   Локальный диск  
  
-   Общее хранилище  

-   [Локальные дисковые пространства \(S2D\)](https://technet.microsoft.com/windows-server-docs/storage/storage-spaces/storage-spaces-direct-overview)
  
-   Общая папка SMB  
  
    > [!NOTE]  
    >  Хранилище SMB не поддерживается для файлов данных автономных или кластерных установок служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Используйте вместо него непосредственно подключенное хранилище, сеть хранения данных или S2D.  
  
    > [!IMPORTANT]  
    >  Хранилище SMB может размещаться на файловом сервере Windows или на устройстве с хранилищем SMB сторонних разработчиков. Если используется файловый сервер Windows, он должен иметь версию 2008 или последующую. Дополнительные сведения об установке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с общей папкой SMB в качестве хранилища см. в разделе [Install SQL Server with SMB Fileshare as a Storage Option](../../database-engine/install-windows/install-sql-server-with-smb-fileshare-as-a-storage-option.md).  
  
    > [!WARNING]  
    >  Установка кластера отработки отказа[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает локальные диски только для установки файлов tempdb. Проверьте правильность пути, указанного для файлов tempdb и файлов журнала на всех узлах кластера. Если во время отработки отказа каталоги tempdb недоступны на целевом узле отработки отказа, то при переводе ресурсов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в режим «в сети» произойдет ошибка.  
  
##  <a name="DC_support"></a> Установка [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на контроллере домена  
 Исходя из соображений безопасности, не рекомендуется устанавливать [!INCLUDE[ssCurrent](../../includes/ssnoversion-md.md)] на контроллере домена. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не заблокирует установку на компьютере, который является контроллером домена, однако при этом будут применены следующие ограничения.  
  
-   Запуск служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на контроллере домена в учетной записи локальной службы невозможен.  
  
-   После установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] компьютер, который является членом домена, нельзя будет сделать контроллером домена. Перед этим придется удалить [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   После установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] компьютер, который является контроллером домена, нельзя будет сделать членом домена. Перед этим придется удалить [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не поддерживает экземпляры отказоустойчивого кластера, где узлы кластера являются контроллерами домена.  
  
- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не поддерживается на контроллере домена только для чтения. Программа установки[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не может создавать группы безопасности или подготавливать учетные записи служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на контроллере домена, доступном только для чтения. В такой ситуации программа установки завершается ошибкой.  

- Экземпляр отказоустойчивого кластера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не поддерживается в среде, где доступен только контроллер домена только для чтения. 
  
## <a name="see-also"></a>См. также:  
 [Планирование установки SQL Server](../../sql-server/install/planning-a-sql-server-installation.md)   
 [Вопросы безопасности при установке SQL Server](../../sql-server/install/security-considerations-for-a-sql-server-installation.md)   
 [Спецификации SQL Server 2016](http://msdn.microsoft.com/library/6445fd53-6844-4170-a86b-7fe76a9f64cb)  
  
  
