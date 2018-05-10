---
title: Установка служб Integration Services | Документы Майкрософт
ms.custom: ''
ms.date: 02/05/2018
ms.prod: sql
ms.prod_service: integration-services
ms.component: install-windows
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
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
caps.latest.revision: 106
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 4d2b8a34a4489e2db01c9e0b53a4cc11c7b435f5
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="install-integration-services"></a>Установка служб Integration Services
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предоставляет единую программу установки для всех компонентов, включая службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Она позволяет на одном компьютере устанавливать службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] как вместе с другими компонентами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , так и отдельно от них.    
    
 В этой статье рассматриваются важные моменты, которые следует знать перед началом установки служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Сведения в этой статье помогут правильно подобрать параметры установки, сделать правильный выбор и успешно осуществить установку.    
    
## <a name="preparing-to-install-integration-services"></a>Подготовка к установке служб Integration Services    
 Прежде чем приступить к установке служб [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], ознакомьтесь со следующими сведениями:    
    
-   [Требования к оборудованию и программному обеспечению для установки SQL Server](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)    
    
-   [Вопросы безопасности при установке SQL Server](../../sql-server/install/security-considerations-for-a-sql-server-installation.md)    
    
## <a name="installing-standalone-or-side-by-side"></a>Автономная или параллельная установка    
Установку служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] можно производить в следующих конфигурациях.    
    
-   Службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] можно установить на компьютере, не содержащем ранее установленных экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].    
    
-   Установить службы [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] можно параллельно с существующим экземпляром служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].    
    
При обновлении до последней версии служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] на компьютере, на котором уже установлена более ранняя версия служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], текущая версия устанавливается параллельно с предыдущей.    
    
Дополнительные сведения об обновлении служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] см. в статье [Обновление служб Integration Services](../../integration-services/install-windows/upgrade-integration-services.md).
    
## <a name="installing-integration-services"></a>установка служб Integration Services    
 Просмотрев требования по установке для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и убедившись, что компьютер соответствует этим требованиям, можно начинать установку служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].    
     
Если службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] устанавливаются с помощью мастера установки, выбор компонентов и параметров производится с помощью последовательности страниц.

-   На странице **Выбор компонентов** в разделе **Общие компоненты** выберите **Службы Integration Services**.

-   В разделе **Компоненты экземпляра** при необходимости выберите **Службы компонента Database Engine** для размещения базы данных каталога SSIS `SSISDB`, которая служит для хранения, выполнения и мониторинга пакетов SSIS, а также управления ими.

-   Чтобы установить управляемые сборки для программирования служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], в разделе **Общие компоненты** также выберите **Пакет SDK клиентских средств**.

> [!NOTE]
> Некоторые из компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], выбранных для установки на странице **Выбор компонентов** мастера установки, устанавливают подмножество компонентов служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Эти компоненты полезны для определенных задач, но функциональные возможности служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ограничены. Например, для компонента **Службы компонента Database Engine** устанавливаются также компоненты служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , необходимые мастеру импорта и экспорта [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Чтобы выполнить полную установку служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], выберите на странице **Выбор компонентов** компонент **Службы Integration Services** .

### <a name="installing-a-dedicated-server-for-etl"></a>Установка выделенного сервера для извлечения, преобразования и загрузки

Чтобы использовать выделенный сервер для извлечения, преобразования и загрузки данных (ETL), установите локальный экземпляр компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] при установке служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] обычно хранят пакеты в экземпляре компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] и используют агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , чтобы составить расписание выполнения этих пакетов. Если на сервере ETL нет экземпляра компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)], нужно запускать пакеты или составлять расписание их выполнения с сервера, на котором имеется экземпляр компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)]. В результате пакеты будут выполняться не на сервере ETL, а на сервере, откуда они запускаются. В результате ресурсы выделенного сервера ETL не будут использоваться так, как ожидалось. Более того, у других серверов может возникнуть нехватка ресурсов из-за выполнения процессов извлечения, преобразования и загрузки.

