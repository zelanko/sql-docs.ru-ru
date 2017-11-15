---
title: "Подключение к SQL Server через прокси-сервер (диспетчер конфигурации SQL Server) | Документы Майкрософт"
ms.custom: 
ms.date: 12/15/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Remote WinSock
- RWS
- LATs
- proxy servers [SQL Server]
- connections [SQL Server], proxy server
- Microsoft Proxy Server [SQL Server]
- local address tables [SQL Server]
ms.assetid: 39714de0-2a1f-4179-9091-5c3fa4612545
caps.latest.revision: "22"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3db9fdfc433edc0ab8f8d5bf7361669eb707061c
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="connect-to-sql-server-through-a-proxy-server-sql-server-configuration-manager"></a>Подключение к SQL Server через прокси-сервер (диспетчер конфигурации SQL Server)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  В этом разделе описано, как в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] установить соединение с SQL Server через прокси-сервер с помощью диспетчера конфигурации SQL Server. Для удаленного прослушивания прокси-сервером Remote WinSock (RWS) определите таблицу локальных адресов (LAT) для прокси-сервера таким образом, чтобы адрес прослушивающего узла находился вне диапазона записей LAT.  
  
##  <a name="SSMSProcedure"></a> Использование диспетчера конфигурации SQL Server  
  
#### <a name="to-enable-connections-to-sql-server-through-microsoft-proxy-server"></a>Обеспечение соединений с SQL Server с помощью прокси-сервера Microsoft  
  
1.  Следуйте указаниям в разделе [Настройка сервера для прослушивания указанного TCP-порта (SQL Server Configuration Manager)](../../database-engine/configure-windows/configure-a-server-to-listen-on-a-specific-tcp-port.md), чтобы определить, какие TCP/IP-порты используются [!INCLUDE[ssDE](../../includes/ssde-md.md)], или настроить [!INCLUDE[ssDE](../../includes/ssde-md.md)] для использования нужного порта.  
  
2.  В прокси-сервере определите таблицу локальных адресов (LAT) для прокси-сервера таким образом, чтобы адрес прослушивающего узла находился вне диапазона записей LAT. Дополнительные сведения см. в документации по прокси-серверу.  
  
>  [!NOTE]
>  Эта тема относится к локальному развертыванию [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]. Сведения о проблемах с подключением, касающихся [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], см. в разделе [Устранение неполадок подключения к Базе данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-troubleshoot-common-connection-issues).  


