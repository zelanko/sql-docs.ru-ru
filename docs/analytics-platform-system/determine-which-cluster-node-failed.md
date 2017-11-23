---
title: "Определить, какой из узлов кластера, сбой (система платформы аналитики)"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: sql-non-specified
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: analytics-platform-system
ms.technology: mpp-data-warehouse
ms.custom: 
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1e001117-a1b6-4357-bf25-e85aba3f1cf0
caps.latest.revision: "21"
ms.openlocfilehash: 59f188526cff2d605c5bffcf2187b3c765276c81
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="determine-which-cluster-node-failed"></a>Определите, какой узел кластера не удалось
Описывается, как определить имя узла SQL Server PDW, произошла ошибка после возникновения сбоя кластера, и было активировано предупреждение отказоустойчивого кластера. В ходе устранения неполадок отказоустойчивого кластера необходимо определить имя узла, который не удалось выполнить перед обращение в корпорацию Майкрософт, чтобы помочь решить проблему.  
  
## <a name="Background"></a>Фон  
Для обеспечения высокой доступности в SQL Server PDW узел элемента управления и вычислительные узлы настроены как активный или пассивный компоненты отказоустойчивых кластеров Windows. Если активный сервер не отвечает на запросы критических системных, пассивный сервер при сбое и выполняет функции сервера, который не удалось.  
  
После отработки отказа кластера когда SQL Server PDW сообщает о состоянии узла, пассивный сервер имеет сбоя через состояние. Однако он не является очевидным каким сервером или узлом не удалось, особенно в том случае, если сервер, не удалось выполнить все еще в сети. Для устранения сбоя кластера, необходимо определить имя узла, при сбое.  
  
## <a name="AdminConsoleSolution"></a>Консоль администрирования решения  
  
#### <a name="to-find-the-name-of-the-node-that-failed"></a>Чтобы определить имя узла, который не удалось  
  
1.  Откройте консоль администрирования. Дополнительные сведения о консоли администрирования см. в разделе [отслеживать устройства с помощью консоли администрирования &#40; Система платформы аналитики &#41; ](monitor-the-appliance-by-using-the-admin-console.md). После перехода на другой ресурс, переход на другой ресурс событие включается в число оповещений на **работоспособности** страницы. Отсутствует **работоспособности** страницы для области PDW области HDI и области структуры устройства. Каждая страница работоспособности имеет **ОПОВЕЩЕНИЯ** вкладки. Дополнительные сведения о предупреждении щелкните страницу работоспособности вкладку "предупреждения" и щелкните оповещение.  
  
## <a name="SystemView"></a>Системное представление решение  
Следующая инструкция SQL показывает, как использовать [sys.dm_pdw_component_health_active_alerts](../relational-databases/system-dynamic-management-views/sys-dm-pdw-component-health-active-alerts-transact-sql.md) системное представление, чтобы найти имя сервера, на котором произошел сбой.  
  
```sql  
SELECT  
SUBSTRING( component_instance_id, 2, charindex(' ', component_instance_id, 1)-2) AS failed_node_name,  
create_time AS failover_time  
FROM sys.dm_pdw_component_health_active_alerts  
WHERE alert_id = 500139  
ORDER BY failed_node_name;  
```  
  
