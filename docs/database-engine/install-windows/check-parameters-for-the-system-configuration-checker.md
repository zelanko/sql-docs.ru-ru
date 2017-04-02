---
title: "Параметры для средства проверки конфигурации системы | Microsoft Docs"
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
  - "установка SQL Server, проверки конфигурации системы"
  - "неудачная проверка конфигурации системы [SQL Server]"
  - "проверка конфигурации перед установкой"
  - "SCC [SQL Server]"
  - "средство проверки конфигурации системы"
  - "обследование компьютера перед установкой [SQL Server]"
  - "проверка конфигурации перед установкой"
  - "сведения о состоянии [SQL Server], средство проверки конфигурации"
  - "параметры [SQL Server], средство проверки конфигурации"
  - "средства проверки конфигурации [SQL Server]"
  - "установка [SQL Server], средство проверки конфигурации"
ms.assetid: 8e712c15-6bfa-4d71-b303-9526101e5594
caps.latest.revision: 46
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 46
---
# Параметры для средства проверки конфигурации системы
  Во время установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] средство проверки конфигурации системы (SCC) просматривает компьютер, на котором устанавливается [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Средство SCC проверяет наличие условий, препятствующих успешной установке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Прежде чем программа установки запустит мастер установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , SCC получает сведения о состоянии каждого элемента. Затем оно сравнивает результаты с требуемыми условиями и предоставляет рекомендации по устранению критических препятствий.  
  
 Средство проверки конфигурации создает отчет, содержащий краткое описание всех выполненных правил и состояние выполнения. Отчет о проверке конфигурации системы находится в папке %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\130\Setup Bootstrap\Log\\<ГГГГММДД_ЧЧММ>\\.  
  
## См. также:  
 [Требования к оборудованию и программному обеспечению для установки SQL Server 2016](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server-2016.md)   
 [Вопросы безопасности при установке SQL Server](../../sql-server/install/security-considerations-for-a-sql-server-installation.md)   
 [Поддерживаемые обновления версий и выпусков](../../database-engine/install-windows/supported-version-and-edition-upgrades.md)  
  
  