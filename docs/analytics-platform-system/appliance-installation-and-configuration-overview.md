---
title: Устройства, установить и настроить - система платформы аналитики | Документы Microsoft
description: Обзор Analytics Platform System (APS) Администраторы устройств через первые шаги для настройки и приступить к работе с нового устройства.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 5b6aa75cdab85fce9ef308d3e853ddb0107c28ee
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
ms.locfileid: "31538624"
---
# <a name="appliance-installation-and-configuration-for-analytics-platform-system"></a>Установка устройств и настройка для система платформы аналитики
Обзор Analytics Platform System (APS) Администраторы устройств через первые шаги для настройки и приступить к работе с нового устройства.  
  
<!-- MISSING LINKS ## <a name="BeforeYouBegin"></a>Before You Begin  
Before you begin to install, configure, and use your new appliance, we recommend reviewing information about the appliance components. Review the following to familiarize yourself with the appliance:  
  
-   Review [Understanding the Appliance Nodes and Hardware (SQL Server PDW)](assetId:///f60f419f-d1e1-403d-8cf9-07e7ef6d6627) to be sure you understand the components included in your new appliance.  
  
-   Review [Connecting to SQL Server PDW (SQL Server PDW)](assetId:///721851d5-e521-4d5b-ba6d-8e2e9d3c7808) to understand how and when appliance administrators will connect to each appliance node.  
-->

## <a name="InstallHardware"></a>1. Установка оборудования  
К новым устройством доставляются на палетах, чтобы закрепить в центре обработки данных.  
  
> [!IMPORTANT]  
> В некоторых случаях к независимому поставщику Оборудования будет распаковать, стойка и подключите устройство для вас в центре обработки данных. Если таким образом, эти инструкции не нужны, и можно перейти к [3. Настройка устройства](#ConfigureAppliance) разделе ниже.  
  
Если к независимому поставщику Оборудования не выполняет установку оборудования, используйте следующие шаги для установки оборудования.  
  
|||  
|-|-|  
|**Задача**|**Description**|  
|Подтвердите документации|Убедитесь, что вы получили все необходимые документы и сведения из вашего оборудования независимых поставщиков Оборудования. В разделе [сведения для получения из вашего Оборудования &#40;Analytics Platform System&#41;](information-to-obtain-from-your-ihv.md).|  
|Установка оборудования|Убедитесь, что центр обработки данных, способное устройства. Устройство компоненты перемещаются в центр обработки данных. Кабели и сетевые коммутаторы, блоками распределения питания, для установки в стойку. В разделе [Установка оборудования &#40;Analytics Platform System&#41;](hardware-installation.md).|  
  
## <a name="PowerOnAppliance"></a>2. Питания на устройстве  
  
|||  
|-|-|  
|**Задача**|**Description**|  
|Питания на устройстве|Питания на каждом узле компонента устройства в нужном порядке, ожидающих при необходимости, чтобы убедиться, что ошибок не обнаружено.|  
  
## <a name="ConfigureAppliance"></a>3. Настройка устройства  
  
|||  
|-|-|  
|**Задача**|**Description**|  
|||  
|Настройка устройства с помощью SQL Server PDW**Configuration Manager**|Используйте диспетчер конфигурации можно установить пароли на устройства, часовые пояса, параметры сети и брандмауэра, сертификаты безопасности, производительности и другие параметры на устройстве. В разделе [настроек устройств &#40;Analytics Platform System&#41;](appliance-configuration.md).|  
  
> [!WARNING]  
> Изменения конфигурации должна выполняться только с помощью SQL Server PDW**Configuration Manager**. Изменения не предоставляется через **Configuration Manager** не поддерживаются. Например SQL Server PDW appliance поддерживает только значения параметра language английский (США).  
  
## <a name="SoftwareServicing"></a>4. Настройка обслуживания программного обеспечения  
  
|||  
|-|-|  
|**Задача**|**Description**|  
|Применение обновлений SQL Server PDW|(Необязательно) Может потребоваться применить одно или несколько обновлений SQL Server PDW для обновления программного обеспечения SQL Server PDW до последней версии. В разделе [применения исправлений системы платформы аналитики &#40;Analytics Platform System&#41;](apply-analytics-platform-system-hotfixes.md).|  
|Настройка Windows Server Update Services|Настройте устройство для получения обновлений из службы обновления Windows Server для поддержки программного обеспечения. В разделе [загрузить и установить обновления Microsoft &#40;Analytics Platform System&#41;](download-and-apply-microsoft-updates.md).|  
  
## <a name="NextSteps"></a>Дальнейшие действия  
После завершения предыдущих шагов будет готов к использованию вашим устройством. Вы или другие сотрудники на место можно перейти в решении следующих задач.  
  
|||  
|-|-|  
|**Задача**|**Description**|  
|Установка SQL Server PDW драйверов и соединения|Настройка локальных компьютерах для подключения к SQL Server PDW с помощью SQL Server Data Tools, sqlcmd, бизнес-аналитики программ или других средств. <!-- MISSING LINKS See [Client Tools (SQL Server PDW)](assetId:///721851d5-e521-4d5b-ba6d-8e2e9d3c7808).-->|  
|Создание ролей входы в систему и сервера и назначение разрешений|Планирование и создание входов и ролях сервера, позволяющих пользователям возможность входа в SQL Server PDW с соответствующими разрешениями. <!-- MISSING LINKS See [PDW Permissions &#40;SQL Server PDW&#41;](../sqlpdw/pdw-permissions-sql-server-pdw.md).-->|  
|Настройка шлюза управления данными Azure|Шлюз позволяет Azure пользователям получать доступ APS локальных данных, предоставляя APS данные, как защитить веб-каналы OData. Шлюз уже установлен на узле управления. Запросить помощь с настройкой Microsoft.|  
|Монитор запросов и устройства пользователей|Используйте консоль администрирования и другие ресурсы для отслеживания запросов и устройства пользователей. В разделе [отслеживать устройства с помощью консоли администрирования &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md)<!-- MISSING LINKS and [User Sessions &#40;SQL Server PDW&#41;](../sqlpdw/user-sessions-sql-server-pdw.md)-->.|  
|Загрузка данных в SQL Server PDW|Загрузка данных на устройство. <!-- MISSING LINKS See [Load &#40;SQL Server PDW&#41;](../sqlpdw/load-sql-server-pdw.md).-->|  
|Создайте план аварийного восстановления|Планирование, каким образом будет защитить данные от сбоев оборудования или перезапись данных. Создание плана с помощью обычного резервного копирования и восстановления планы в случае потери или повреждения данных. <!-- MISSING LINKS See [Create a Disaster Recovery Plan &#40;SQL Server PDW&#41;](../sqlpdw/create-a-disaster-recovery-plan-sql-server-pdw.md).-->|  
|Мониторинг устройства|Отслеживать состояние устройства, работоспособность и производительность с помощью системных представлений, журналов и консоли администрирования. Исправьте или о всех проблемах. В разделе [монитора в состояние работоспособности устройства &#40;Analytics Platform System&#41;](../relational-databases/system-dynamic-management-views/sys-dm-pdw-component-health-status-transact-sql.md).|  