### <a name="configuring-ssis-event-logging"></a>Настройка ведения журнала событий служб SSIS
    
По умолчанию в новой установке службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] настроены таким образом, чтобы не заносить в журнал событий приложений события, связанные с запуском пакетов. Это позволяет избежать слишком большого количества записей в журнале событий при использовании компонента сборщика данных [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. События, которые не заносятся в журнал: EventID 12288, "Package started" и EventID 12289, "Package finished successfully." Чтобы эти события заносились в журнал событий приложений, откройте реестр для изменения. Затем найдите в реестре узел HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\130\SSIS и измените значение DWORD для параметра LogPackageExecutionToEventLog с 0 на 1.    
    
## <a name="a-complete-installation-of-integration-services"></a>Полная установка служб Integration Services

Чтобы произвести полную установку служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], выберите нужные компоненты из приведенного ниже списка.

-   **Службы Integration Services (SSIS)**. Установите службы SSIS с помощью мастера установки SQL Server. При выборе служб SSIS устанавливаются следующие компоненты:
    -   поддержка каталога SSIS в ядре СУБД SQL Server;
    -   дополнительный компонент SSIS Scale Out, который состоит из главной и рабочих ролей;
    -   32-и 64-разрядные компоненты служб SSIS;
    -   При установке служб SSIS **не** устанавливаются средства, необходимые для проектирования и разработки пакетов SSIS.
-   **Ядро СУБД SQL Server**. Установите ядро СУБД с помощью мастера установки SQL Server. При выборе ядра СУБД можно создать и разместить базу данных каталога SSIS `SSISDB`, которая служит для хранения, выполнения и мониторинга пакетов SSIS, а также управления ими.
-   **SQL Server Data Tools (SSDT)**. Инструкции по скачиванию и установке SQL Server Data Tools (SSDT) см. в разделе [Скачать SQL Server Data Tools (SSDT)](../../ssdt/download-sql-server-data-tools-ssdt.md). Установив SSDT, вы сможете разрабатывать и развертывать пакеты SSIS. В составе SSDT устанавливаются следующие компоненты:
    -   средства проектирования и разработки пакетов SSIS, включая конструктор служб SSIS;
    -   только 32-разрядные компоненты служб SSIS;
    -   версия Visual Studio с ограниченными возможностями (если еще не установлен один из выпусков Visual Studio);
    -   Visual Studio Tools for Applications (VSTA), редактор скриптов, используемый задачей "Скрипт" и компонентом "Скрипт" службы SSIS;
    -   мастеры служб SSIS, включая мастер развертывания и мастер обновления пакетов;
    -   мастер импорта и экспорта SQL Server.
-   **Пакет дополнительных компонентов служб Integration Services для Azure**. Чтобы скачать и установить пакет дополнительных компонентов, перейдите на страницу [пакета дополнительных компонентов служб Microsoft SQL Server 2017 Integration Services для Azure](https://www.microsoft.com/download/details.aspx?id=54798). Установка пакета дополнительных компонентов позволяет пакетам подключаться к службам хранения и анализа данных в облаке Azure, включая следующие службы:
    -   хранилище BLOB-объектов Azure;
    -   Azure HDInsight;
    -   Azure Data Lake Store;
    -   хранилище данных SQL Azure.
-   **Дополнительные компоненты**. При необходимости можно скачать дополнительные компоненты от сторонних производителей, входящие в состав пакета дополнительных компонентов SQL Server.
    -   Соединитель с SAP BW (Microsoft®) для Microsoft SQL Server®. Чтобы получить эти компоненты, перейдите на страницу [пакета дополнительных компонентов Microsoft® SQL Server® 2017](https://www.microsoft.com/download/details.aspx?id=55992).
    -   Соединитель для Oracle (Microsoft) версии 5.0 от компании Attunity и соединитель для Teradata (Microsoft) версии 5.0 от компании Attunity. Чтобы получить эти компоненты, перейдите на страницу [соединителей для Oracle и Teradata (Microsoft) версии 5.0](https://www.microsoft.com/download/details.aspx?id=55179).
