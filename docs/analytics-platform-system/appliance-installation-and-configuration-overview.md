---
title: Устройство, установить и настроить - Analytics Platform System | Документация Майкрософт
description: Пошаговое описание Analytics Platform System (APS) Администраторы устройств через первоначальные этапы для настройки и приступить к использованию нового устройства.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 5b6aa75cdab85fce9ef308d3e853ddb0107c28ee
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63276350"
---
# <a name="appliance-installation-and-configuration-for-analytics-platform-system"></a>Модуль установки и настройки для Analytics Platform System
Пошаговое описание Analytics Platform System (APS) Администраторы устройств через первоначальные этапы для настройки и приступить к использованию нового устройства.  
  
<!-- MISSING LINKS ## <a name="BeforeYouBegin"></a>Before You Begin  
Before you begin to install, configure, and use your new appliance, we recommend reviewing information about the appliance components. Review the following to familiarize yourself with the appliance:  
  
-   Review [Understanding the Appliance Nodes and Hardware (SQL Server PDW)](assetId:///f60f419f-d1e1-403d-8cf9-07e7ef6d6627) to be sure you understand the components included in your new appliance.  
  
-   Review [Connecting to SQL Server PDW (SQL Server PDW)](assetId:///721851d5-e521-4d5b-ba6d-8e2e9d3c7808) to understand how and when appliance administrators will connect to each appliance node.  
-->

## <a name="InstallHardware"></a>1. Установка оборудования  
Новые устройства будут доставлены на палет на панель закрепления в вашем центре обработки данных.  
  
> [!IMPORTANT]  
> В некоторых случаях независимого поставщика Оборудования будут Распаковка, установка в стойку и подключите устройство для вас в вашем центре обработки данных. Если таким образом, эти инструкции не обязательны, и можно перейти к [3. Настройте модуль](#ConfigureAppliance) разделе ниже.  
  
Если независимого поставщика Оборудования выполняется установка оборудования, следуйте инструкциям ниже для установки оборудования.  
  
|||  
|-|-|  
|**Задача**|**Описание**|  
|Подтвердите документации|Убедитесь, что вы получили все необходимые документы и сведения из вашего независимого поставщика оборудования (IHV). См. в разделе [сведения, получаемые от независимого поставщика Оборудования &#40;Analytics Platform System&#41;](information-to-obtain-from-your-ihv.md).|  
|Установка оборудования|Убедитесь, что в центр обработки данных можно разместить модуль. Компоненты перемещаются в устройства в центр обработки данных. Сетевые коммутаторы, PDU, установка в стойку и подключение кабелей. См. в разделе [Установка оборудования &#40;Analytics Platform System&#41;](hardware-installation.md).|  
  
## <a name="PowerOnAppliance"></a>2. Питания на устройстве  
  
|||  
|-|-|  
|**Задача**|**Описание**|  
|Питания на устройстве|Питания на каждом узле компонента устройства в нужном порядке, ожидающих так, чтобы подтвердить, что ошибки не обнаружены.|  
  
## <a name="ConfigureAppliance"></a>3. Настройка устройства  
  
|||  
|-|-|  
|**Задача**|**Описание**|  
|||  
|Настройка устройства с помощью SQL Server PDW**Configuration Manager**|Используйте диспетчер конфигурации для задания паролей устройства, часовых поясов, параметры сети и брандмауэра, сертификаты безопасности и производительности и другие параметры на устройстве. См. в разделе [конфигурация устройства &#40;Analytics Platform System&#41;](appliance-configuration.md).|  
  
> [!WARNING]  
> Изменения конфигурации должны производиться только с помощью SQL Server PDW**Configuration Manager**. Изменения не предоставляется через **Configuration Manager** не поддерживаются. Например SQL Server PDW appliance поддерживает только параметр языка английского (США).  
  
## <a name="SoftwareServicing"></a>4. Настройка обслуживания программного обеспечения  
  
|||  
|-|-|  
|**Задача**|**Описание**|  
|Применение обновлений SQL Server PDW|(Необязательно) Может потребоваться применить одно или несколько обновлений SQL Server PDW для обновления до последней версии программного обеспечения SQL Server PDW. См. в разделе [применения исправлений системы платформы аналитики &#40;Analytics Platform System&#41;](apply-analytics-platform-system-hotfixes.md).|  
|Настройка служб Windows Server Update Services|Настройте устройство для получения обновлений из службы обновления Windows Server для поддержки программного обеспечения. См. в разделе [скачивание и применение обновлений Майкрософт &#40;Analytics Platform System&#41;](download-and-apply-microsoft-updates.md).|  
  
## <a name="NextSteps"></a>Дальнейшие действия  
После завершения всех предыдущих шагов, ваше устройство будет готов к использованию. Вы или другой персонал на место можно перейти в решении следующих задач.  
  
|||  
|-|-|  
|**Задача**|**Описание**|  
|Установить SQL Server PDW драйверы и настройки подключения|Настройка локальных компьютерах для подключения к SQL Server PDW с помощью SQL Server Data Tools, sqlcmd, бизнес-аналитики программ или других средств. <!-- MISSING LINKS See [Client Tools (SQL Server PDW)](assetId:///721851d5-e521-4d5b-ba6d-8e2e9d3c7808).-->|  
|Создание ролей входы в систему и сервера и назначение разрешений|Планирование и Создание ролей входы в систему и сервера, которые позволяют пользователям входить на SQL Server PDW с соответствующими разрешениями. <!-- MISSING LINKS See [PDW Permissions &#40;SQL Server PDW&#41;](../sqlpdw/pdw-permissions-sql-server-pdw.md).-->|  
|Настройка шлюза управления данными Azure|Шлюз обеспечивает Azure пользователям получать доступ к локальным данным APS посредством размещения данных APS максимально безопасной веб-каналы OData. На управляющем узле уже установлен шлюз. Спросите у Майкрософт за помощь в конфигурации.|  
|Монитор запросов и устройства пользователей|Используйте консоль администратора и другие ресурсы для отслеживания запросов и устройства пользователей. См. в разделе [мониторинг устройства с помощью консоли администрирования &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md)<!-- MISSING LINKS and [User Sessions &#40;SQL Server PDW&#41;](../sqlpdw/user-sessions-sql-server-pdw.md)-->.|  
|Загрузка данных в SQL Server PDW|Загрузка данных в устройстве. <!-- MISSING LINKS See [Load &#40;SQL Server PDW&#41;](../sqlpdw/load-sql-server-pdw.md).-->|  
|Создать план аварийного восстановления|Запланируйте, как позволяет защитить ваши данные от сбоев оборудования или перезаписи данных. Создание плана с помощью регулярного резервного копирования и восстановления планы в случае потери или повреждения данных. <!-- MISSING LINKS See [Create a Disaster Recovery Plan &#40;SQL Server PDW&#41;](../sqlpdw/create-a-disaster-recovery-plan-sql-server-pdw.md).-->|  
|Мониторинг устройства|Отслеживать состояние устройства, работоспособность и производительность с помощью системных представлений, журналов и консоли администрирования. Исправьте или сообщить о неполадках. См. в разделе [состояния работоспособности монитора устройства &#40;Analytics Platform System&#41;](../relational-databases/system-dynamic-management-views/sys-dm-pdw-component-health-status-transact-sql.md).|  
