---
title: Установка и Настройка устройства
description: Пошаговые инструкции по настройке и началу работы с новым устройством см. в руководстве по выполнению действий администраторами управляющих систем платформы AP.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 49ed0f26f20d081f4f9b307e6be90a3f5bd8c372
ms.sourcegitcommit: 591bbf4c7e4e2092f8abda6a2ffed263cb61c585
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/22/2020
ms.locfileid: "86942206"
---
# <a name="appliance-installation-and-configuration-for-analytics-platform-system"></a>Установка и настройка устройств для платформы аналитики
Пошаговые инструкции по настройке и началу работы с новым устройством см. в руководстве по выполнению действий администраторами управляющих систем платформы AP.  
  
<!-- MISSING LINKS ## <a name="BeforeYouBegin"></a>Before You Begin  
Before you begin to install, configure, and use your new appliance, we recommend reviewing information about the appliance components. Review the following to familiarize yourself with the appliance:  
  
-   Review [Understanding the Appliance Nodes and Hardware (SQL Server PDW)](assetId:///f60f419f-d1e1-403d-8cf9-07e7ef6d6627) to be sure you understand the components included in your new appliance.  
  
-   Review [Connecting to SQL Server PDW (SQL Server PDW)](assetId:///721851d5-e521-4d5b-ba6d-8e2e9d3c7808) to understand how and when appliance administrators will connect to each appliance node.  
-->

## <a name="1-install-the-hardware"></a><a name="InstallHardware"></a>1. Установка оборудования  
Новое устройство будет доставлено на палеты на закрепление в центре обработки данных.  
  
> [!IMPORTANT]  
> В некоторых случаях независимо от поставщика оборудования будет распаковаться в стойку и подключить устройство для вас в центре обработки данных. В этом случае эти инструкции не требуются, и можно перейти к [3. Настройте раздел "устройство"](#ConfigureAppliance) ниже.  
  
Если IHV не выполняет установку оборудования, выполните следующие действия для установки оборудования.  
  
|Задача|Описание|  
|-|-|  
|Подтверждение документации|Убедитесь, что получены все необходимые документы и сведения от независимого поставщика оборудования (IHV). Ознакомьтесь со [сведениями, которые можно получить из&#41;системы &#40;аналитики независимого поставщика оборудования ](information-to-obtain-from-your-ihv.md).|  
|Установка оборудования|Убедитесь, что центр обработки данных может разместить устройство. Переместите компоненты устройства в центр обработки данных. Стойка сетевых коммутаторов, PDU и кабелей. См. раздел [Установка оборудования &#40;Analytics Platform System&#41;](hardware-installation.md).|  
  
## <a name="2-power-on-the-appliance"></a><a name="PowerOnAppliance"></a>2. Включение устройства  
  
|Задача|Описание|  
|-|-|  
|Включение устройства|Включите питание каждого узла компонента устройства в нужном порядке, дождитесь, если это необходимо, чтобы убедиться в отсутствии ошибок.|  
  
## <a name="3-configure-the-appliance"></a><a name="ConfigureAppliance"></a>3. Настройка устройства  
  
|Задача|Описание|  
|-|-|  
|Настройте устройство с помощью SQL Server PDW**Configuration Manager**|Используйте Configuration Manager, чтобы задать пароли устройств, часовые пояса, параметры сети и брандмауэра, сертификаты безопасности, а также производительность и другие параметры устройства. См. раздел [Конфигурация устройства &#40;Analytics Platform System&#41;](appliance-configuration.md).|  
  
> [!WARNING]  
> Изменения конфигурации следует вносить только с помощью**Configuration Manager**SQL Server PDW. Изменения, не представленные в **Configuration Manager** , не поддерживаются. Например, устройство SQL Server PDW поддерживает только параметр английского языка (США).  
  
## <a name="4-set-up-software-servicing"></a><a name="SoftwareServicing"></a>4. Настройка обслуживания программного обеспечения  
  
|Задача|Описание|  
|-|-|  
|Применить обновления SQL Server PDW|Используемых Чтобы обновить программное обеспечение SQL Server PDW до последней версии, может потребоваться применить одно или несколько SQL Server PDW обновлений. См. статью [применение исправлений системы &#40;Analytics platform&#41;](apply-analytics-platform-system-hotfixes.md).|  
|Настройка служб Windows Server Update Services|Настройте устройство на получение обновлений от Windows Server Update Services для поддержки программного обеспечения. См. статью [Загрузка и применение обновлений майкрософт &#40;Analytics Platform System&#41;](download-and-apply-microsoft-updates.md).|  
  
## <a name="next-steps"></a><a name="NextSteps"></a>Дальнейшие действия  
После выполнения всех описанных выше действий устройство будет готово к использованию. Вы или другие сотрудники в своем расположении могут продолжить выполнение следующих задач.  
  
|Задача|Описание|  
|-|-|  
|Установка драйверов SQL Server PDW и Настройка подключения|Настройте локальные компьютеры для подключения к SQL Server PDW с помощью SQL Server Data Tools, sqlcmd, программного обеспечения бизнес-аналитики или других средств. <!-- MISSING LINKS See [Client Tools (SQL Server PDW)](assetId:///721851d5-e521-4d5b-ba6d-8e2e9d3c7808).-->|  
|Создание входов и ролей сервера и назначение разрешений|Спланируйте и создайте входы и роли сервера, которые позволят пользователям входить в SQL Server PDW с соответствующими разрешениями. <!-- MISSING LINKS See [PDW Permissions &#40;SQL Server PDW&#41;](../sqlpdw/pdw-permissions-sql-server-pdw.md).-->|  
|Настройка шлюза Azure Управление данными|Шлюз позволяет пользователям Azure получать доступ к локальным данным AP, предоставляя данные ТД в качестве защищенных веб-каналов OData. Шлюз уже установлен на узле управления. Обратитесь в корпорацию Майкрософт за помощью в настройке.|  
|Наблюдение за запросами и пользователями устройств|Используйте консоль администрирования и другие ресурсы для мониторинга запросов и пользователей устройств. См. раздел [мониторинг устройства с помощью консоли администрирования &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md)<!-- MISSING LINKS and [User Sessions &#40;SQL Server PDW&#41;](../sqlpdw/user-sessions-sql-server-pdw.md)-->.|  
|Загрузка данных в SQL Server PDW|Загрузите данные на устройство. <!-- MISSING LINKS See [Load &#40;SQL Server PDW&#41;](../sqlpdw/load-sql-server-pdw.md).-->|  
|Создание плана аварийного восстановления|Спланируйте, как вы будете защищать данные от сбоев оборудования или перезаписи данных. Создайте план, используя регулярные резервные копии и планы восстановления в случае повреждения или потери данных. <!-- MISSING LINKS See [Create a Disaster Recovery Plan &#40;SQL Server PDW&#41;](../sqlpdw/create-a-disaster-recovery-plan-sql-server-pdw.md).-->|  
|Мониторинг устройства|Отслеживайте состояние, работоспособность и производительность устройства с помощью системных представлений, журналов и консоли администрирования. Исправьте или сообщите о проблемах. См. раздел [мониторинг состояния работоспособности устройства &#40;&#41;платформы аналитики ](../relational-databases/system-dynamic-management-views/sys-dm-pdw-component-health-status-transact-sql.md).|  
