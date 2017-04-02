---
title: "Изменение настроек конфигурации базы данных | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "конфигурация базы данных [SQL Server]"
  - "параметры конфигурации [SQL Server], базы данных"
  - "изменение параметров конфигурации базы данных"
ms.assetid: c29c3385-5043-400f-bb4e-044a4c9a9a4b
caps.latest.revision: 29
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 29
---
# Изменение настроек конфигурации базы данных
  В этом разделе описывается изменение параметров уровня базы данных в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]. Эти параметры уникальны для каждой базы данных и не влияют на другие базы данных.  
  
 **В этом разделе**  
  
-   **Перед началом работы выполните следующие действия.**  
  
     [Ограничения](#Restrictions)  
  
     [Безопасность](#Security)  
  
-   **Изменение настроек параметров для базы данных с помощью различных средств.**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   Только системный администратор, владелец базы данных, члены предопределенной роли сервера **sysadmin** и **dbcreator** и предопределенной роли базы данных **db_owner** могут изменять эти параметры.  
  
###  <a name="Security"></a> Безопасность  
  
####  <a name="Permissions"></a> Разрешения  
 Необходимо разрешение ALTER на базу данных.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### Изменение настроек параметров для базы данных  
  
1.  В обозревателе объектов подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)], разверните сервер, разверните узел **Базы данных**, щелкните правой кнопкой мыши базу данных и выберите пункт **Свойства**.  
  
2.  В диалоговом окне **Свойства базы данных** щелкните **Параметры** для обращения к большинству настроек конфигурации. Конфигурации файла и файловой группы, зеркального отображения и доставки журналов находятся на соответствующих им страницах.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### Изменение настроек параметров для базы данных  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере задается модель восстановления и параметры проверки страницы данных для образца базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
 [!code-sql[DatabaseDDL#AlterDatabase7](../../relational-databases/databases/codesnippet/tsql/change-the-configuration_1.sql)]  
  
 Дополнительные сведения см. в статье [Параметры ALTER DATABASE SET (Transact-SQL)](../Topic/ALTER%20DATABASE%20SET%20Options%20\(Transact-SQL\).md).  
  
## См. также:  
 [Уровень совместимости инструкции ALTER DATABASE (Transact-SQL)](../Topic/ALTER%20DATABASE%20Compatibility%20Level%20\(Transact-SQL\).md)   
 [Зеркальное отображение базы данных ALTER DATABASE (Transact-SQL)](../Topic/ALTER%20DATABASE%20Database%20Mirroring%20\(Transact-SQL\).md)   
 [ALTER DATABASE SET HADR (Transact-SQL)](../Topic/ALTER%20DATABASE%20SET%20HADR%20\(Transact-SQL\).md)   
 [Переименование базы данных](../../relational-databases/databases/rename-a-database.md)   
 [Сжатие базы данных](../../relational-databases/databases/shrink-a-database.md)  
  
  