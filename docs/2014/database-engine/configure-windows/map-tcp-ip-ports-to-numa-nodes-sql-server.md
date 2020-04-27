---
title: Сопоставление портов TCP/IP с узлами NUMA (SQL Server) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- NUMA
- memory [SQL Server], NUMA
- affinity NUMA
- ports [SQL Server], working with NUMA
- CPU [SQL Server], NUMA support
- NUMA, How to map a port to a NUMA node
- NUMA affinity
- TCP/IP [SQL Server], NUMA support
- non-uniform memory access
ms.assetid: 07727642-0266-4cbc-8c55-3c367e4458ca
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 138e5743e18ba6e39aa55aaec6931413dd21175b
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "62781748"
---
# <a name="map-tcp-ip-ports-to-numa-nodes-sql-server"></a>Сопоставление портов TCP/IP с узлами NUMA (SQL Server)
  В этом разделе описывается сопоставление портов TCP/IP с узлами архитектуры доступа к неоднородной памяти (NUMA) с помощью диспетчера конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . При запуске компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] записывает сведения об узле в журнал ошибок.  
  
 Для определения номера используемого узла прочитайте сведения об узле в журнале ошибок или в представлении **sys.dm_os_schedulers** . Для установки адреса и порта TCP/IP для одного или нескольких узлов добавьте битовую карту идентификации узла (маску схожести) в квадратных скобках после номера порта. Узлы могут быть указаны как в десятичном, так и в шестнадцатеричном формате. Для создания битовой карты пронумеруйте узлы справа налево начиная от нуля, то есть в порядке 76543210. Создайте битовое представление списка узлов, указывая 1 для используемых узлов и 0 — для неиспользуемых. Например, чтобы задействовать узлы NUMA 0, 2 и 5, укажите 00100101.  
  
|||  
|-|-|  
|номер узла NUMA|76543210|  
|Отметьте 0, 2 и 5, считая справа|00100101|  
  
 Преобразуйте двоичное представление (00100101) в десятичное `[37]`или шестнадцатеричное `[0x25]`. Для прослушивания всех узлов не указывайте идентификатор узла.  
  
 Если порт сопоставлен с более чем одним узлом NUMA, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] назначает соединения с узлами циклическим образом, не пытаясь сохранить баланс нагрузки между разными узлами.  
  
> [!NOTE]  
>  Чтобы настроить [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на прослушивание нескольких портов TCP для каждого IP-адреса, см. раздел [Настройка компонента Database Engine на прослушивание нескольких портов TCP](configure-the-database-engine-to-listen-on-multiple-tcp-ports.md).  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="SSMSProcedure"></a> Использование диспетчера конфигурации SQL Server  
  
#### <a name="to-map-a-tcpip-port-to-a-numa-node"></a>Сопоставление порта TCP/IP узлу NUMA  
  
1.  В диспетчере конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] разверните узел **Сетевая конфигурация SQL Server** и щелкните элемент **Протоколы для** *\<имя экземпляра>* .  
  
2.  В области сведений дважды щелкните **TCP/IP**.  
  
3.  На вкладке **IP-адреса** в разделе, соответствующем настраиваемому IP-адресу, в поле **TCP-порт** добавьте идентификатор узла NUMA в квадратных скобках после номера порта. Например, для TCP-порта 1500 и узлов 0, 2 и 5 используйте `1500[37]` или `1500[0x25]`.  
  
## <a name="see-also"></a>См. также:  
 [Настройка SQL Server для использования &#40;SQL Server с мягкими NUMA&#41;](soft-numa-sql-server.md)  
  
  
