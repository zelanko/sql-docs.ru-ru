---
title: Настройка брандмауэра PDW — Analytics Platform System | Документы Microsoft
description: Страница брандмауэра SQL Server PDW Configuration Manager позволяет включить или отключить правила брандмауэра, которые разрешают или запрещают доступ к конкретным портам на устройстве, Analytics Platform System.
aauthor: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 8ccfd60aee7647c2421870a09ab5fa9b2653b99d
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="parallel-data-warehouse-firewall-configuration-in-analytics-platform-system"></a>Параллельные хранилища данных конфигурации брандмауэра, в Analytics Platform System
**Брандмауэра** страница SQL Server PDW Configuration Manager позволяет включить или отключить правила брандмауэра, которые разрешают или запрещают доступ к конкретным портам на устройстве, Analytics Platform System.  
  
## <a name="to-manage-ports-and-firewall-rules-for-appliance-nodes"></a>Управление портами и правила брандмауэра для узлы устройств  
  
1.  Запустите диспетчер конфигурации. Дополнительные сведения см. в разделе [запустите диспетчер конфигурации &#40;Analytics Platform System&#41;](launch-the-configuration-manager.md).  
  
2.  В левой панели диспетчера конфигурации разверните **топологии хранилища параллельных данных**, а затем нажмите кнопку **брандмауэра**.  
  
3.  Найдите правило порта или брандмауэр, для обновления списка конфигураций и затем установите или снимите флажок рядом с этого элемента. В этом списке, включая открытие и закрытие портов на общедоступный узлов отображаются только параметры можно настроить администратора SQL Server PDW.  
  
4.  Нажмите кнопку **применить** для сохранения изменений.  
  
![Брандмауэр PDW DWConfig](./media/pdw-firewall-configuration/SQL_Server_PDW_DWConfig_ApplPDWFirewall.png "SQL_Server_PDW_DWConfig_ApplPDWFirewall")  
  
## <a name="external-ports"></a>Внешние порты  
Для клиентских подключений, поступающих от за пределами PDW открыты следующие порты.  
  
|Назначение|Порт №|Узлы|  
|-----------|-----------|---------|  
|Доступ клиентов SQL PDW (TDS)|17001|СПИСОК ДОВЕРИЯ СЕРТИФИКАТОВ|  
|Загрузчик клиентского доступа (dwloader & служб SSIS)|8001|СПИСОК ДОВЕРИЯ СЕРТИФИКАТОВ|  
|Удаленного доступа к рабочему столу|3389|СПИСОК ДОВЕРИЯ СЕРТИФИКАТОВ, CMP|  
|BinaryLoaderDataChannel служб SSIS|16551|СПИСОК ДОВЕРИЯ СЕРТИФИКАТОВ|  
|dwloader BinaryLoaderDataChannel|16551|CMP|  
|SSL-шифрованием подключений (для внутренней связи, для доступа к консоли администрирования и доступ к службам кластера HDInsight)|443|Все узлы|  
|SQL Server PDW нагрузки управлений - учетные данные Windows|8002|СПИСОК ДОВЕРИЯ СЕРТИФИКАТОВ|  
|_Kerberos|88|AD01 и AD02,|  
|_фильтры|389|AD01 и AD02|  
  
## <a name="internal-ports"></a>Внутренние порты  
Следующие порты используются по PDW для внутренней связи, но не открыт для подключений, поступающих от за пределами PDW appliance.  
  
|Назначение|Порт №|Узлы|  
|-----------|-----------|---------|  
|Канал управления DMS трафика|16450|СПИСОК ДОВЕРИЯ СЕРТИФИКАТОВ, CMP|  
|Трафик канала данных DMS.|16550|СПИСОК ДОВЕРИЯ СЕРТИФИКАТОВ, CMP|  
|Внутренней диагностики|16650|СПИСОК ДОВЕРИЯ СЕРТИФИКАТОВ, CMP|  
|Состояние отработки отказа (DMS)|15000|СПИСОК ДОВЕРИЯ СЕРТИФИКАТОВ, CMP|  
|Состояние отработки отказа (Engine)|15001|CMP|  
|Динамический (эфемерных) диапазон портов|20000-65535|СПИСОК ДОВЕРИЯ СЕРТИФИКАТОВ, CMP|  
|Диапазоны портов SQL Server (TDS)|1433, 1500-1508|СПИСОК ДОВЕРИЯ СЕРТИФИКАТОВ, CMP|  
  
> [!NOTE]  
> Создание внешних таблиц или внешние источники данных использует TCP-порт 8020 по умолчанию. Эти инструкции можно настроить для использования вместо других портов. Порт по умолчанию Hortonworks JOB_TRACKER_LOCATION — 50300. Интеграция с другими системами и средства может потребоваться дополнительные порты.  
  
<!-- MISSING LINKS ## See Also  
[HDInsight Firewall Configuration &#40;Analytics Platform System&#41;](hdinsight-firewall-configuration.md)  -->  
  
