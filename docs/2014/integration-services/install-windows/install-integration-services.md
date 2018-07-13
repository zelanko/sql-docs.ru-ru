---
title: Установка служб Integration Services | Документы Майкрософт
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Integration Services, installing
- SSIS, installing
- installing Integration Services, about installing Integration Services
- SQL Server Integration Services, installing
- Setup [Integration Services], about installing Integration Services
- installing Integration Services
- Setup [Integration Services]
ms.assetid: bd20fd3a-414b-4581-959d-ebba4ddf5a55
caps.latest.revision: 100
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: cd10fc638ed7a1d9c42b926190eebc0df5dd37b8
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37156542"
---
# <a name="install-integration-services"></a>Установка служб Integration Services
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предоставляет единую программу установки для всех компонентов, включая службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Она позволяет на одном компьютере устанавливать службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] как вместе с другими компонентами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , так и отдельно от них.  
  
 Этот раздел обращает внимание на важные моменты, которые следует рассмотреть перед началом установки служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Сведения, содержащиеся в этом разделе, помогут правильно подобрать параметры установки, сделать правильный выбор и успешно осуществить установку.  
  
 Этот раздел не содержит инструкций по запуску программы установки, ее выполнению из командной строки и использованию мастера установки. Пошаговые инструкции по запуску программы установки и выберите компоненты для установки, см. в разделе [Быстрая установка SQL Server 2014](../../getting-started/quick-start-installation-of-sql-server-2014.md). Сведения о параметрах командной строки для установки [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], см. в разделе [Установка SQL Server 2014 из командной строки](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md).  
  
## <a name="preparing-to-install-integration-services"></a>Подготовка к установке служб Integration Services  
 Прежде чем приступить к установке служб [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], ознакомьтесь со следующими требованиями:  
  
-   [Требования к оборудованию и программному обеспечению для установки SQL Server 2014](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)  
  
-   [Параметры для средства проверки конфигурации системы](../../database-engine/install-windows/check-parameters-for-the-system-configuration-checker.md)  
  
-   [Вопросы безопасности при установке SQL Server](../../sql-server/install/security-considerations-for-a-sql-server-installation.md)  
  
## <a name="selecting-an-integration-services-configuration"></a>Выбор конфигурации служб Integration Services  
 Установку служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] можно производить в следующих конфигурациях.  
  
-   Службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] можно установить на компьютере, не содержащем ранее установленных экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Установить службы [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] вы можете параллельно с существующим экземпляром служб [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] и [!INCLUDE[ssISversion11](../../includes/ssisversion11-md.md)].  
  
     При обновлении до [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] на компьютере, где уже установлена одна из предыдущих версий [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] устанавливается параллельно с более ранней версией.  
  
     Дополнительные сведения об обновлении [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]см. в статье [Обновление служб Integration Services](upgrade-integration-services.md). Дополнительные сведения об обратной совместимости с предыдущими версиями служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]см. в статье [Обратная совместимость служб Reporting Services](../integration-services-backward-compatibility.md).  
  
## <a name="installing-integration-services"></a>установка служб Integration Services  
 Просмотрев требования по установке для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и убедившись, что компьютер соответствует этим требованиям, можно начинать установку служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
> [!NOTE]  
>  В предыдущих версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]по умолчанию при установке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] все пользователи в группе пользователей имели доступ к службе [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . При установке [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]пользователи не имеют доступа к службе [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . По умолчанию эта служба является защищенной. После [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] администратор должен запустить средство настройки DCOM (Dcomcnfg.exe), чтобы предоставить конкретным пользователям доступ к **SQL Server Integration Services 12.0**.  
>   
>  Инструкции о том, как предоставлять разрешения, см. в статье [Предоставление разрешений службам Integration Services](../grant-permissions-to-integration-services-service.md).  
  
 Если службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]устанавливаются с помощью мастера установки, выбор компонентов и параметров производится с помощью последовательности страниц. Ниже приведены страницы в мастере установки, где выбранных параметров влияет на установку [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] выбора рекомендации:  
  
-   **Выбор компонентов**  
  
     Выберите компонент **Службы Integration Services** , чтобы установить службу [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] и получить возможность запускать пакеты вне среды разработки.  
  
     Для полной установки служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]вместе со средствами и документацией для разработки пакетов и управления ими выберите службы **Integration Services** и следующие **общие компоненты**:  
  
    -   **SQL Server Data Tools** , чтобы установить средства разработки пакетов.  
  
    -   **Средства управления — полный набор** для установки среды управления пакетами [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] .  
  
    -   **Пакет SDK клиентских средств** , чтобы установить управляемые сборки для программирования служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
     Многие решения по реализации хранилищ данных требуют установки дополнительных компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , например компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
    > [!NOTE]  
    >  Некоторые из компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], выбранных для установки на странице **Выбор компонентов** мастера установки, устанавливают подмножество компонентов служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Эти компоненты полезны для определенных задач, но функциональные возможности служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] будут ограничены. Например, для компонента **Службы компонента Database Engine** устанавливаются также компоненты служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , необходимые мастеру импорта и экспорта [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . При выборе компонента **SQL Server Data Tools** также устанавливаются компоненты служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , необходимые для разработки пакетов, однако сами службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] не устанавливаются, и поэтому выполнение пакетов за пределами среды [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]будет невозможно. Чтобы выполнить полную установку служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], выберите на странице **Выбор компонентов** компонент **Службы Integration Services** .  
  
     **Установка на 64-разрядный компьютер.** На 64-разрядном компьютере при выборе компонента **Службы Integration Services** устанавливаются только 64-разрядные версии средств и среды выполнения. Если требуется выполнять пакеты в 32-разрядном режиме, нужно также выбрать дополнительный параметр, чтобы установить 32-разрядные версии средств и среды выполнения.  
  
    -   Если 64-разрядном компьютере запущена операционная система x86, выберите **SQL Server Data Tools** или **средства управления — полный**.  
  
    -   Если работает под управлением 64-разрядном компьютере [!INCLUDE[vcpritanium](../../includes/vcpritanium-md.md)] операционной системе, выберите **средства управления — полный**.  
  
     **Установка на выделенном сервере для извлечения, преобразования и загрузки.** Чтобы использовать выделенный сервер для извлечения, преобразования и загрузки данных, рекомендуется установить локальный экземпляр компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] при установке служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] обычно хранят пакеты в экземпляре компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] и используют агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , чтобы составить расписание выполнения этих пакетов. Если на сервере ETL нет экземпляра компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)], нужно запускать пакеты или составлять расписание их выполнения с сервера, на котором имеется экземпляр компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Это значит, что пакеты будут выполняться не на сервере ETL, а на сервере, откуда они были запущены. В результате ресурсы выделенного сервера ETL не будут использоваться так, как ожидалось. Более того, у других серверов может возникнуть нехватка ресурсов из-за выполнения процессов извлечения, преобразования и загрузки.  
  
