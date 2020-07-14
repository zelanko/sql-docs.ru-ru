---
title: Параметр конфигурации сервера "cross db ownership chaining" | Документы Майкрософт
description: Сведения об использовании параметра cross db ownership chaining в SQL Server. Факторы, которые необходимо учитывать при включении или выключении межбазовых цепочек владения.
ms.custom: ''
ms.date: 08/15/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- cross-database ownership chaining
- cross db ownership chaining option
- chaining ownership
ms.assetid: 7b2d49f2-b91c-4aee-a52b-6cc49bed03af
author: markingmyname
ms.author: maghan
ms.openlocfilehash: eefc2b48f43aa91afa982775829648d76856b392
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85772613"
---
# <a name="cross-db-ownership-chaining-server-configuration-option"></a>Параметр конфигурации сервера «cross db ownership chaining»
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Используйте параметр **cross db ownership chaining**, чтобы настроить межбазовые цепочки владения для экземпляра [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Этот серверный параметр позволяет управлять межбазовыми цепочками владения на уровне базы данных и обеспечивает применение межбазовых цепочек владения для всех баз данных:  
  
-   Если параметр **cross db ownership chaining** отключен для экземпляра (0), межбазовые цепочки владения выключены для всех баз данных.  
  
-   Если параметр **cross db ownership chaining** включен для экземпляра (1), межбазовые цепочки владения включены для всех баз данных.  
  
-   Межбазовые цепочки владения для отдельных баз данных можно установить с помощью предложения SET инструкции ALTER DATABASE. При создании новой базы данных параметр cross db ownership chaining можно установить с использованием инструкции CREATE DATABASE.  
  
     Не рекомендуется присваивать параметру **cross db ownership chaining** значение "1", за исключением ситуаций, когда все базы данных, размещенные на экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , должны участвовать в межбазовой цепочке владения и известно влияние данного значения на безопасность.  

Чтобы определить текущее состояние межбазовой цепочки владения, выполните следующий запрос.  
```sql
SELECT is_db_chaining_on, name FROM sys.databases;
```  
Значение 1 указывает, что включены межбазовые цепочки владения.

## <a name="controlling-cross-database-ownership-chaining"></a>Управление межбазовыми цепочками владения  
 Прежде чем включить или выключить межбазовые цепочки владения, следует учесть следующие факторы:  
  
-   Для включения и выключения межбазовых цепочек владения необходимо быть членом предопределенной роли сервера **sysadmin** .  
  
-   Прежде чем отключить межбазовые цепочки владения на производственном сервере, проведите полное тестирование всех приложений, в том числе приложений от сторонних поставщиков, чтобы убедиться, что изменения не влияют на функциональность приложений.  
  
-   Можно изменить параметр **cross db ownership chaining** на активном сервере, если указать RECONFIGURE как хранимую процедуру **sp_configure**.  
  
-   При работе с базами данных, требующими межбазовых цепочек владения, рекомендуется отключить параметр **cross db ownership chaining** для экземпляра с помощью хранимой процедуры **sp_configure**; затем с помощью инструкции ALTER DATABASE следует включить межбазовые цепочки владения для отдельных баз данных, если это требуется.  
  
## <a name="see-also"></a>См. также:  
 [ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql.md)   
 [CREATE DATABASE (SQL Server Transact-SQL)](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [RECONFIGURE (Transact-SQL)](../../t-sql/language-elements/reconfigure-transact-sql.md)  
  
  
