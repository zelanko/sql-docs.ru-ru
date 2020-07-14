---
title: Изменение настроек конфигурации базы данных | Документация Майкрософт
description: Узнайте, как в SQL Server 2019 изменить параметры уровня БД с помощью SQL Server Management Studio или Transact-SQL.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- database configuration [SQL Server]
- configuration options [SQL Server], databases
- modifying database configuration settings
ms.assetid: c29c3385-5043-400f-bb4e-044a4c9a9a4b
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: bec4ac42635494ae49573d353314d4e156684328
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85679607"
---
# <a name="change-the-configuration-settings-for-a-database"></a>Изменение настроек конфигурации базы данных
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  В этом разделе описывается изменение параметров уровня базы данных в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]. Эти параметры уникальны для каждой базы данных и не влияют на другие базы данных.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [Безопасность](#Security)  
  
-   **Изменение настроек параметров для базы данных с помощью различных средств.**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Ограничения  
  
-   Только системный администратор, владелец базы данных, члены предопределенной роли сервера **sysadmin** и **dbcreator** и предопределенной роли базы данных **db_owner** могут изменять эти параметры.  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Необходимо разрешение ALTER на базу данных.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-change-the-option-settings-for-a-database"></a>Изменение настроек параметров для базы данных  
  
1.  В обозревателе объектов подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] , разверните сервер, разверните узел **Базы данных**, щелкните правой кнопкой мыши базу данных и выберите пункт **Свойства**.  
  
2.  В диалоговом окне **Свойства базы данных** щелкните **Параметры** для обращения к большинству настроек конфигурации. Конфигурации файла и файловой группы, зеркального отображения и доставки журналов находятся на соответствующих им страницах.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-change-the-option-settings-for-a-database"></a>Изменение настроек параметров для базы данных  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере задается модель восстановления и параметры проверки страницы данных для образца базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] .  
  
 [!code-sql[DatabaseDDL#AlterDatabase7](../../relational-databases/databases/codesnippet/tsql/change-the-configuration_1.sql)]  
  
 Дополнительные сведения см. в статье [Параметры ALTER DATABASE SET (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql-set-options.md).  
  
## <a name="see-also"></a>См. также:  
 [Уровень совместимости инструкции ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md)   
 [Зеркальное отображение базы данных ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql-database-mirroring.md)   
 [ALTER DATABASE SET HADR (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql-set-hadr.md)   
 [Переименование базы данных](../../relational-databases/databases/rename-a-database.md)   
 [Сжатие базы данных](../../relational-databases/databases/shrink-a-database.md)  
  
  
