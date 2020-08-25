---
title: Конфигурация брандмауэра PDW
description: Страница брандмауэр SQL Server PDW Configuration Manager позволяет включать или отключать правила брандмауэра, которые разрешают или запрещают доступ к конкретным портам на устройстве системы аналитики.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 4ed739ce12170aa6d0ab79b996de0075cd6723ee
ms.sourcegitcommit: 33e774fbf48a432485c601541840905c21f613a0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/25/2020
ms.locfileid: "74400887"
---
# <a name="parallel-data-warehouse-firewall-configuration-in-analytics-platform-system"></a>Конфигурация брандмауэра параллельного хранилища данных в системе платформы аналитики

Страница **брандмауэр** SQL Server PDW Configuration Manager позволяет включать или отключать правила брандмауэра, которые разрешают или запрещают доступ к конкретным портам на устройстве системы аналитики.  
  
## <a name="to-manage-ports-and-firewall-rules-for-appliance-nodes"></a>Управление портами и правилами брандмауэра для узлов устройств  
  
1.  Запустите Configuration Manager. Дополнительные сведения см. [в статье запуск Configuration Manager &#40;Analytics Platform System&#41;](launch-the-configuration-manager.md).  
  
2.  В левой области Configuration Manager разверните **топология параллельного хранилища данных**, а затем щелкните **брандмауэр**.  
  
3.  Найдите порт или правило брандмауэра для обновления в списке Конфигурация, а затем установите или снимите флажок рядом с этим элементом. В этом списке показаны только SQL Server PDW параметры, настраиваемые администратором, включая открытие и закрытие портов на внешних узлах.  
  
4.  Нажмите кнопку **Применить** , чтобы сохранить изменения.  
  
![Брандмауэр PDW устройств DWConfig](./media/pdw-firewall-configuration/SQL_Server_PDW_DWConfig_ApplPDWFirewall.png "SQL_Server_PDW_DWConfig_ApplPDWFirewall")  
  
## <a name="external-ports"></a>Внешние порты  
Следующие порты открыты для клиентских подключений, поступающих за пределы PDW.  
  
|Назначение|Порту #|Узлы|  
|-----------|-----------|---------|  
|Доступ клиента SQL для PDW (TDS)|17001|ДОВЕРИЯ|  
|Клиентский доступ загрузчика (dwloader & SSIS)|8001|ДОВЕРИЯ|  
|Доступ к удаленному рабочему столу|3389|CTL, CMP|  
|Бинарилоадердатачаннел служб SSIS|16551|ДОВЕРИЯ|  
|dwloader Бинарилоадердатачаннел|16551|ФАЙЛЕ|  
|SSL-шифрованные подключения (для внутренней связи, для доступа к консоли администрирования)|443|Все узлы|  
|Поток управления SQL Server PDW нагрузки — учетные данные Windows|8002|ДОВЕРИЯ|  
|_Kerberos|88|AD01 и AD02,|  
|_ldap|389|AD01 и AD02|  
| &nbsp; | &nbsp; | &nbsp; |
  
## <a name="internal-ports"></a>Внутренние порты  
Следующие порты используются в PDW для внутреннего взаимодействия, но не открываются для подключений, поступающих за пределы устройства PDW.  
  
|Назначение|Порту #|Узлы|  
|-----------|-----------|---------|  
|Трафик канала управления DMS|16450|CTL, CMP|  
|Трафик канала данных DMS|16550|CTL, CMP|  
|Внутренняя диагностика|16650|CTL, CMP|  
|Состояние отработки отказа (DMS)|15 000|CTL, CMP|  
|Состояние отработки отказа (механизм)|15001|ФАЙЛЕ|  
|Динамический диапазон портов (эфемерных)|20000-65535|CTL, CMP|  
|Диапазоны портов SQL Server (TDS)|1433, 1500-1508|CTL, CMP|  
| &nbsp; | &nbsp; | &nbsp; |
  
> [!NOTE]  
> При создании внешних таблиц или внешних источников данных по умолчанию используется TCP-порт 8020. Эти инструкции можно настроить так, чтобы вместо них использовались другие порты. Порт JOB_TRACKER_LOCATION Hortonworks по умолчанию — 50300. Для интеграции с другими системами и инструментами могут потребоваться дополнительные порты.  
  
<!-- MISSING LINKS ## See Also  
[HDInsight Firewall Configuration &#40;Analytics Platform System&#41;](hdinsight-firewall-configuration.md)
-->
  