-   **Конфигурация экземпляра**  
  
     Ни один из параметров, выбранных на странице **Конфигурация экземпляра** , не оказывает влияния на службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] или службу [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
     На компьютере может быть установлен только один экземпляр службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Подключение к службе производится с помощью имени компьютера.  
  
     По умолчанию службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] настроены для управления пакетами в базе данных **msdb** экземпляра компонента Database Engine, установленного одновременно со службами [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Если экземпляр компонента Database Engine одновременно со службами [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]не установлен, служба [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] будет настроена для управления пакетами, хранящимися в базе данных **msdb** на локальном экземпляре по умолчанию компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Чтобы управлять пакетами, хранящимися на именованном или удаленном экземпляре компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] либо на нескольких экземплярах компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)], необходимо изменить файл конфигурации. Дополнительные сведения об изменении этого файла конфигурации см. в статье [Настройка служб Integration Services (служба SSIS)](../service/integration-services-service-ssis-service.md).  
  
-   **Конфигурация сервера**  
  
     Просмотрите настройки службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] на вкладке **Учетные записи службы** страницы **Конфигурация сервера** .  
  
     Если установлены Windows 7 или Windows Server 2008 R2, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] служба регистрируется для запуска под виртуальной учетной NT Services\MsDtsServer120 и **тип запуска** — **автоматического**.  Для виртуальной учетной записи не обязательно вводить пароль. Если на компьютере установлены Microsoft Vista или Windows Server 2008, то служба [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] регистрируется для запуска под встроенной учетной записью "Network Service", а **Тип запуска** определяется как **Автоматический**. Для работы под встроенной учетной записью Network Service пароль вводить не нужно.  
  
 По умолчанию в новой установке службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] настроены таким образом, чтобы не заносить в журнал событий приложений события, связанные с запуском пакетов. Это позволяет избежать слишком большого количества записей в журнале событий при использовании компонента сборщика данных [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. События, которые не заносятся в журнал: EventID 12288, "Package started" и EventID 12289, "Package finished successfully." Чтобы эти события заносились в журнал событий приложений, откройте реестр для изменения. Затем найдите в реестре узел HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\SSIS и измените значение DWORD для параметра LogPackageExecutionToEventLog с 0 на 1.  
  
## <a name="understanding-the-integration-services-service"></a>Основные сведения о службе Integration Services  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] устанавливает службу [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
 По умолчанию служба [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] устанавливается при выборе на странице **Выбор компонентов** параметра **Службы Integration Services** . При выборе настроек по умолчанию на странице **Конфигурация сервера** служба [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] включена, а ее **Тип запуска** установлен в значение **Авто**.  
  
 Предусмотрена возможность установить только единственный экземпляр службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] на отдельном компьютере. Эта служба не относится к конкретному экземпляру компонента Database Engine. Подключение к этой службе производится с помощью имени компьютера, на котором она запущена.  
  
## <a name="installing-integration-services-on-64-bit-computers"></a>Установка служб Integration Services на 64-разрядных компьютерах  
  
### <a name="integration-services-features-installed-on-64-bit-computers"></a>Функциональные возможности служб Integration Services, установленных на 64-разрядных компьютерах  
 Программа установки производит установку различных функций служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] в зависимости от выбранных пользователем параметров установки.  
  
-   Если при установке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выбирается установка служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , то программа установки произведет установку всех доступных 64-разрядных функций и средств служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
-   Если пользователю необходимы функции времени разработки служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , то следует также установить среду [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
-   При необходимости запуска определенных пакетов в 32-разрядном режиме с помощью 32-разрядных версий среды выполнения и средств служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] следует также установить среду [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
 64-разрядные функции устанавливаются в каталог **Program Files** , а 32-разрядные — отдельно в каталог **Program Files (x86)** . (Это одинаково для служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].)  
  
> [!IMPORTANT]  
>  Среда [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], 32-разрядная среда разработки для пакетов служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], не поддерживается на 64-разрядных платформах [!INCLUDE[vcpritanium](../../includes/vcpritanium-md.md)] и не устанавливается на серверы на базе процессоров [!INCLUDE[vcpritanium](../../includes/vcpritanium-md.md)].  
  
  
