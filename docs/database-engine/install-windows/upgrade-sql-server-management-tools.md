---
title: "Обновление средств управления SQL Server | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "setup-install"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "средства управления, обновление"
ms.assetid: 1dab50b9-d16c-49a1-9ecc-af72adb6c378
caps.latest.revision: 19
author: "stevestein"
ms.author: "sstein"
manager: "jhubbard"
caps.handback.revision: 19
---
# Обновление средств управления SQL Server
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] поддерживает обновление с версии [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] или более поздней. В этом разделе описаны средства поддержки и процесс обновления средств управления [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , компонента Database Mail, планов обслуживания, XPStar, XPWeb и других компонентов управления.  
  
> [!IMPORTANT]  
>  Для локальных установок программу установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] нужно запускать с правами администратора. При установке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] из удаленной общей папки необходимо пользоваться учетной записью домена, имеющей разрешения на чтение и выполнение для удаленной общей папки.  
  
## Известные проблемы при обновлении  
 Прежде чем приступать к обновлению до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], необходимо учесть следующие моменты.  
  
### Для всех сценариев обновления  
  
-   Перед обновлением главного сервера должны быть обновлены все целевые серверы. Дополнительные сведения о главных и целевых серверах [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] см. в статье [Автоматизация администрирования в масштабах предприятия](../../ssms/agent/automated-administration-across-an-enterprise.md).  
  
-   Все компоненты экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должны быть обновлены одновременно. Компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)], а также службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]и [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] должны иметь один и тот же номер версии для одного экземпляра [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
-   При обновлении до [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] к существующей установке [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] могут быть добавлены новые компоненты. Дополнительные сведения см. в статье [Обновление до SQL Server 2016 с помощью мастера установки (программы установки)](../../database-engine/install-windows/upgrade-to-sql-server-2016-using-the-installation-wizard-setup.md).  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , такие как [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], помощник по настройке компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] , sqlcmd и osql, до версии [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Клиентские средства запускаются параллельно с компонентами предыдущих версий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] поддерживает импорт параметров из предыдущих версий клиентских средств [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Проверка подлинности из агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] будет переключена из режима [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в режим Windows, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
-   После обновления до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]данные заданий и предупреждений сохранятся.  
  
-   Если в обновляемом экземпляре используется программа SQLMail, то связанные с ней расширенные хранимые процедуры после обновления будут сохранены и включены. В противном случае они будут отключены.  
  
-   При обновлении [!INCLUDE[ssDE](../../includes/ssde-md.md)] компонент Database Mail (также называемый SQLiMail) обновляется одновременно с компонентом [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. По умолчанию после обновления компонент Database Mail отключается. Все изменения схемы после этого должны быть согласованы со скриптом обновления.  
  
## См. также:  
 [Поддерживаемые обновления версий и выпусков](../../database-engine/install-windows/supported-version-and-edition-upgrades.md)   
 [Обратная совместимость_удалено](../Topic/Backward%20Compatibility_deleted.md)   
 [Обновление до SQL Server 2016 с помощью мастера установки (программа установки)](../../database-engine/install-windows/upgrade-to-sql-server-2016-using-the-installation-wizard-setup.md)  
  
  