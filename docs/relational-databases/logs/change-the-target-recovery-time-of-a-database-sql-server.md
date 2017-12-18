---
title: "Изменение целевого времени восстановления базы данных (SQL Server) | Документация Майкрософт"
ms.custom: 
ms.date: 08/24/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: logs
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e466419a-d8a4-48f7-8d97-13a903ad6b15
caps.latest.revision: "16"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1ef7a5103a327739266689d45b058043d17fc1c6
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="change-the-target-recovery-time-of-a-database-sql-server"></a>Изменение целевого времени восстановления базы данных (SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] В этом разделе описывается изменение целевого времени восстановления базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]. По умолчанию целевое время восстановления — 60, а база данных использует *косвенные контрольные точки*. Значение целевого времени восстановления устанавливает верхнюю границу времени восстановления для этой базы данных.  
  
> [!NOTE]  
>  Верхняя граница, указываемая для отдельной базы данных посредством настройки целевого времени восстановления, может быть превышена из-за долгой транзакции, которая может вызвать чрезмерное время для отмены действий.  
  
-   **Перед началом:**  [Ограничения](#Restrictions), [Безопасность](#Security)  
  
-   **Для изменения целевого времени восстановления воспользуйтесь**  [SQL Server Management Studio](#SSMSProcedure) или [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения 
  
> [!CAUTION]  
>  В базе данных, которая настроена на использование косвенных контрольных точек, может снизиться производительность обработки транзакционной нагрузки в режиме «в сети». Косвенные конечные точки сохраняют количество «грязных» страниц ниже определенного порогового значения, чтобы восстановление базы данных выполнялось в течение заданного времени восстановления. Параметр конфигурации интервала восстановления использует количество транзакций для определения времени восстановления вместо косвенных конечных точек, которые основываются на количестве «грязных» страниц. Если косвенные конечные точки включены в базе данных, получающей большое число операций DML, средство фоновой записи может начать агрессивно сбрасывать «грязные» буферы обмена на диск, чтобы гарантировать, что время, необходимое для выполнения восстановления, находится в пределах целевого периода восстановления базы данных. Это может вызвать дополнительную активность операций ввода-вывода в определенных системах, что способно привести к созданию узких мест с точки зрения производительности, если подсистема диска превысила пороговое значение операций ввода-вывода или приближается к нему.  
  
###  <a name="Security"></a> Безопасность  
  
####  <a name="Permissions"></a> Разрешения  
 Необходимо разрешение ALTER на базу данных.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 **Изменение целевого времени восстановления**  
  
1.  В **обозревателе объектов**подключитесь к экземпляру [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]и разверните его.  
  
2.  Щелкните правой кнопкой мыши базу данных, которую необходимо изменить, и выберите команду **Свойства** .  
  
3.  В диалоговом окне **Свойства базы данных** выберите страницу **Параметры** .  
  
4.  На панели **Восстановление** в поле **Целевое время восстановления (секунды)** укажите количество секунд в качестве верхней границы времени восстановления этой базы данных.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 **Изменение целевого времени восстановления**  
  
1.  Установите подключение к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , на котором размещена база данных.  
  
2.  Используйте инструкцию [ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql-set-options.md)следующим образом:  
  
     TARGET_RECOVERY_TIME **=***target_recovery_time* { SECONDS | MINUTES }  
  
     *target_recovery_time*  
     Начиная с версии [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)], значение по умолчанию равно 1 минуте. Если значение больше 0 (значение по умолчанию для более старых версий), то оно указывает значение верхней границы времени восстановления для заданной базы данных в случае сбоя.  
  
     SECONDS  
     Указывает, что значение *target_recovery_time* выражается в количестве секунд.  
  
     MINUTES  
     Указывает, что значение *target_recovery_time* выражается в количестве минут.  
  
     В следующем примере устанавливается время восстановления базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] в `60` секунд.  
  
    ```  
    ALTER DATABASE AdventureWorks2012 SET TARGET_RECOVERY_TIME = 60 SECONDS;  
    ```  
  
## <a name="see-also"></a>См. также:  
 [Контрольные точки базы данных (SQL Server)](../../relational-databases/logs/database-checkpoints-sql-server.md)   
 [Параметры ALTER DATABASE SET (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql-set-options.md)  
  
  
