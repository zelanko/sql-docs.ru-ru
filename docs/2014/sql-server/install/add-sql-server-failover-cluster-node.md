---
title: Добавление узла отказоустойчивого кластера SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: e5035122-784f-40ee-8188-7f485a9ae3e8
caps.latest.revision: 20
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c865f7866b6fd0985d26575762871c4bc57a8269
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37226544"
---
# <a name="add-sql-server-failover-cluster-node"></a>Добавление узла отказоустойчивого кластера SQL Server
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Программа установки проверяет конфигурацию компьютера перед началом установки. Во время установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] средство проверки конфигурации системы (SCC) просматривает компьютер, на котором устанавливается [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Средство SCC проверяет наличие условий, препятствующих успешной установке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Прежде чем программа установки запустит мастер установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , SCC получает сведения о состоянии каждого элемента. Затем оно сравнивает результаты с требуемыми условиями и предоставляет рекомендации по устранению критических препятствий.  
  
 При проверке конфигурации системы создается отчет, содержащий краткое описание всех выполненных правил и состояния выполнения. Отчет о проверке конфигурации системы находится в %programfiles%\Microsoft SQL Server\120\Setup Bootstrap\Log\\< ггггммдд_ччмм >\\.  
  
 Прежде чем начинать установку, ознакомьтесь со следующими разделами:  
  
1.  [Требования к оборудованию и программному обеспечению для установки SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md)  
  
2.  [Возможности, поддерживаемые различными выпусками SQL Server 2014](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)  
  
3.  [Вопросы безопасности при установке SQL Server](../../../2014/sql-server/install/security-considerations-for-a-sql-server-installation.md)  
  
4.  [Версии SQL Server на местных языках](../../../2014/sql-server/install/local-language-versions-in-sql-server.md)  
  
 Другие ссылки:  
  
1.  [Поддерживаемые обновления версий и выпусков](../../database-engine/install-windows/supported-version-and-edition-upgrades.md)  
  
2.  [Подготовка к установке отказоустойчивого кластера](../failover-clusters/install/before-installing-failover-clustering.md)  
  
## <a name="see-also"></a>См. также  
 [Правила установки](../../../2014/sql-server/install/install-rules.md)  
  
  
