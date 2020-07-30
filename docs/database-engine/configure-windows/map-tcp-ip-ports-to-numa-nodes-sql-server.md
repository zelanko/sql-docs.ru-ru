---
title: Сопоставление портов TCP/IP с узлами NUMA (SQL Server) | Документы Майкрософт
description: Узнайте, как использовать сопоставление портов TCP/IP с узлами NUMA с помощью диспетчера конфигурации SQL Server. Поймите, как создать битовую карту идентификации узла.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: high-availability
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
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 055821c4d005c52ff20b79967fca35ac2994ff9f
ms.sourcegitcommit: 99f61724de5edf6640efd99916d464172eb23f92
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/28/2020
ms.locfileid: "87362631"
---
# <a name="map-tcp-ip-ports-to-numa-nodes-sql-server"></a>Сопоставление портов TCP/IP с узлами NUMA (SQL Server)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  В этом разделе описывается сопоставление портов TCP/IP с узлами архитектуры доступа к неоднородной памяти (NUMA) с помощью диспетчера конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . При запуске компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] записывает сведения об узле в журнал ошибок.  
  
 Для определения номера используемого узла прочитайте сведения об узле в журнале ошибок или в представлении **sys.dm_os_schedulers** . Для установки адреса и порта TCP/IP для одного или нескольких узлов добавьте битовую карту идентификации узла (маску схожести) в квадратных скобках после номера порта. Узлы могут быть указаны как в десятичном, так и в шестнадцатеричном формате. Для создания битовой карты пронумеруйте узлы справа налево начиная от нуля, то есть в порядке 76543210. Создайте битовое представление списка узлов, указывая 1 для используемых узлов и 0 — для неиспользуемых. Например, чтобы задействовать узлы NUMA 0, 2 и 5, укажите 00100101.  
  
```text
NUMA node number                            76543210
Mask for 0, 2, and 5 counting from right    00100101
```
  
 Преобразуйте двоичное представление (00100101) в десятичное `[37]`или шестнадцатеричное `[0x25]`. Для прослушивания всех узлов не указывайте идентификатор узла.  
  
 Если порт сопоставлен с более чем одним узлом NUMA, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] назначает соединения с узлами циклическим образом, не пытаясь сохранить баланс нагрузки между разными узлами.  
  
> [!NOTE]  
>  Чтобы настроить [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на прослушивание нескольких портов TCP для каждого IP-адреса, см. раздел [Настройка компонента Database Engine на прослушивание нескольких портов TCP](../../database-engine/configure-windows/configure-the-database-engine-to-listen-on-multiple-tcp-ports.md).  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="SSMSProcedure"></a> Использование диспетчера конфигурации SQL Server  
  
#### <a name="to-map-a-tcpip-port-to-a-numa-node"></a>Сопоставление порта TCP/IP узлу NUMA  
  
1.  В диспетчере конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] раскройте раздел **Сетевая конфигурация SQL Server** и щелкните элемент **Протоколы для**  *\<instance name>* .  
  
2.  В области сведений дважды щелкните **TCP/IP**.  
  
3.  На вкладке **IP-адреса** в разделе, соответствующем настраиваемому IP-адресу, в поле **TCP-порт** добавьте идентификатор узла NUMA в квадратных скобках после номера порта. Например, для TCP-порта 1500 и узлов 0, 2 и 5 используйте **1500[37]** или **1500[0x25]** .  
  
## <a name="see-also"></a>См. также:  
 [Архитектура Soft-NUMA (SQL Server)](../../database-engine/configure-windows/soft-numa-sql-server.md)  
  
  
