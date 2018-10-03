---
title: Настойка FILESTREAM в отказоустойчивом кластере | Документация Майкрософт
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.technology: filestream
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], setting up on a failover cluster
ms.assetid: 6721f780-20b7-4109-8ddb-ac327310699e
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: ca95e56a965cb2dd967a673fb33688fd09981960
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48228040"
---
# <a name="set-up-filestream-on-a-failover-cluster"></a>Установка FILESTREAM в отказоустойчивом кластере
  В этом разделе описано включение FILESTREAM в отказоустойчивом кластере. Перед началом этой процедуры необходимо ознакомиться с принципами работы [отказоустойчивой кластеризации](../../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md) и включить FILESTREAM. Сведения о включении FILESTREAM см. в разделе [Включение и настройка FILESTREAM](enable-and-configure-filestream.md).  
  
### <a name="to-set-up-filestream-on-a-failover-cluster"></a>Установка FILESTREAM в отказоустойчивом кластере  
  
1.  Установите основной узел отказоустойчивого кластера.  
  
     После завершения программы установки включите FILESTREAM на основном узле с помощью **диспетчера конфигурации SQL Server**. Тем самым включаются параметры, требующие права доступа администратора Windows. Если нужен удаленный доступ, установите флажок **Разрешить удаленным клиентам потоковый доступ к данным FILESTREAM**. Этим создается кластерный ресурс общей папки.  
  
2.  Установите пассивный узел.  
  
     После завершения программы установки включите FILESTREAM на пассивном узле с помощью **диспетчера конфигурации SQL Server**. Имя указываемого **общего ресурса Windows** должно быть одинаковым для всех узлов кластера.  
  
3.  Чтобы установить дополнительные пассивные узлы, повторите шаг 2.  
  
4.  После добавления всех узлов завершите процесс, выполнив хранимую процедуру sp_configure на каждом экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
5.  Чтобы в любое время добавить и задействовать дополнительные узлы кластера, можно повторить шаги 2, 3 и 4.  
  
## <a name="see-also"></a>См. также  
 [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [Создание отказоустойчивого кластера SQL Server (программа установки)](../../sql-server/failover-clusters/install/create-a-new-sql-server-failover-cluster-setup.md)   
 [Удаление экземпляра отказоустойчивого кластера SQL Server (программа установки)](../../sql-server/failover-clusters/install/remove-a-sql-server-failover-cluster-instance-setup.md)   
 [Добавление или удаление узлов в отказоустойчивом кластере SQL Server (программа установки)](../../sql-server/failover-clusters/install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md)  
  
  
