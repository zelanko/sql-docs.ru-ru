---
title: "Определение логического устройства резервного копирования для ленточного накопителя (SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-backup-restore"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "устройства резервного копирования [SQL Server], определение"
  - "устройства резервного копирования [SQL Server], ленты"
  - "резервное копирование баз данных [SQL Server], ленты"
  - "резервные копии баз данных [SQL Server], ленты"
  - "ленточные устройства резервного копирования, создание"
ms.assetid: 66f36e1d-0287-4fac-8a51-71f9f0d7ad5b
caps.latest.revision: 38
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 38
---
# Определение логического устройства резервного копирования для ленточного накопителя (SQL Server)
  В данном разделе описывается процесс определения логического устройства резервного копирования для ленточного накопителя в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]. Логическое устройство представляет собой определяемое пользователем имя, которое указывает на конкретное физическое устройство резервного копирования (дисковый файл или ленточный накопитель).  Инициализация физического устройства происходит позже, при записи на него резервной копии.  
  
> [!NOTE]  
>  Поддержка ленточных устройств резервного копирования будет удалена в одной из будущих версий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется.  
  
 **В этом разделе**  
  
-   **Перед началом работы выполните следующие действия.**  
  
     [Ограничения](#Restrictions)  
  
     [Безопасность](#Security)  
  
-   **Определение логического устройства резервного копирования для ленточного накопителя с помощью:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   Ленточный накопитель или диски должны поддерживаться операционной системой Microsoft Windows.  
  
-   Ленточное устройство должно быть физически подключено к компьютеру, на котором запущен экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Резервное копирование на удаленный ленточный накопитель не поддерживается.  
  
###  <a name="Security"></a> Безопасность  
  
####  <a name="Permissions"></a> Разрешения  
 Требует членства в предопределенной роли сервера **diskadmin** .  
  
 Необходимо разрешение на запись на жесткий диск.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### Определение логического устройства резервного копирования для ленточного накопителя  
  
1.  После соединения с соответствующим экземпляром компонента [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]в обозревателе объектов разверните дерево сервера, щелкнув его имя.  
  
2.  Разверните узел **Объекты сервера** и щелкните правой кнопкой мыши пункт **Устройства резервного копирования**.  
  
3.  Выберите пункт **Новое устройство резервного копирования**, в результате чего появится диалоговое окно **Устройство резервного копирования** .  
  
4.  Введите имя устройства.  
  
5.  В разделе «Расположение» установите переключатель **Лента** и выберите ленточный накопитель, который еще не связан с другим устройством резервного копирования. Если таких накопителей нет, не устанавливайте переключатель **Лента** .  
  
6.  Чтобы определить новое устройство, нажмите кнопку **OK**.  
  
 Чтобы выполнить резервное копирование на новое устройство, добавьте его в поле **Создать резервную копию на** в диалоговом окне **Резервное копирование базы данных** (**Общие**). Дополнительные сведения см. в разделе [Создание полной резервной копии базы данных (SQL Server)](../../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md).  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### Определение логического устройства резервного копирования для ленточного накопителя  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. Этот пример иллюстрирует использование процедуры [sp_addumpdevice](../../relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql.md) в целях определения логического устройства резервного копирования для ленточного накопителя. В этом примере добавляется ленточное устройство резервного копирования с именем `tapedump1`, которое имеет физическое имя `\\.\tape0`.  
  
```tsql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_addumpdevice 'tape', 'tapedump1', '\\.\tape0' ;  
GO  
```  
  
## См. также:  
 [BACKUP (Transact-SQL)](../../t-sql/statements/backup-transact-sql.md)   
 [sys.backup_devices (Transact-SQL)](../../relational-databases/system-catalog-views/sys-backup-devices-transact-sql.md)   
 [sp_addumpdevice (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql.md)   
 [sp_dropdevice (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-dropdevice-transact-sql.md)   
 [Устройства резервного копирования (SQL Server)](../../relational-databases/backup-restore/backup-devices-sql-server.md)   
 [Определение логического устройства резервного копирования для дискового файла (SQL Server)](../../relational-databases/backup-restore/define-a-logical-backup-device-for-a-disk-file-sql-server.md)   
 [Просмотр свойств и содержимого логического устройства резервного копирования (SQL Server)](../../relational-databases/backup-restore/view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
  