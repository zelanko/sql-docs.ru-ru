---
title: Изменение настроек конфигурации базы данных | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: databases
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- database configuration [SQL Server]
- configuration options [SQL Server], databases
- modifying database configuration settings
ms.assetid: c29c3385-5043-400f-bb4e-044a4c9a9a4b
caps.latest.revision: 29
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 8cab180d0d82157c346fe25ade6a54ee853fbe60
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43062749"
---
# <a name="change-the-configuration-settings-for-a-database"></a>Изменение настроек конфигурации базы данных
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  В этом разделе описывается изменение параметров уровня базы данных в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]. Эти параметры уникальны для каждой базы данных и не влияют на другие базы данных.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [безопасность](#Security)  
  
-   **Изменение настроек параметров для базы данных с помощью различных средств.**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   Только системный администратор, владелец базы данных, члены предопределенной роли сервера **sysadmin** и **dbcreator** и предопределенной роли базы данных **db_owner** могут изменять эти параметры.  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Необходимо разрешение ALTER на базу данных.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-change-the-option-settings-for-a-database"></a>Изменение настроек параметров для базы данных  
  
1.  В обозревателе объектов подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] , разверните сервер, разверните узел **Базы данных**, щелкните правой кнопкой мыши базу данных и выберите пункт **Свойства**.  
  
2.  В диалоговом окне **Свойства базы данных** щелкните **Параметры** для обращения к большинству настроек конфигурации. Конфигурации файла и файловой группы, зеркального отображения и доставки журналов находятся на соответствующих им страницах.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-change-the-option-settings-for-a-database"></a>Изменение настроек параметров для базы данных  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере задается модель восстановления и параметры проверки страницы данных для образца базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
 [!code-sql[DatabaseDDL#AlterDatabase7](../../relational-databases/databases/codesnippet/tsql/change-the-configuration_1.sql)]  
  
 Дополнительные сведения см. в статье [Параметры ALTER DATABASE SET (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql-set-options.md).  
  
## <a name="see-also"></a>См. также:  
 [Уровень совместимости инструкции ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md)   
 [Зеркальное отображение базы данных ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql-database-mirroring.md)   
 [ALTER DATABASE SET HADR (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql-set-hadr.md)   
 [Переименование базы данных](../../relational-databases/databases/rename-a-database.md)   
 [Сжатие базы данных](../../relational-databases/databases/shrink-a-database.md)  
  
  
