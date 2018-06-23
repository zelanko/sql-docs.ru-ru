---
title: Свойства общей памяти | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- configmgr-client
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- shared memory [SQL Server]
ms.assetid: dc1704da-eacd-4d26-b529-c996f958ca4b
caps.latest.revision: 20
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 3ff71e8b8e4bfd3de68adc401c4871be92614acc
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36189158"
---
# <a name="shared-memory-properties"></a>Свойства общей памяти
  Используйте страницу **Протокол** в диалоговом окне **Свойства общей памяти**, чтобы включить или выключить протокол общей памяти. Общая память является простейшим протоколом и не имеет настраиваемых параметров. Поскольку клиенты, использующие протокол общей памяти, могут подключаться только к экземпляру [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , запущенному на том же компьютере, этот протокол не подходит для большинства операций с базами данных. Используйте протокол общей памяти, чтобы устранить неполадки, если есть вероятность того, что другие протоколы настроены некорректно.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должен быть перезапущен, чтобы включить или отключить протокол.  
  
## <a name="options"></a>Параметры  
 **Enabled**  
 Возможные значения: **Да** и **Нет**. По умолчанию протокол общей памяти включен.  
  
## <a name="see-also"></a>См. также  
 [Выбор сетевого протокола](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md)   
 [Создание допустимой строки соединения с использованием протокола общей памяти](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-shared-memory-protocol.md)  
  
  