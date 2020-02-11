---
title: Свойства общей памяти | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- shared memory [SQL Server]
ms.assetid: dc1704da-eacd-4d26-b529-c996f958ca4b
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: bea56ada3ef490225fd08892128abb482b9342a8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62999540"
---
# <a name="shared-memory-properties"></a>Свойства общей памяти
  Используйте страницу **Протокол** в диалоговом окне **Свойства общей памяти**, чтобы включить или выключить протокол общей памяти. Общая память является простейшим протоколом и не имеет настраиваемых параметров. Поскольку клиенты, использующие протокол общей памяти, могут подключаться [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] только к экземпляру, выполняющемуся на том же компьютере, он не полезен для большинства операций с базой данных. Используйте протокол общей памяти, чтобы устранить неполадки, если есть вероятность того, что другие протоколы настроены некорректно.  
  
 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должен быть перезапущен, чтобы включить или отключить протокол.  
  
## <a name="options"></a>Параметры  
 **Enabled**  
 Возможные значения: **Да** и **Нет**. По умолчанию протокол общей памяти включен.  
  
## <a name="see-also"></a>См. также:  
 [Выбор сетевого протокола](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md)   
 [Создание допустимой строки соединения с использованием протокола общей памяти](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-shared-memory-protocol.md)  
  
  
