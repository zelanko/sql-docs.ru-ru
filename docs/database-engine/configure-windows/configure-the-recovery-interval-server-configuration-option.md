---
title: "Настройка параметра конфигурации сервера recovery interval | Документы Майкрософт"
ms.custom: 
ms.date: 03/02/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: configure-windows
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- restoring recovery interval [SQL Server]
- checkpoints [SQL Server]
- recovery interval option [SQL Server]
- default recovery interval option
- time [SQL Server], recovery interval
- interval for recovery [SQL Server]
- maximum number of minutes per database recovery
- recovery [SQL Server], recovery interval option
ms.assetid: e4734b3b-8fbe-4b65-9c48-91b5a3dd18e1
caps.latest.revision: "39"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 98bab43fdcada2a88734e16f6705e9fa09ead275
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="configure-the-recovery-interval-server-configuration-option"></a>Настройка параметра конфигурации сервера recovery interval
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  В этом разделе описываются способы настройки параметра конфигурации сервера **recovery interval** в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]. Параметр **recovery interval** определяет верхний предел времени восстановления базы данных. Компонент [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] использует значение этого параметра чтобы приблизительно определить частоту выделения [автоматических контрольных точек](../../relational-databases/logs/database-checkpoints-sql-server.md) для данной базы данных.  
  
 По умолчанию задано значение интервала восстановления 0, позволяющее компоненту [!INCLUDE[ssDE](../../includes/ssde-md.md)] автоматически настраивать интервал восстановления. Обычно при интервале восстановления по умолчанию автоматические контрольные точки создаются приблизительно раз в минуту для активных баз данных, а время восстановления занимает меньше минуты. Более высокие значения указывают приблизительное максимальное время восстановления в минутах. Например, интервал восстановления, равный 3, указывает, что максимальное время восстановления равно приблизительно 3 минутам.  
  
 **В этом разделе**  
  
-   **Перед началом работы выполните следующие действия.**  
  
     [Ограничения](#Restrictions)  
  
     [Рекомендации](#Recommendations)  
  
     [Безопасность](#Security)  
  
-   **Настройка параметра конфигурации сервера recovery interval с помощью:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Дальнейшие действия.**  [После настройки параметра recovery interval](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   Интервал восстановления влияет только на базы данных, использующие целевое время восстановления по умолчанию (0). Чтобы переопределить интервал восстановления сервера для базы данных, следует настроить целевое время восстановления, не являющееся временем восстановления по умолчанию для этой базы данных. Дополнительные сведения см. в разделе [Изменение целевого времени восстановления базы данных (SQL Server)](../../relational-databases/logs/change-the-target-recovery-time-of-a-database-sql-server.md).  
  
###  <a name="Recommendations"></a> Рекомендации  
  
-   Этот параметр является дополнительным и его следует изменять только опытным администраторам баз данных или сертифицированным техническим специалистам [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Обычно рекомендуется сохранять интервал восстановления, равный 0, если нет проблем с производительностью. Если принято решение увеличить параметр интервала восстановления, рекомендуется увеличивать его постепенно с небольшими приращениями и оценивать влияние каждого приращения на производительность восстановления.  
  
-   При использовании хранимой процедуры **sp_configure** для изменения параметра **recovery interval** до значения, превышающего 60 минут, необходимо указать параметр RECONFIGURE WITH OVERRIDE. Параметр WITH OVERRIDE отключает проверку значения конфигурации (при которой выполняется поиск недопустимых или нерекомендованных значений).  
  
###  <a name="Security"></a> Безопасность  
  
####  <a name="Permissions"></a> Разрешения  
 Разрешения на выполнение хранимой процедуры **sp_configure** без параметров или только с первым параметром по умолчанию предоставляются всем пользователям. Для выполнения процедуры **sp_configure** с обоими параметрами для изменения параметра конфигурации или запуска инструкции RECONFIGURE необходимо иметь разрешение ALTER SETTINGS на уровне сервера. Разрешение ALTER SETTINGS неявным образом предоставлено предопределенным ролям сервера **sysadmin** и **serveradmin** .  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 **Указание интервала восстановления**  
  
1.  В обозревателе объектов щелкните правой кнопкой мыши экземпляр сервера и выберите пункт **Свойства**.  
  
2.  Щелкните узел **Параметры базы данных** .  
  
3.  В разделе **Восстановление**в поле **Интервал восстановления (в минутах)** введите или выберите значение от 0 до 32 767 максимального интервала времени в минутах, которое [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должен при запуске выделять на восстановление каждой базы данных. Если значение по умолчанию равно 0, оно означает автоматическую настройку, которую выполняет [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. На практике это означает время восстановления менее минуты и создание контрольных точек приблизительно раз в минуту для активно используемых баз данных.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-set-the-recovery-interval"></a>Указание интервала восстановления  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере показано использование хранимой процедуры [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) для задания значения параметра `recovery interval` равным `3` мин.  
  
```tsql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'recovery interval', 3 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
 Дополнительные сведения см. в разделе [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md).  
  
##  <a name="FollowUp"></a> Дальнейшие действия. После настройки параметра recovery interval  
 Параметр вступает в силу немедленно, без перезапуска сервера.  
  
## <a name="see-also"></a>См. также:  
 [Изменение целевого времени восстановления базы данных (SQL Server)](../../relational-databases/logs/change-the-target-recovery-time-of-a-database-sql-server.md)   
 [Контрольные точки базы данных (SQL Server)](../../relational-databases/logs/database-checkpoints-sql-server.md)   
 [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [Параметр конфигурации сервера "show advanced options"](../../database-engine/configure-windows/show-advanced-options-server-configuration-option.md)   
 [RECONFIGURE (Transact-SQL)](../../t-sql/language-elements/reconfigure-transact-sql.md)  
  
  
