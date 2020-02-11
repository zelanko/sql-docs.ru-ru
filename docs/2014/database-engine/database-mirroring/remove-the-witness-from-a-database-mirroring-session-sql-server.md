---
title: Удаление следящего сервера из сеанса зеркального отображения базы данных (SQL Server) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- witness [SQL Server], turning off
- witness [SQL Server], removing
- database mirroring [SQL Server], witness
ms.assetid: f3ce7afc-8936-4d35-80ce-d0f8fbc318d3
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 0fee60fa1a78c2d6d0becb63b2319105016adf1c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62754667"
---
# <a name="remove-the-witness-from-a-database-mirroring-session-sql-server"></a>Удаление следящего сервера из сеанса зеркального отображения базы данных (SQL Server)
  В этом разделе описано, как удалить следящий сервер из сеанса зеркального отображения базы данных [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]. Во время сеанса зеркального отображения владелец базы данных в любой момент может отключить следящий сервер для сеанса зеркального отображения базы данных.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Безопасность](#Security)  
  
-   **Для замены удалите следящий сервер с помощью:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Дальнейшие действия.**  [после удаления следящего сервера](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Необходимо разрешение ALTER на базу данных.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-remove-the-witness"></a>Удаление следящего сервера  
  
1.  Установите соединение с экземпляром основного сервера и на панели **Обозреватель объектов** щелкните имя сервера, чтобы развернуть этот узел.  
  
2.  Раскройте **Базы данных**и выберите базу данных, для которой нужно удалить следящий сервер.  
  
3.  Щелкните базу данных правой кнопкой мыши, выберите **Задачи**, а затем **Зеркальное отображение**. Откроется страница **Зеркальное отображение** диалогового окна **Свойства базы данных** .  
  
4.  Чтобы удалить следящий сервер, удалите его сетевой адрес из поля **Следящий** .  
  
    > [!NOTE]  
    >  При переключении из режима высокого уровня безопасности с автоматической отработкой отказа в высокопроизводительный режим поле **Следящий** автоматически очищается.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-remove-the-witness"></a>Удаление следящего сервера  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)] на экземпляре любого из серверов-участников.  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Выполните следующую инструкцию:  
  
     [ALTER database](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) *DATABASE_NAME* Set свидетель Off  
  
     где *имя_базы_данных* — имя зеркально отображаемой базы данных.  
  
     В следующем примере показано удаление следящего сервера для базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] .  
  
    ```  
    ALTER DATABASE AdventureWorks2012 SET WITNESS OFF ;  
    ```  
  
##  <a name="FollowUp"></a>Дальнейшие действия. После удаления следящего сервера  
 При отключении следящего сервера [режим работы](database-mirroring-operating-modes.md)изменяется в соответствии с параметром безопасности транзакций.  
  
-   Если уровень безопасности транзакций установлен в FULL (значение по умолчанию), то сеанс использует синхронный режим с высоким уровнем защиты без автоматической отработки отказа.  
  
-   Когда безопасность транзакций отключена, сеанс работает асинхронно (в режиме высокой производительности), не требуя кворума. При отключенной безопасности транзакций настоятельно рекомендуется также отключить следящий сервер.  
  
> [!TIP]  
>  Параметры безопасности транзакций для каждого участника на экземпляре сервера доступны через представление каталога [sys.database_mirroring](/sql/relational-databases/system-catalog-views/sys-database-mirroring-transact-sql), в столбцах **mirroring_safety_level** и **mirroring_safety_level_desc**.  
  
##  <a name="RelatedTasks"></a> Связанные задачи  
  
-   [Добавление следящего сервера зеркального отображения базы данных с использованием проверки подлинности Windows &#40;Transact-SQL&#41;](add-a-database-mirroring-witness-using-windows-authentication-transact-sql.md)  
  
-   [Добавление или замена следящего сервера зеркального отображения базы данных &#40;SQL Server Management Studio&#41;](../database-mirroring/add-or-replace-a-database-mirroring-witness-sql-server-management-studio.md)  
  
## <a name="see-also"></a>См. также:  
 [&#41;Transact-SQL для зеркального отображения базы данных ALTER DATABASE &#40;](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring)   
 [Изменение безопасности транзакций в сеансе зеркального отображения базы данных &#40;&#41;Transact-SQL](change-transaction-safety-in-a-database-mirroring-session-transact-sql.md)   
 [Добавление следящего сервера зеркального отображения базы данных с использованием проверки подлинности Windows &#40;Transact-SQL&#41;](add-a-database-mirroring-witness-using-windows-authentication-transact-sql.md)   
 [Database Mirroring Witness](database-mirroring-witness.md)  
  
  
