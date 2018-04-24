---
title: Настойка FILESTREAM в отказоустойчивом кластере | Документация Майкрософт
ms.custom: ''
ms.date: 08/26/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: blob
ms.reviewer: ''
ms.suite: sql
ms.technology:
- dbe-blob
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- FILESTREAM [SQL Server], setting up on a failover cluster
ms.assetid: 6721f780-20b7-4109-8ddb-ac327310699e
caps.latest.revision: 20
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d738480648fc9427707ca3949672a9311fe5f2e2
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="set-up-filestream-on-a-failover-cluster"></a>Установка FILESTREAM в отказоустойчивом кластере
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  В этом разделе описано включение FILESTREAM в отказоустойчивом кластере. Перед началом этой процедуры необходимо ознакомиться с принципами работы [отказоустойчивой кластеризации](../../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md) и включить FILESTREAM. Сведения о включении FILESTREAM см. в разделе [Включение и настройка FILESTREAM](../../relational-databases/blob/enable-and-configure-filestream.md).  
  
### <a name="to-set-up-filestream-on-a-failover-cluster"></a>Установка FILESTREAM в отказоустойчивом кластере  
  
1.  Установите основной узел отказоустойчивого кластера.  
  
     После завершения программы установки включите FILESTREAM на основном узле с помощью **диспетчера конфигурации SQL Server**. Тем самым включаются параметры, требующие права доступа администратора Windows. Если нужен удаленный доступ, установите флажок **Разрешить удаленным клиентам потоковый доступ к данным FILESTREAM**. Этим создается кластерный ресурс общей папки.  
  
2.  Установите пассивный узел.  
  
     После завершения программы установки включите FILESTREAM на пассивном узле с помощью **диспетчера конфигурации SQL Server**. Имя указываемого **общего ресурса Windows** должно быть одинаковым для всех узлов кластера.  
  
3.  Чтобы установить дополнительные пассивные узлы, повторите шаг 2.  
  
4.  После добавления всех узлов завершите процесс, выполнив хранимую процедуру sp_configure на каждом экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
5.  Чтобы в любое время добавить и задействовать дополнительные узлы кластера, можно повторить шаги 2, 3 и 4.  
  
## <a name="see-also"></a>См. также:  
 [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [Создание отказоустойчивого кластера SQL Server (программа установки)](../../sql-server/failover-clusters/install/create-a-new-sql-server-failover-cluster-setup.md)   
 [Удаление экземпляра отказоустойчивого кластера SQL Server (программа установки)](../../sql-server/failover-clusters/install/remove-a-sql-server-failover-cluster-instance-setup.md)   
 [Добавление или удаление узлов в отказоустойчивом кластере SQL Server (программа установки)](../../sql-server/failover-clusters/install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md)  
  
  
