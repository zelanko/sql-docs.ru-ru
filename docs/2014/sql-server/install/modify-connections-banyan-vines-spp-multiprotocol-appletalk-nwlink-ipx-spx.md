---
title: Изменение подключений, использующих сетевые протоколы Banyan VINEs виртуализированного протокола (SPP), Multiprotocol, AppleTalk или NWLink IPX SPX | Документация Майкрософт
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66093901"
---
# <a name="modify-connections-that-use-banyan-vines-sequenced-packet-protocol-spp-multiprotocol-appletalk-or-nwlink-ipx-spx-network-protocols"></a>Изменение подключений, использующие сетевые протоколы Banyan VINES SPP, Multiprotocol, AppleTalk или NWLink IPX/SPX
  Помощник по обновлению обнаружил протоколы соединений «клиент-сервер», неподдерживаемые в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Клиентские приложения, использующие сетевые протоколы Banyan VINES Sequenced Packet Protocol (SPP), Multiprotocol, AppleTalk и NWLink IPX/SPX, должны устанавливать соединение с помощью поддерживаемого протокола.  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] не поддерживает сетевые протоколы Banyan VINES Sequenced Packet Protocol (SPP), Multiprotocol, AppleTalk и NWLink IPX/SPX. Клиенты, подключенные ранее с помощью этих протоколов, должны выбрать другой протокол.  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Измените клиентские приложения, чтобы они использовали для соединения с сервером поддерживаемый протокол. Если существует псевдоним, использующий один из неподдерживаемых протоколов, необходимо изменить псевдоним, чтобы использовался один из поддерживаемых протоколов.  
  
 Если строка подключения приложения использует или загружает один из этих протоколов, укажите NETWORK = DBMSRPCN для RPC, NETWORK = DBMSADSN for AppleTalk или NETWORK = ДБМСВИНН для свойства Banyan VINEs или с помощью явного префикса, например "SPX:*сохраняет*" для SPX, "BV:*Server*" для Banyan Vines, "ADSP:*Server*" для AppleTalk или "RPC:*Server*" для многопротокольного протокола, необходимо изменить приложение для использования одного из поддерживаемых протоколов.  
  
 Дополнительные сведения см. в разделе «Выбор сетевого протокола» в электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>См. также:  
 [Проблемы обновления ядро СУБД](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Советник по переходу SQL Server 2014 &#91;New&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
