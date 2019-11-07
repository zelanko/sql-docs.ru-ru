---
title: Требования к оборудованию и программному обеспечению для установки SQL Server | Документация Майкрософт
ms.custom: sqlfreshmay19
ms.date: 11/04/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: install
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
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 88ed55a3c2890864e3e9623f3fa53ca3e747350c
ms.sourcegitcommit: 830149bdd6419b2299aec3f60d59e80ce4f3eb80
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/04/2019
ms.locfileid: "73536182"
---
# <a name="hardware-and-software-requirements-for-installing-sql-server"></a>Требования к оборудованию и программному обеспечению для установки SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этой статье приведены минимальные требования к оборудованию и программному обеспечению, необходимым для установки и запуска [!INCLUDE[ssNoVer](../../includes/ssnoversion-md.md)] в операционной системе Windows.

[!INCLUDE[sscurrent](../../includes/sssqlv14-md.md)] впервые реализует поддержку [!INCLUDE[ssNoVer](../../includes/ssnoversion-md.md)] в Linux. Дополнительные сведения см. в разделе [Требования к оборудованию и программному обеспечению для установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в Linux](../../linux/sql-server-linux-setup.md#system). 

**Попробуйте продукт:**  
  
- Скачайте SQL Server в [**Центре Evaluation Center**.](https://www.microsoft.com/evalcenter/evaluate-sql-server-2019-rc) 
  
<!-- 
- Spin up a Virtual Machine with [**SQL Server 2017**](https://azure.microsoft.com/services/virtual-machines/sql-server/?wt.mc_id=sqL16_vm) already installed.  
-->
  
**Следующие аспекты применяются ко всем выпускам.**  
  
- Программа установки[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] заблокирует установку на диски со сжатием, сетевые диски и диски, доступные только для чтения.  
  
- Установку не удастся выполнить, если запустить программу установки через удаленный рабочий стол, но носитель при этом будет расположен на клиенте RDC. Чтобы выполнить установку удаленно, установочный носитель должен быть расположен на общем сетевом ресурсе или в локальной папке физической или виртуальной машины. Установочный носитель[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может быть расположен на общем сетевом ресурсе, сопоставленном диске, локальном диске, или он может быть представлен в виде ISO-образа на виртуальной машине.
- Программа установки[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] устанавливает следующие компоненты, необходимые для продукта:  
  
    - [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client  
  
    - [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Файлы поддержки программы установки  

##  <a name="hwswr"></a> Требования к оборудованию и программному обеспечению  
Следующие требования относятся ко всем видам установки.  
  
|Компонент|Требование|  
|---------------|-----------------|  
|Операционная система|Windows 10 TH1 1507 или более поздней версии<br/><br>Windows Server 2016 или более поздней версии<br/><br/>
|.NET Framework|Минимальная версия операционной системы подразумевает минимальную версию платформы .NET Framework.|  
|Сетевое программное обеспечение|Поддерживаемые операционные системы для [!INCLUDE[ssCurrent](../../includes/ssnoversion-md.md)] содержат встроенное сетевое программное обеспечение. Именованные экземпляры и экземпляры по умолчанию изолированной установки поддерживают следующие сетевые протоколы: Shared memory, Named Pipes и TCP/IP.<br/><br/> |  
|Жесткий диск|Для[!INCLUDE[ssCurrent](../../includes/ssnoversion-md.md)] требуется как минимум 6 ГБ свободного места на диске.<br/><br/> Требования к месту на диске определяются набором устанавливаемых компонентов [!INCLUDE[ssCurrent](../../includes/ssnoversion-md.md)] . Дополнительные сведения см. в разделе [Требования к месту на диске](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md#HardDiskSpace) далее в этой статье. Сведения о поддерживаемых типах хранилищ для файлов данных см. в разделе [Storage Types for Data Files](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md#StorageTypes).|  
|Монитор|Для[!INCLUDE[ssCurrent](../../includes/ssnoversion-md.md)] требуется монитор Super VGA с разрешением 800x600 пикселей или более высоким.|  
|Интернет|Для поддержки функциональных средств Интернета требуется доступ к Интернету (могут применяться дополнительные тарифы).|  

> [!NOTE]
> Система [!INCLUDE[ssCurrent](../../includes/ssnoversion-md.md)], запущенная в виртуальной машине, будет работать медленнее, чем в физической, в связи с необходимостью поддержки виртуализации.  

> [!IMPORTANT]
> Для компонента PolyBase существуют дополнительные аппаратные и программные требования. Дополнительные сведения см. в разделе [Приступая к работе с PolyBase](../../relational-databases/polybase/get-started-with-polybase.md).  
  
##  <a name="pmosr"></a> Требования к процессору, памяти и операционной системе  
 Следующие требования к памяти и процессору применяются ко всем выпускам [!INCLUDE[ssCurrent](../../includes/ssnoversion-md.md)]:  
  
|Компонент|Требование|  
|---------------|-----------------|  
|Память \*|**Минимальные:**<br/><br/> Экспресс-выпуски: 512 МБ<br/><br/> Все другие выпуски: 1 ГБ<br/><br/> **Рекомендуемые:**<br/><br/> Экспресс-выпуски: 1 ГБ<br/><br/> Все другие выпуски: Для обеспечения оптимальной производительности требуется не менее 4 ГБ с последующим увеличением по мере роста размера базы данных.|  
|Быстродействие процессора|**Минимум**: процессор x64 с тактовой частотой 1,4 ГГц<br/><br/> **Рекомендуемые:** 2,0 ГГц и выше|  
|Тип процессора|Процессор x64: AMD Opteron, AMD Athlon 64, Intel Xeon с поддержкой Intel EM64T, Intel Pentium IV с поддержкой EM64T.|  
  
> [!NOTE]  
> Установка [!INCLUDE[ssCurrent](../../includes/ssnoversion-md.md)] поддерживается только для процессоров x64. Процессоры x86 больше не поддерживаются.  
  
 \* Минимальный объем оперативной памяти, необходимый для установки компонента [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] в [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] (DQS), составляет 2 ГБ. Это значение отличается от требований, предъявляемых к минимальному объему памяти [!INCLUDE[ssCurrent](../../includes/ssnoversion-md.md)]. Подробные сведения об установке DQS см. в разделе [Install Data Quality Services](../../data-quality-services/install-windows/install-data-quality-services.md).  

**Поддержка Server Core:**

Установка SQL Server 2019 в режиме основных серверных компонентов поддерживается в следующих выпусках Windows Server:

|                              |
| :------------------------  |
| Windows Server 2019 Core | 
| Windows Server 2016 Core |
| &nbsp; | 

Дополнительные сведения об установке SQL Server на Server Core см. в разделе [Установка SQL Server на Server Core](../../database-engine/install-windows/install-sql-server-on-server-core.md).  

###  <a name="TOP_Principal"></a> Совместимость с ОС   

В следующей таблице показано, какие версии SQL Server 2019 совместимы с различными версиями Windows:  
  

| Выпуск SQL Server:               | Enterprise | Разработчик | Standard | Web Edition | Express |  
| :------------------------       | :--------- | :-------- | :------- | :-- | :------ | 
| Windows Server 2019 Datacenter    |    Да     |    Да    |    Да   | Да |   Да   |
| Windows Server 2019 Standard      |    Да     |    Да    |    Да   | Да |   Да   |
| Windows Server 2019 Essentials    |    Да     |    Да    |    Да   | Да |   Да   |
| Windows Server 2016 Datacenter    |    Да     |    Да    |    Да   | Да |   Да   |
| Windows Server 2016 Standard      |    Да     |    Да    |    Да   | Да |   Да   |
| Windows Server 2016 Essentials    |    Да     |    Да    |    Да   | Да |   Да   |
| &nbsp; | &nbsp; |


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
  
- Локальный диск 
    - [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сейчас поддерживает диски со стандартным размером сектора в 512 байт и 4 КБ.  Использование жестких дисков с размером сектора размером более 4 КБ могут привести к ошибкам при попытке сохранить файлы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на них.  См. в разделе [Ограничения размера сектора жесткого диска в SQL Server](https://support.microsoft.com/kb/926930) дополнительные сведения о поддерживаемых размерах сектора жесткого диска в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. 
    - [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает локальные диски только для установки файлов tempdb. Проверьте правильность пути, указанного для файлов tempdb и файлов журнала на всех узлах кластера. Если во время отработки отказа каталоги tempdb недоступны на целевом узле отработки отказа, то при переводе ресурсов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в режим «в сети» произойдет ошибка.
- Общее хранилище  
- [Локальные дисковые пространства \(S2D\)](https://technet.microsoft.com/windows-server-docs/storage/storage-spaces/storage-spaces-direct-overview)  
- Общая папка SMB  
    - Хранилище SMB не поддерживается для файлов данных автономных или кластерных установок служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Используйте вместо него непосредственно подключенное хранилище, сеть хранения данных или S2D. 
    - Хранилище SMB может размещаться на файловом сервере Windows или на устройстве с хранилищем SMB сторонних разработчиков. Если используется файловый сервер Windows, он должен иметь версию 2008 или последующую. Дополнительные сведения об установке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с общей папкой SMB в качестве хранилища см. в разделе [Установка SQL Server с общей папкой SMB в качестве хранилища](../../database-engine/install-windows/install-sql-server-with-smb-fileshare-as-a-storage-option.md).  
  
  
  
##  <a name="DC_support"></a> Установка [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на контроллере домена  
 Исходя из соображений безопасности, не рекомендуется устанавливать [!INCLUDE[ssCurrent](../../includes/ssnoversion-md.md)] на контроллере домена. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не заблокирует установку на компьютере, который является контроллером домена, однако при этом будут применены следующие ограничения.  
  
- Запуск служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на контроллере домена в учетной записи локальной службы невозможен.    
- После установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] компьютер, который является членом домена, нельзя будет сделать контроллером домена. Перед этим придется удалить [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .    
- После установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] компьютер, который является контроллером домена, нельзя будет сделать членом домена. Перед этим придется удалить [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .   
- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не поддерживает экземпляры отказоустойчивого кластера, где узлы кластера являются контроллерами домена.   
- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не поддерживается на контроллере домена только для чтения. Программа установки[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не может создавать группы безопасности или подготавливать учетные записи служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на контроллере домена, доступном только для чтения. В такой ситуации программа установки завершается ошибкой. 
- Экземпляр отказоустойчивого кластера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не поддерживается в среде, где доступен только контроллер домена только для чтения. 
  
## <a name="see-also"></a>См. также раздел  
 [Планирование установки SQL Server](../../sql-server/install/planning-a-sql-server-installation.md)   
 [Вопросы безопасности при установке SQL Server](../../sql-server/install/security-considerations-for-a-sql-server-installation.md)   

