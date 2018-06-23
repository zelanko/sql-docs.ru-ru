---
title: Изменение подключений, использующих сетевые протоколы Banyan VINES Sequenced Packet Protocol (SPP), Multiprotocol, AppleTalk и NWLink IPX SPX | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 20
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0167af6c11abb12e8aa38a52a77707b81aecbe78
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36098125"
---
# <a name="modify-connections-that-use-banyan-vines-sequenced-packet-protocol-spp-multiprotocol-appletalk-or-nwlink-ipx-spx-network-protocols"></a>Изменение подключений, использующих сетевые протоколы Banyan VINES Sequenced Packet Protocol (SPP), Multiprotocol, AppleTalk и NWLink IPX SPX
  Помощник по обновлению обнаружил протоколы соединений «клиент-сервер», неподдерживаемые в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Клиентские приложения, использующие сетевые протоколы Banyan VINES Sequenced Packet Protocol (SPP), Multiprotocol, AppleTalk и NWLink IPX/SPX, должны устанавливать соединение с помощью поддерживаемого протокола.  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Описание  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] не поддерживает сетевые протоколы Banyan VINES Sequenced Packet Protocol (SPP), Multiprotocol, AppleTalk и NWLink IPX/SPX. Клиенты, подключенные ранее с помощью этих протоколов, должны выбрать другой протокол.  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Измените клиентские приложения, чтобы они использовали для соединения с сервером поддерживаемый протокол. Если существует псевдоним, использующий один из неподдерживаемых протоколов, необходимо изменить псевдоним, чтобы использовался один из поддерживаемых протоколов.  
  
 Если строка подключения приложения явно использует или загружает неподдерживаемые протоколы, указывая Network = DBMSRPCN для RPC, NETWORK = DBMSADSN для Appletalk или NETWORK = DBMSVINN для Banyan Vines или с помощью явного префиксом в виде, например «spx: *сохраняет*» для протокола SPX, «bv:*сервера*» для Banyan VINES, «adsp:*сервера*» для протокола AppleTalk или» rpc:*сервера*«для Multiprotocol, то необходимо изменить приложение для использования одного из поддерживаемых протоколов.  
  
 Дополнительные сведения см. в разделе «Выбор сетевого протокола» в электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>См. также  
 [Проблемы обновления компонента Database Engine](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Помощник по обновлению SQL Server 2014 &#91;new&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
