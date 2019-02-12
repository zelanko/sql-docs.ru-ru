---
title: Размещение базы данных сервера отчетов в отказоустойчивом кластере SQL Server | Документы Майкрософт
ms.custom: ''
ms.date: 08/10/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 7bd5f019-2857-452f-a023-cc3b9e93aec4
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 2f5d07383c2a312747cff94508ab2397f402793c
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/11/2019
ms.locfileid: "56043159"
---
# <a name="host-a-report-server-database-in-a-sql-server-failover-cluster"></a>Размещение базы данных сервера отчетов в отказоустойчивом кластере SQL Server
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предоставляет поддержку отказоустойчивой кластеризации, поэтому можно использовать несколько дисков для одного или более экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Отказоустойчивая кластеризация поддерживается только для базы данных сервера отчетов, служба Report Server не может работать как часть отказоустойчивого кластера.  
  
 Чтобы разместить базу данных сервера отчетов в отказоустойчивом кластере [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , кластер должен быть предварительно установлен и настроен. После этого можно выбрать отказоустойчивый кластер в качестве имени сервера при создании базы данных сервера отчетов на странице «Настройка базы данных» программы настройки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
 Хотя служба Report Server и не может быть частью отказоустойчивого кластера, службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] можно установить на компьютере с установленным отказоустойчивым кластером [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Сервер отчетов работает независимо от отказоустойчивого кластера. При установке сервера отчетов на компьютере, являющемся частью экземпляра отработки отказа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не обязательно использовать отказоустойчивый кластер для базы данных сервера отчетов. Для размещения базы данных можно использовать другой экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="see-also"></a>См. также  
 [База данных сервера отчетов (службы Reporting Services в собственном режиме)](../report-server/report-server-database-ssrs-native-mode.md)   
 [Создание базы данных сервера отчетов (диспетчер конфигурации служб SSRS)](../../sql-server/install/create-a-report-server-database-ssrs-configuration-manager.md)  
  
  
