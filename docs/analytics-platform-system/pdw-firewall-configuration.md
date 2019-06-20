---
title: Конфигурация брандмауэра PDW - Analytics Platform System | Документация Майкрософт
description: Страница брандмауэра SQL Server PDW Configuration Manager позволяет включить или отключить правила брандмауэра, разрешить или запретить доступ к определенные порты на устройстве, Analytics Platform System.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: d92d92752b4de105857f5611fbe95262476a4e13
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66822431"
---
# <a name="parallel-data-warehouse-firewall-configuration-in-analytics-platform-system"></a>Параллельные хранилища данных в брандмауэре в Analytics Platform System

**Брандмауэра** страница SQL Server PDW Configuration Manager позволяет включить или отключить правила брандмауэра, разрешить или запретить доступ к определенные порты на устройстве, Analytics Platform System.  
  
## <a name="to-manage-ports-and-firewall-rules-for-appliance-nodes"></a>Для управления портами и правила брандмауэра для узлов устройства  
  
1.  Запустите диспетчер конфигурации. Дополнительные сведения см. в разделе [запустить диспетчер конфигурации служб &#40;Analytics Platform System&#41;](launch-the-configuration-manager.md).  
  
2.  В левой области Configuration Manager разверните узел **топологии хранилище параллельных данных**, а затем нажмите кнопку **брандмауэра**.  
  
3.  Найдите правило порта или брандмауэра для обновления списка конфигураций и затем установите или снимите флажок рядом с этого элемента. В этом списке, включая открытие и закрытие портов на узлах, доступных извне отображаются только параметры можно настроить администратора SQL Server PDW.  
  
4.  Нажмите кнопку **применить** для сохранения изменений.  
  
![Брандмауэр PDW устройств DWConfig](./media/pdw-firewall-configuration/SQL_Server_PDW_DWConfig_ApplPDWFirewall.png "SQL_Server_PDW_DWConfig_ApplPDWFirewall")  
  
## <a name="external-ports"></a>Внешние порты  
Следующие порты открыты для клиентских подключений, поступающих от за пределами PDW.  
  
|Цель|Номер порта|Узлы|  
|-----------|-----------|---------|  
|SQL клиентского доступа для PDW (TDS)|17001|СПИСОК ДОВЕРИЯ СЕРТИФИКАТОВ|  
|Загрузчик клиентского доступа (dwloader & служб SSIS)|8001|СПИСОК ДОВЕРИЯ СЕРТИФИКАТОВ|  
|Удаленному рабочему столу|3389|CTL, CMP|  
|BinaryLoaderDataChannel служб SSIS|16551|СПИСОК ДОВЕРИЯ СЕРТИФИКАТОВ|  
|dwloader BinaryLoaderDataChannel|16551|КОМПАНИЯ CMP|  
|SSL-шифрованием подключений (для внутреннего обмена данными, для доступа к консоли администрирования)|443|Все узлы|  
|Поток управления нагрузки PDW сервера SQL - учетные данные Windows|8002|СПИСОК ДОВЕРИЯ СЕРТИФИКАТОВ|  
|_Kerberos|88|AD01 и AD02,|  
|_ldap|389|AD01 и AD02|  
| &nbsp; | &nbsp; | &nbsp; |
  
## <a name="internal-ports"></a>Внутренние порты  
Следующие порты используются PDW для внутренней связи, но не открыт для подключений, поступающих от за пределами PDW appliance.  
  
|Цель|Номер порта|Узлы|  
|-----------|-----------|---------|  
|Трафик канала управления DMS|16450|CTL, CMP|  
|Трафик канала данных DMS|16550|CTL, CMP|  
|Внутренней диагностики|16650|CTL, CMP|  
|Состояние отработки отказа (DMS)|15000|CTL, CMP|  
|Состояние отработки отказа (ядра)|15001|КОМПАНИЯ CMP|  
|Диапазон динамических портов (временного)|20000-65535|CTL, CMP|  
|Диапазоны портов SQL Server (TDS)|1433, 1500-1508|CTL, CMP|  
| &nbsp; | &nbsp; | &nbsp; |
  
> [!NOTE]  
> Создание внешних таблиц или внешние источники данных использует TCP-порт 8020 по умолчанию. Эти инструкции можно настроить для использования вместо других портов. Порт по умолчанию Hortonworks JOB_TRACKER_LOCATION — 50300. Интеграция с другими системами и средства может потребоваться дополнительные порты.  
  
<!-- MISSING LINKS ## See Also  
[HDInsight Firewall Configuration &#40;Analytics Platform System&#41;](hdinsight-firewall-configuration.md)
-->
  
