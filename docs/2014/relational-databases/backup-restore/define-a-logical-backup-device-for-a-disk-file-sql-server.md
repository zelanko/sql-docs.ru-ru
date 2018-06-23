---
title: Определение логического устройства резервного копирования для дискового файла (SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-backup-restore
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- backup devices [SQL Server], defining
- backup devices [SQL Server], disks
- disk backup devices [SQL Server]
- database backups [SQL Server], disks
- backing up databases [SQL Server], disks
ms.assetid: 86331d43-c738-4523-ae3d-7d6700348ed1
caps.latest.revision: 37
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a28e686e81ac6ed17c153a6c7888676882ab485d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36098916"
---
# <a name="define-a-logical-backup-device-for-a-disk-file-sql-server"></a>Определение логического устройства резервного копирования для дискового файла (SQL Server)
  В данном разделе описывается процесс определения логического устройства резервного копирования для дискового файла в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]. Логическое устройство представляет собой определяемое пользователем имя, которое указывает на конкретное физическое устройство резервного копирования (дисковый файл или ленточный накопитель).  Инициализация физического устройства происходит позже, при записи на него резервной копии.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [Рекомендации](#Recommendations)  
  
     [безопасность](#Security)  
  
-   **Определение логического устройства резервного копирования для дискового файла с помощью:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   Каждое имя логического устройства должно быть уникальным в пространстве имен всех логических устройств резервного копирования на экземпляре сервера. Чтобы просмотреть имена существующих логических устройств, запросите представление каталога [sys.backup_devices](/sql/relational-databases/system-catalog-views/sys-backup-devices-transact-sql) .  
  
###  <a name="Recommendations"></a> Рекомендации  
  
-   Резервные копии, базы данных и журналы рекомендуется хранить на разных дисках. Это является необходимым, чтобы можно было гарантировать возможность доступа к резервным копиям при сбое диска с базой данных или журналами.  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Требует членства в предопределенной роли сервера **diskadmin** .  
  
 Необходимо разрешение на запись на жесткий диск.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-define-a-logical-backup-device-for-a-disk-file"></a>Определение логического устройства резервного копирования для дискового файла  
  
1.  После соединения с соответствующим экземпляром компонента [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]в обозревателе объектов разверните дерево сервера, щелкнув его имя.  
  
2.  Разверните **Объекты сервера**и щелкните правой кнопкой мыши **Устройства резервного копирования**.  
  
3.  Выберите команду **Создать устройство резервного копирования**. Откроется диалоговое окно **Устройство резервного копирования** .  
  
4.  Введите имя устройства.  
  
5.  В качестве места назначения выберите **Файл** и укажите полный путь к файлу.  
  
6.  Чтобы определить новое устройство, нажмите кнопку **OK**.  
  
 Чтобы выполнить резервное копирование на новое устройство, добавьте его в поле **Создать резервную копию на** в диалоговом окне **Резервное копирование базы данных** (**Общие**). Дополнительные сведения см. в разделе [Создание полной резервной копии базы данных (SQL Server)](create-a-full-database-backup-sql-server.md).  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-define-a-logical-backup-for-a-disk-file"></a>Определение логического устройства резервного копирования для дискового файла  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. Этот пример иллюстрирует использование процедуры [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql) в целях определения логического устройства резервного копирования для дискового файла. В этом примере добавляется дисковое устройство резервного копирования с именем `mydiskdump`, которое имеет физическое имя `c:\dump\dump1.bak`.  
  
```tsql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_addumpdevice 'disk', 'mydiskdump', 'c:\dump\dump1.bak' ;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [BACKUP (Transact-SQL)](/sql/t-sql/statements/backup-transact-sql)   
 [Устройства резервного копирования (SQL Server)](backup-devices-sql-server.md)   
 [sys.backup_devices (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-backup-devices-transact-sql)   
 [sp_addumpdevice (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql)   
 [sp_dropdevice (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-dropdevice-transact-sql)   
 [Определение логического устройства резервного копирования для ленточного накопителя (SQL Server)](define-a-logical-backup-device-for-a-tape-drive-sql-server.md)   
 [Просмотр свойств и содержимого логического устройства резервного копирования (SQL Server)](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
  
