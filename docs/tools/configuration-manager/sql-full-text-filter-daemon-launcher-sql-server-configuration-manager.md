---
title: Средство запуска управляющей программы полнотекстовой фильтрации SQL (диспетчер конфигурации SQL Server) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.suite: sql
ms.technology: configuration
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: d0dc03db-5f76-4558-b041-1ac7b9b5bb16
caps.latest.revision: 8
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5ad6f90d1165e1c7097425edfa13dd58e3a56681
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38035082"
---
# <a name="sql-full-text-filter-daemon-launcher-sql-server-configuration-manager"></a>Средство запуска управляющей программы полнотекстовой фильтрации SQL (диспетчер конфигурации SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
  Начиная с версии [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], в полнотекстовом поиске [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] используется средство запуска управляющей программы полнотекстовой фильтрации SQL (средство запуска FDHOST) для запуска хост-процесса управляющей программы полнотекстовой фильтрации, которая выполняет фильтрацию полнотекстового поиска и разбиение по словам. Для использования полнотекстового поиска эта служба должна быть запущена. Средство запуска FDHOST представляет собой привязанную к экземпляру службу, которая связана с конкретным экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Эта служба передает сведения об учетной записи службы в каждый запущенный хост-процесс управляющей программы фильтрации. Сведения о хост-процессах управляющей программы фильтрации см. в разделе "Архитектура компонента Full-Text Search" электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
  
