---
title: Обмен ролями между сервером-источником и сервером-получателем доставки журналов (SQL Server) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- log shipping [SQL Server], role changes
- secondary data files [SQL Server], roles changed between
- primary databases [SQL Server]
- initial role changes [SQL Server]
- log shipping [SQL Server], failover
- failover [SQL Server], log shipping
ms.assetid: 2d7cc40a-47e8-4419-9b2b-7c69f700e806
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 08467118608db6b222bea2a41351eac951449a16
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "62774568"
---
# <a name="change-roles-between-primary-and-secondary-log-shipping-servers-sql-server"></a>Обмен ролями между сервером-источником и сервером-получателем доставки журналов (SQL Server)
  После перехода конфигурации доставки журналов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на ресурс сервера-получателя можно настроить базу данных-получатель для работы в качестве базы данных-источника. Затем базу данных-источник и базу данных-получатель можно менять местами по необходимости.  
  
## <a name="performing-the-initial-role-change"></a>Выполнение исходного изменения роли  
 В первый раз при переключении на базу данных-получатель и назначении ее новой базой данных-источником необходимо выполнить ряд шагов. После выполнения этих первоначальных шагов появится возможность легко менять местами базу данных-источник и базу данных-получатель.  
  
1.  Переход с базы данных-источника на базу данных-получатель вручную. Обязательно создайте резервную копию активного журнала транзакций сервера-источника с параметром NORECOVERY. Дополнительные сведения см. в разделе [Переход на вторичный сервер доставки журналов (SQL Server)](fail-over-to-a-log-shipping-secondary-sql-server.md).  
  
2.  Отключите задание резервного копирования в доставке журналов на исходном сервере-источнике и задания копирования и восстановления на исходном сервере-получателе.  
  
3.  С помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] настройте доставку журналов для базы данных-получателя (базы данных, которую хотите сделать источником). Дополнительные сведения см. в разделе [Настройка доставки журналов (SQL Server)](configure-log-shipping-sql-server.md). Выполните следующие шаги:  
  
    1.  Для создания резервных копий используйте ту же общую папку, которая была создана для первоначального сервера-источника.  
  
    2.  При добавлении базы данных-получателя в диалоговом окне **Настройки базы данных-получателя** введите имя исходной базы данных-источника в поле **База данных-получатель**  
  
    3.  В диалоговом окне **Настройки базы данных-получателя** выберите параметр **Нет, база данных-получатель инициализирована**.  
  
4.  Если в предыдущей конфигурации доставки журналов был включен мониторинг доставки журнала, внесите изменения в настройки мониторинга доставки журнала для отслеживания новой конфигурации доставки журнала.  Выполните следующие команды, заменив *database_name* именем вашей базы данных:  
  
    1.  **На новом сервере-источнике**  
  
         Выполните следующие инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] .  
  
        ```  
        -- Statement to execute on the new primary server  
        USE msdb  
        GO  
        EXEC master.dbo.sp_change_log_shipping_secondary_database @secondary_database = N'database_name', @threshold_alert_enabled = 0;  
        GO  
        ```  
  
    2.  **На новом сервере-получателе**  
  
         Выполните следующие инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] .  
  
        ```  
        -- Statement to execute on the new secondary server  
        USE msdb  
        GO  
        EXEC master.dbo.sp_change_log_shipping_primary_database @database=N'database_name', @threshold_alert_enabled = 0;  
        GO  
        ```  
  
## <a name="swapping-roles"></a>Смена ролей  
 После завершения перечисленных выше шагов для первоначальной смены ролей можно выполнить обмен ролями между базой данных-источником и базой данных-получателем, выполняя действия, приведенные в этом разделе. Выполните следующие шаги для обмена ролями:  
  
1.  Переведите базу данных-получатель в режим «в сети», выполните резервное копирование журнала транзакций на сервере-источнике с параметром NORECOVERY.  
  
2.  Отключите задание резервного копирования в доставке журналов на исходном сервере-источнике и задания копирования и восстановления на исходном сервере-получателе.  
  
3.  Включите задание резервного копирования в доставке журналов на исходном сервере-получателе (новом сервере-источнике) и задания копирования и восстановления на исходном сервере-источнике (новом сервере-получателе).  
  
> [!IMPORTANT]  
>  Чтобы обеспечить согласованную работу пользователей и приложений при изменении базы данных-получателя на базу данных-источник, необходимо повторно создать часть или все метаданные базы данных, такие как имена входа и задания, в новом экземпляре сервера-источника. Дополнительные сведения см. [в разделе Управление метаданными при обеспечении доступности базы данных на другом экземпляре сервера &#40;SQL Server&#41;](../../relational-databases/databases/manage-metadata-when-making-a-database-available-on-another-server.md).  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Связанные задачи  
  
-   [Переход на вторичный сервер доставки журналов (SQL Server)](fail-over-to-a-log-shipping-secondary-sql-server.md)  
  
-   [Управление именами входа и заданиями после переключения ролей (SQL Server)](../../sql-server/failover-clusters/management-of-logins-and-jobs-after-role-switching-sql-server.md)  
  
## <a name="see-also"></a>См. также  
 [Log Shipping Tables and Stored Procedures](log-shipping-tables-and-stored-procedures.md)  
  
  
