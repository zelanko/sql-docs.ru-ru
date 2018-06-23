---
title: Параметр конфигурации сервера "cross db ownership chaining" | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cross-database ownership chaining
- cross db ownership chaining option
- chaining ownership
ms.assetid: 7b2d49f2-b91c-4aee-a52b-6cc49bed03af
caps.latest.revision: 26
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 0eeedb591ad2a7f3330a9dae53f4982e16489b8d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36100924"
---
# <a name="cross-db-ownership-chaining-server-configuration-option"></a>Параметр конфигурации сервера «cross db ownership chaining»
  Используйте параметр **cross db ownership chaining** , чтобы настроить межбазовые цепочки владения для экземпляра [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Этот серверный параметр позволяет управлять межбазовыми цепочками владения на уровне базы данных и обеспечивает применение межбазовых цепочек владения для всех баз данных:  
  
-   Если параметр **cross db ownership chaining** отключен для экземпляра (0), межбазовые цепочки владения выключены для всех баз данных.  
  
-   Если параметр **cross db ownership chaining** включен для экземпляра (1), межбазовые цепочки владения включены для всех баз данных.  
  
-   Межбазовые цепочки владения для отдельных баз данных можно установить с помощью предложения SET инструкции ALTER DATABASE. При создании новой базы данных параметр cross db ownership chaining можно установить с использованием инструкции CREATE DATABASE.  
  
     Не рекомендуется присваивать параметру **cross db ownership chaining** значение "1", за исключением ситуаций, когда все базы данных, размещенные на экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , должны участвовать в межбазовой цепочке владения и известно влияние данного значения на безопасность.  
  
## <a name="controlling-cross-database-ownership-chaining"></a>Управление межбазовыми цепочками владения  
 Прежде чем включить или выключить межбазовые цепочки владения, следует учесть следующие факторы:  
  
-   Для включения и выключения межбазовых цепочек владения необходимо быть членом предопределенной роли сервера **sysadmin** .  
  
-   Прежде чем отключить межбазовые цепочки владения на производственном сервере, проведите полное тестирование всех приложений, в том числе приложений от сторонних поставщиков, чтобы убедиться, что изменения не влияют на функциональность приложений.  
  
-   Можно изменить параметр **cross db ownership chaining** на активном сервере, если указать RECONFIGURE как хранимую процедуру **sp_configure**.  
  
-   При работе с базами данных, требующими межбазовых цепочек владения, рекомендуется отключить параметр **cross db ownership chaining** для экземпляра с помощью хранимой процедуры **sp_configure**; затем с помощью инструкции ALTER DATABASE следует включить межбазовые цепочки владения для отдельных баз данных, если это требуется.  
  
## <a name="see-also"></a>См. также  
 [ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql)   
 [CREATE DATABASE (SQL Server Transact-SQL)](/sql/t-sql/statements/create-database-sql-server-transact-sql)   
 [Параметры конфигурации сервера (SQL Server)](server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)   
 [RECONFIGURE (Transact-SQL)](/sql/t-sql/language-elements/reconfigure-transact-sql)  
  
  
