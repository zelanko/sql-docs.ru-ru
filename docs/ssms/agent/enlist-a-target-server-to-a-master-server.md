---
description: Прикрепление целевого сервера к главному
title: Прикрепление целевого сервера к главному
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- enlisting target servers [SQL Server]
- SQL Server Agent jobs, target servers
- master servers [SQL Server], enlisting target servers
- SQL Server Agent jobs, master servers
- target servers [SQL Server], enlisting
ms.assetid: 7633adb5-d140-4e58-a8f2-5b4b50c2f95b
author: markingmyname
ms.author: maghan
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: b75aca103c33ff30a2f524c511420e79b7e01a7f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88480429"
---
# <a name="enlist-a-target-server-to-a-master-server"></a>Прикрепление целевого сервера к главному
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> В [Управляемом экземпляре Azure SQL](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) в настоящее время поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия в T-SQL между Управляемым экземпляром SQL Azure и SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

В этом разделе описывается, как добавить целевые серверы в конфигурацию администрирования нескольких серверов. Запустите эту процедуру с главного сервера. В [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)]или управляющих объектов SQL Server (SMO).  
  
Дополнительные сведения о влиянии учетной записи Windows для службы агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на многосерверную среду см. в разделе [Создание многосерверной среды](../../ssms/agent/create-a-multiserver-environment.md).  
  
Для соединений между главными и целевыми серверами по умолчанию включено полное шифрование протокола защиты транспортного уровня (TLS), заменившего SSL, и проверка сертификата. Дополнительные сведения см. в статье [Установка параметров шифрования на целевых серверах](../../ssms/agent/set-encryption-options-on-target-servers.md).  
  
## <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a>Использование среды SQL Server Management Studio  
  
#### <a name="to-enlist-a-target-server"></a>Прикрепление целевого сервера  
  
1.  В **Обозревателе объектов**разверните главный сервер.  
  
2.  Щелкните правой кнопкой мыши элемент **Агент SQL Server**, укажите пункт **Администрирование нескольких серверов**, а затем выберите пункт **Добавление целевых серверов**.  
  
3.  Завершите работу мастера настройки целевого сервера, который проводит пользователя по этапам процесса.  
  
## <a name="using-transact-sql"></a><a name="TsqlProcedure"></a>Использование Transact-SQL  
  
#### <a name="to-enlist-a-target-server"></a>Прикрепление целевого сервера  
  
1.  Используйте хранимую процедуру **sp_msx_enlist** .  Дополнительные сведения см. в разделе [sp_msx_enlist (Transact-SQL)](https://msdn.microsoft.com/ceb3b2bc-0cc4-48d8-9bdc-6a809556e35f).  
  
## <a name="see-also"></a>См. также:  
[Автоматизация администрирования в масштабах предприятия](../../ssms/agent/automated-administration-across-an-enterprise.md)  
  
