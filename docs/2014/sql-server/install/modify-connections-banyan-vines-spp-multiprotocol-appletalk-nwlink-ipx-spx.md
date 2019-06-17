---
title: Изменение подключений, использующих сетевые протоколы Banyan VINES Sequenced Packet Protocol (SPP), Multiprotocol, AppleTalk и NWLink IPX SPX | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- network protocols [SQL Server], modifying connections
- SPP [SQL Server]
- NWLink IPX/SPX [SQL Server]
- connections [SQL Server]
- AppleTalk [SQL Server]
- Sequenced Packet Protocol [SQL Server]
- Multiprotocol Net-Library [SQL Server]
- Banyan VINES Sequenced Package Protocol [SQL Server]
- IPX/SPX [SQL Server]
- protocols [SQL Server], modifying connections
- RPC [SQL Server]
ms.assetid: 5c5ae453-cc5b-4898-95c7-ad34157b1f60
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: cdbcaa39e3d9630bd4ea50919f31cdbb15a36d14
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66093901"
---
# <a name="modify-connections-that-use-banyan-vines-sequenced-packet-protocol-spp-multiprotocol-appletalk-or-nwlink-ipx-spx-network-protocols"></a>Изменение подключений, использующие сетевые протоколы Banyan VINES SPP, Multiprotocol, AppleTalk или NWLink IPX/SPX
  Помощник по обновлению обнаружил протоколы соединений «клиент-сервер», неподдерживаемые в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Клиентские приложения, использующие сетевые протоколы Banyan VINES Sequenced Packet Protocol (SPP), Multiprotocol, AppleTalk и NWLink IPX/SPX, должны устанавливать соединение с помощью поддерживаемого протокола.  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Описание  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] не поддерживает сетевые протоколы Banyan VINES Sequenced Packet Protocol (SPP), Multiprotocol, AppleTalk и NWLink IPX/SPX. Клиенты, подключенные ранее с помощью этих протоколов, должны выбрать другой протокол.  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Измените клиентские приложения, чтобы они использовали для соединения с сервером поддерживаемый протокол. Если существует псевдоним, использующий один из неподдерживаемых протоколов, необходимо изменить псевдоним, чтобы использовался один из поддерживаемых протоколов.  
  
 Если строка подключения приложения явно использует или загружает неподдерживаемые протоколы, указывая Network = DBMSRPCN для RPC, NETWORK = DBMSADSN для Appletalk или NETWORK = DBMSVINN для Banyan Vines, или с помощью явного префикс, например «spx: *сервер\экземпляр*"для протокола SPX, «bv:*server*" для Banyan VINES, «adsp:*server*"для протокола AppleTalk или «rpc:*server*«для Multiprotocol, то необходимо изменить приложение для использования одного из поддерживаемых протоколов.  
  
 Дополнительные сведения см. в разделе «Выбор сетевого протокола» в электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>См. также  
 [Проблемы обновления компонента Database Engine](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Помощник по обновлению SQL Server 2014 &#91;new&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
