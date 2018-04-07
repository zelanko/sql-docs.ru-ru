---
title: Конфигурация брандмауэра PDW (система платформы аналитики)
author: barbkess
ms.author: barbkess
manager: craigg
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: ''
ms.component: ''
ms.technology: mpp-data-warehouse
ms.custom: ''
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 191f292d-16bc-4166-b855-158854ad062d
caps.latest.revision: 28
ms.openlocfilehash: 8795f2254160a4ba605643b89dc4b9df0cce4c7f
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2018
---
# <a name="pdw-firewall-configuration"></a>Конфигурация брандмауэра PDW
**Брандмауэра** страница SQL Server PDW Configuration Manager позволяет включить или отключить правила брандмауэра, которые разрешают или запрещают доступ к конкретным портам на устройстве, Analytics Platform System.  
  
## <a name="to-manage-ports-and-firewall-rules-for-appliance-nodes"></a>Управление портами и правила брандмауэра для узлы устройств  
  
1.  Запустите диспетчер конфигурации. Дополнительные сведения см. в разделе [запустите диспетчер конфигурации &#40;Analytics Platform System&#41;](launch-the-configuration-manager.md).  
  
2.  В левой панели диспетчера конфигурации разверните **топологии хранилища параллельных данных**, а затем нажмите кнопку **брандмауэра**.  
  
3.  Найдите правило порта или брандмауэр, для обновления списка конфигураций и затем установите или снимите флажок рядом с этого элемента. В этом списке, включая открытие и закрытие портов на общедоступный узлов отображаются только параметры можно настроить администратора SQL Server PDW.  
  
4.  Нажмите кнопку **применить** для сохранения изменений.  
  
![DWConfig Appliance PDW Firewall](./media/pdw-firewall-configuration/SQL_Server_PDW_DWConfig_ApplPDWFirewall.png "SQL_Server_PDW_DWConfig_ApplPDWFirewall")  
  
## <a name="external-ports"></a>Внешние порты  
Для клиентских подключений, поступающих от за пределами PDW открыты следующие порты.  
  
|Назначение|Порт №|Узлы|  
|-----------|-----------|---------|  
|Доступ клиентов SQL PDW (TDS)|17001|CTL|  
|Загрузчик клиентского доступа (dwloader & служб SSIS)|8001|CTL|  
|Удаленного доступа к рабочему столу|3389|СПИСОК ДОВЕРИЯ СЕРТИФИКАТОВ, CMP|  
|BinaryLoaderDataChannel служб SSIS|16551|CTL|  
|dwloader BinaryLoaderDataChannel|16551|CMP|  
|SSL-шифрованием подключений (для внутренней связи, для доступа к консоли администрирования и доступ к службам кластера HDInsight)|443|Все узлы|  
|SQL Server PDW нагрузки управлений - учетные данные Windows|8002|CTL|  
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
  
