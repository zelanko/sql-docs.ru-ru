---
title: Средство запуска управляющей программы полнотекстовой фильтрации SQL (диспетчер конфигурации SQL Server) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: d0dc03db-5f76-4558-b041-1ac7b9b5bb16
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1ca6dc3f6cd15a799d3b110fb446be821de679c9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "63137573"
---
# <a name="sql-full-text-filter-daemon-launcher-sql-server-configuration-manager"></a>Средство запуска управляющей программы полнотекстовой фильтрации SQL (диспетчер конфигурации SQL Server)
  Начиная с версии [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], в полнотекстовом поиске [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] используется средство запуска управляющей программы полнотекстовой фильтрации SQL (средство запуска FDHOST) для запуска хост-процесса управляющей программы полнотекстовой фильтрации, которая выполняет фильтрацию полнотекстового поиска и разбиение по словам. Для использования полнотекстового поиска эта служба должна быть запущена. Средство запуска FDHOST представляет собой привязанную к экземпляру службу, которая связана с конкретным экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Эта служба передает сведения об учетной записи службы в каждый запущенный хост-процесс управляющей программы фильтрации. Сведения о хост-процессах управляющей программы фильтрации см. в разделе «Архитектура компонента Full-Text Search» электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
  
