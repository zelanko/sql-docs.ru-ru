---
title: Общие сведения о процессе обновления | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- upgrading SQL Server
- Upgrade Advisor [SQL Server], process description
- SQL Server Upgrade Advisor, process description
- upgrade process [Upgrade Advisor]
ms.assetid: f77ffbab-a195-4124-acce-9c538f7ca9ce
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: fb4bfb2073427d0f48b3d4a7ac7b7ab496299030
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66091521"
---
# <a name="upgrade-process-overview"></a>Общие сведения о процессе обновления
  В этом разделе содержатся рекомендации для советника по переходу [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и сводка рекомендованных процедур для обновления до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
## <a name="upgrade-process"></a>Процесс обновления  
 Серверы, работающие с [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] или [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], могут быть обновлены до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Некоторые компоненты [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно обновить на месте, другие необходимо перенести, а некоторые нужно заменить новым компонентом. Например, начиная с [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ([!INCLUDE[ssIS](../../includes/ssis-md.md)]) заменяют службы DTS, которые больше не поддерживаются в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. При формировании плана обновления необходимо определить, будут ли текущие пакеты служб DTS обновлены до пакетов служб [!INCLUDE[ssIS](../../includes/ssis-md.md)].  
  
 Помощник по обновлению позволяет оценить текущие установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], компоненты и связанные файлы, чтобы выявить известные неполадки, которые вызовут проблемы в процессе и после обновления или перехода на [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Некоторые из них могут привести к невозможности обновления до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. В отчете помощника по обновлению эти проблемы определены как блокировщики обновления. Если препятствия к обновлению не устранены до запуска программы установки, то установка [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] будет прекращена с рекомендацией запустить помощник по обновлению, чтобы выявить конкретные проблемы, которые не позволяют его выполнить.  
  
 Перед началом обновления до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] рекомендуется создать резервную копию данных и системных настроек и выполнить стратегические шаги, перечисленные в рабочих правилах, принятых в компании. Для завершения обновления выполните следующие шаги.  
  
1.  Обратитесь к разделу [Hardware and Software Requirements for Installing SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md).  
  
2.  Создайте резервную копию данных и системных настроек.  
  
3.  Запустите помощник по обновлению.  
  
     Помощник по обновлению не изменяет данные или параметры компьютера.  
  
4.  Просмотрите проблемы, выявленные в отчете помощника по обновлению.  
  
5.  Устраните любые критические препятствия, которые не позволяют выполнить обновление до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
6.  Устраните любые проблемы, связанные с подготовкой к обновлению.  
  
7.  Запустите помощник по обновлению, чтобы убедиться, что все известные проблемы устранены.  
  
8.  Запустите программу установки [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] .  
  
9. Устраните любые проблемы, возникающие после обновления и миграции.  
  
## <a name="see-also"></a>См. также  
 [Запуск помощника по обновлению &#40;пользовательского интерфейса&#41;](../../../2014/sql-server/install/running-upgrade-advisor-user-interface.md)   
 [С помощью отчетов](../../../2014/sql-server/install/using-reports.md)   
 [Работа с помощником по обновлению](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
