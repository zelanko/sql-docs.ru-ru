---
title: Удаление зеркального отображения базы данных (SQL Server) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], removing
- removing database mirroring [SQL Server]
ms.assetid: bbc4d7f7-3bc7-40d6-a822-af195fe7f8c0
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 55003fd84bbf25416d951342dbf2b9b4a2bb68dd
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84934055"
---
# <a name="remove-database-mirroring-sql-server"></a>Удаление зеркального отображения базы данных (SQL Server)
  В этом разделе описано, как удалить зеркальное отображение базы данных [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  Владелец базы данных может в любое время удалить зеркальное отображение базы данных. Для этого он должен вручную остановить сеанс.  
  
 
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Необходимо разрешение ALTER на базу данных.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-remove-database-mirroring"></a>Удаление зеркального отображения базы данных  
  
1.  Во время сеанса зеркального отображения базы данных установите соединение с экземпляром главного сервера, в обозревателе объектов щелкните имя сервера и разверните дерево сервера.  
  
2.  Разверните **Базы данных**и выберите нужную базу данных.  
  
3.  Щелкните базу данных правой кнопкой мыши, выберите **Задачи**, а затем **Зеркальное отображение**. Откроется страница **Зеркальное отображение** диалогового окна **Свойства базы данных** .  
  
4.  На панели **Выбор страницы** щелкните **Зеркальное отображение**.  
  
5.  Для удаления зеркального отображения нажмите **Отключить отображение**. Будет запрошено подтверждение. Если нажать кнопку **Да**, сеанс будет остановлен и зеркальное отображение будет удалено из этой базы данных.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
 Удалить зеркальное отображение базы данных можно в диалоговом окне **Свойства базы данных**. Откройте страницу **Зеркальное отображение** диалогового окна **Свойства базы данных** .  
  
#### <a name="to-remove-database-mirroring"></a>Удаление зеркального отображения базы данных  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)] любого из участников зеркального отображения.  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Выполните следующую инструкцию [!INCLUDE[tsql](../../includes/tsql-md.md)] :  
  
    ```  
    ALTER DATABASE database_name SET PARTNER OFF  
    ```  
  
     где *database_name* — зеркально отображаемая база данных, сеанс которой необходимо удалить.  
  
     В следующем примере удаляется зеркальное отображение образца базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] .  
  
    ```  
    ALTER DATABASE AdventureWorks2012 SET PARTNER OFF;  
    ```  
  
##  <a name="follow-up-removing-database-mirroring"></a><a name="FollowUp"></a>Дальнейшие действия. Удаление зеркального отображения базы данных  
  
> [!NOTE]  
>  Дополнительные сведения о последствиях удаления зеркального отображения базы данных см. в статье [Удаление зеркального отображения базы данных (SQL Server)](database-mirroring-sql-server.md).  
  
-   **Если планируется возобновление зеркального отображения базы данных**  
  
     Перед повторным запуском зеркального отображения к зеркальной базе данных необходимо применить все резервные копии журналов, созданные в основной базе данных перед удалением зеркального отображения.  
  
-   **Если возобновление зеркального отображения не планируется**  
  
     При необходимости можно восстановить прежнюю зеркальную базу данных. На экземпляре сервера, который был зеркальным сервером, можно выполнить следующую инструкцию [!INCLUDE[tsql](../../includes/tsql-md.md)] .  
  
    ```  
    RESTORE DATABASE database_name WITH RECOVERY;  
    ```  
  
    > [!IMPORTANT]  
    >  При восстановлении этой базы данных в режиме «в сети» будут доступны две разные базы данных с одним и тем же именем. Поэтому необходимо предусмотреть, чтобы у клиентов был доступ только к одной из них, обычно к новейшей основной базе данных.  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Связанные задачи  
  
-   [Приостановка или возобновление сеанса зеркального отображения базы данных (SQL Server)](pause-or-resume-a-database-mirroring-session-sql-server.md)  
  
-   [Удаление следящего сервера из сеанса зеркального отображения базы данных (SQL Server)](remove-the-witness-from-a-database-mirroring-session-sql-server.md)  
  
-   [Создание сеанса зеркального отображения базы данных с использованием проверки подлинности Windows (среда SQL Server Management Studio)](establish-database-mirroring-session-windows-authentication.md)  
  
-   [Создание сеанса зеркального отображения базы данных с использованием проверки подлинности Windows (Transact-SQL)](database-mirroring-establish-session-windows-authentication.md)  
  
-   [Пример. Настройка зеркального отображения базы данных с помощью сертификатов (Transact-SQL)](example-setting-up-database-mirroring-using-certificates-transact-sql.md)  
  
## <a name="see-also"></a>См. также:  
 [SQL Server &#40;зеркального отображения базы данных&#41;](database-mirroring-sql-server.md)   
 [Настройка SQL Server &#40;зеркального отображения базы данных&#41;](setting-up-database-mirroring-sql-server.md)   
 [Группы доступности AlwaysOn (SQL Server)](../availability-groups/windows/always-on-availability-groups-sql-server.md)  
  
  
