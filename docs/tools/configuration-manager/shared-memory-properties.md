---
title: "Свойства общей памяти | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: shared memory [SQL Server]
ms.assetid: dc1704da-eacd-4d26-b529-c996f958ca4b
caps.latest.revision: "21"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f974671a3d3d7bb63b52ace33634fe00f936f290
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="shared-memory-properties"></a>Свойства общей памяти
  Используйте страницу **Протокол**в диалоговом окне **Свойства общей памяти** , чтобы включить или выключить протокол общей памяти. Общая память является простейшим протоколом и не имеет настраиваемых параметров. Поскольку клиенты, использующие протокол общей памяти, могут подключаться только к экземпляру [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , запущенному на том же компьютере, этот протокол не подходит для большинства операций с базами данных. Используйте протокол общей памяти, чтобы устранить неполадки, если есть вероятность того, что другие протоколы настроены некорректно.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должен быть перезапущен, чтобы включить или отключить протокол.  
  
## <a name="options"></a>Параметры  
 **Enabled**  
 Возможные значения: **Да** и **Нет**. По умолчанию протокол общей памяти включен.  
  
## <a name="see-also"></a>См. также  
 [Выбор сетевого протокола](http://msdn.microsoft.com/library/6565fb7d-b076-4447-be90-e10d0dec359a)   
 [Создание допустимой строки соединения с использованием протокола общей памяти](../../tools/configuration-manager/creating-a-valid-connection-string-using-shared-memory-protocol.md)  
  
  
