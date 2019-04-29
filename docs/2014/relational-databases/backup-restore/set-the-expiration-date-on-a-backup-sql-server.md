---
title: Назначение срока хранения резервной копии (SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- backing up databases [SQL Server], expiration dates
- expiration [SQL Server]
- database backups [SQL Server], expiration dates
ms.assetid: 76e814df-6487-4893-9f09-7759f1863a5c
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 30f5a68f51bf501f243bd129d11051d63a6efabd
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62877308"
---
# <a name="set-the-expiration-date-on-a-backup-sql-server"></a>Назначение срока хранения резервной копии (SQL Server)
  В этом разделе описано, как задать срок хранения для устройства резервного копирования в среде [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [безопасность](#Security)  
  
-   **Задание срока хранения резервной копии с помощью:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Разрешения BACKUP DATABASE и BACKUP LOG назначены по умолчанию членам предопределенной роли сервера **sysadmin** и предопределенным ролям базы данных **db_owner** и **db_backupoperator** .  
  
 Проблемы, связанные с владельцем и разрешениями у физических файлов на устройстве резервного копирования, могут помешать операции резервного копирования. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должен иметь возможность считывать и записывать данные на устройстве; учетная запись, от имени которой выполняется служба [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , должна иметь разрешения на запись. Однако процедура [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql), добавляющая запись для устройства резервного копирования в системные таблицы, не проверяет разрешения на доступ к файлу. Проблемы физического файла устройства резервного копирования могут не проявляться до момента доступа к физическому ресурсу во время операции резервного копирования или восстановления.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-set-the-expiration-date-on-a-backup"></a>Назначение срока хранения резервной копии  
  
1.  После соединения с соответствующим экземпляром компонента [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)]в обозревателе объектов разверните дерево сервера, щелкнув его имя.  
  
2.  Раскройте узел **Базы данных**и в зависимости от типа восстанавливаемой базы данных выберите пользовательскую базу данных или раскройте узел **Системные базы данных** и выберите системную базу данных.  
  
3.  Щелкните правой кнопкой мыши базу данных, выберите пункт **Задачи**, а затем команду **Создать резервную копию**. Откроется диалоговое окно **Резервное копирование базы данных** .  
  
4.  На странице **Общие** в поле **Срок действия резервного набора данных истекает**укажите дату истечения срока, чтобы определить, когда резервный набор данных можно будет перезаписать другой резервной копией:  
  
    -   Чтобы задать срок действия резервного набора данных, выберите пункт **После** (параметр по умолчанию) и введите срок действия набора в днях с момента его создания. Это значение может быть задано в диапазоне от 0 до 99 999 дней. Значение 0 означает, что срок действия резервного набора данных не ограничен.  
  
         Значение по умолчанию задается в параметре **Срок хранения носителей резервных копий по умолчанию (дней):** диалогового окна **Свойства сервера** (страница**Параметры базы данных** ). Чтобы получить доступ к этому параметру, щелкните правой кнопкой мыши имя сервера в обозревателе объектов и выберите пункт "Свойства", а затем выберите страницу **Настройки базы данных** .  
  
    -   Чтобы указать дату истечения срока действия резервного набора данных, выберите пункт **На**и введите дату истечения срока действия резервного набора данных.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-set-the-expiration-date-on-a-backup"></a>Назначение срока хранения резервной копии  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  В инструкции [BACKUP](/sql/t-sql/statements/backup-transact-sql) укажите параметр EXPIREDATE или RETAINDAYS, чтобы определить, когда компоненту [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)] можно будет перезаписать резервную копию. Если ни один из этих параметров не указан, то срок хранения определяется параметром конфигурации [media retention](../../database-engine/configure-windows/configure-the-media-retention-server-configuration-option.md) . В следующем примере параметр `EXPIREDATE` задает срок истечения хранения 30 июня 2015 г. (`6/30/2015`).  
  
```sql  
USE AdventureWorks2012;  
GO  
BACKUP DATABASE AdventureWorks2012  
 TO DISK = 'Z:\SQLServerBackups\AdventureWorks2012.Bak'  
   WITH EXPIREDATE = '6/30/2015' ;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Создание полной резервной копии базы данных (SQL Server)](create-a-full-database-backup-sql-server.md)   
 [Резервное копирование файлов и файловых групп (SQL Server)](back-up-files-and-filegroups-sql-server.md)   
 [Создание резервной копии журнала транзакций (SQL Server)](back-up-a-transaction-log-sql-server.md)   
 [Создание разностной резервной копии базы данных (SQL Server)](create-a-differential-database-backup-sql-server.md)  
  
  
