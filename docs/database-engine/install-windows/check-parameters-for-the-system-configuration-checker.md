---
title: Параметры для средства проверки конфигурации системы | Документы Майкрософт
ms.custom: ''
ms.date: 09/05/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: install
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- installing SQL Server, system configuration checks
- failed system configuration checks [SQL Server]
- verifying configuration before installation
- SCC [SQL Server]
- system configuration checker
- scanning computer before installation [SQL Server]
- checking configuration before installation
- status information [SQL Server], system configuration checker
- parameters [SQL Server], system configuration checker
- configuration checkers [SQL Server]
- Setup [SQL Server], system configuration checker
ms.assetid: 8e712c15-6bfa-4d71-b303-9526101e5594
caps.latest.revision: 46
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 374b5a6aa993957ad83f44a6561a2d63a8966b2b
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2018
ms.locfileid: "34771360"
---
# <a name="check-parameters-for-the-system-configuration-checker"></a>Параметры для средства проверки конфигурации системы

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Во время установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] средство проверки конфигурации системы (SCC) просматривает компьютер, на котором устанавливается [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Средство SCC проверяет наличие условий, препятствующих успешной установке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Прежде чем программа установки запустит мастер установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , SCC получает сведения о состоянии каждого элемента. Затем оно сравнивает результаты с требуемыми условиями и предоставляет рекомендации по устранению критических препятствий.  
  
Средство проверки конфигурации создает отчет, содержащий краткое описание всех выполненных правил и состояние выполнения. Отчет о проверке конфигурации системы находится в папке %programfiles%\Microsoft SQL Server\140\Setup Bootstrap\Log\\\<ГГГГММДД_ЧЧММ>\\\..    
  
Дополнительные сведения см. по следующим ссылкам:

- [Требования к оборудованию и программному обеспечению для установки SQL Server](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)   
- [Вопросы безопасности при установке SQL Server](../../sql-server/install/security-considerations-for-a-sql-server-installation.md)   
- [Поддерживаемые обновления версий и выпусков](../../database-engine/install-windows/supported-version-and-edition-upgrades.md)  
  
  
