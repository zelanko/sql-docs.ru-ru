---
title: Размещение базы данных сервера отчетов в отказоустойчивом кластере SQL Server | Документы Майкрософт
ms.custom: ''
ms.date: 08/10/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7bd5f019-2857-452f-a023-cc3b9e93aec4
caps.latest.revision: 4
author: markingmyname
ms.author: maghan
manager: jhubbard
ms.openlocfilehash: d2a0a0fc008c2bdb08786d7cf32f76310f259b6d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36096078"
---
# <a name="host-a-report-server-database-in-a-sql-server-failover-cluster"></a>Размещение базы данных сервера отчетов в отказоустойчивом кластере SQL Server
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предоставляет поддержку отказоустойчивой кластеризации, поэтому можно использовать несколько дисков для одного или более экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Отказоустойчивая кластеризация поддерживается только для базы данных сервера отчетов, служба Report Server не может работать как часть отказоустойчивого кластера.  
  
 Чтобы разместить базу данных сервера отчетов в отказоустойчивом кластере [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , кластер должен быть предварительно установлен и настроен. После этого можно выбрать отказоустойчивый кластер в качестве имени сервера при создании базы данных сервера отчетов на странице «Настройка базы данных» программы настройки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
 Хотя служба Report Server и не может быть частью отказоустойчивого кластера, службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] можно установить на компьютере с установленным отказоустойчивым кластером [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Сервер отчетов работает независимо от отказоустойчивого кластера. При установке сервера отчетов на компьютере, являющемся частью экземпляра отработки отказа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не обязательно использовать отказоустойчивый кластер для базы данных сервера отчетов. Для размещения базы данных можно использовать другой экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="see-also"></a>См. также  
 [База данных сервера отчетов &#40;собственный режим служб SSRS&#41;](../report-server/report-server-database-ssrs-native-mode.md)   
 [Создать базу данных сервера отчетов &#40;диспетчер конфигурации служб SSRS&#41;](../../sql-server/install/create-a-report-server-database-ssrs-configuration-manager.md)  
  
  