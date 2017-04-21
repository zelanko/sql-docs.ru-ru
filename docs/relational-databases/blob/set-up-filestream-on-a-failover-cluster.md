---
title: "Настойка FILESTREAM в отказоустойчивом кластере | Документация Майкрософт"
ms.custom: 
ms.date: 08/26/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-blob
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FILESTREAM [SQL Server], setting up on a failover cluster
ms.assetid: 6721f780-20b7-4109-8ddb-ac327310699e
caps.latest.revision: 20
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 8c5bcc49ace68aaf9d35fd3365e693ddd953a0ce
ms.lasthandoff: 04/11/2017

---
# <a name="set-up-filestream-on-a-failover-cluster"></a>Установка FILESTREAM в отказоустойчивом кластере
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
  
  

