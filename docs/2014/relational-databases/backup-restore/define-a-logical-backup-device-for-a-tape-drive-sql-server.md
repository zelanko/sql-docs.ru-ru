---
title: Определение логического устройства резервного копирования для ленточного накопителя (SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- backup devices [SQL Server], defining
- backup devices [SQL Server], tapes
- backing up databases [SQL Server], tapes
- database backups [SQL Server], tapes
- tape backup devices, creating
ms.assetid: 66f36e1d-0287-4fac-8a51-71f9f0d7ad5b
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 14a96a44967c41b185d3196c9d6577f67547e77a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62877945"
---
# <a name="define-a-logical-backup-device-for-a-tape-drive-sql-server"></a>Определение логического устройства резервного копирования для ленточного накопителя (SQL Server)
  В данном разделе описывается процесс определения логического устройства резервного копирования для ленточного накопителя в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]. Логическое устройство представляет собой определяемое пользователем имя, которое указывает на конкретное физическое устройство резервного копирования (дисковый файл или ленточный накопитель).  Инициализация физического устройства происходит позже, при записи на него резервной копии.  
  
> [!NOTE]  
>  Поддержка ленточных устройств резервного копирования будет удалена в одной из будущих версий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [безопасность](#Security)  
  
-   **Определение логического устройства резервного копирования для ленточного накопителя с помощью:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   Ленточный накопитель или диски должны поддерживаться операционной системой Microsoft Windows.  
  
-   Ленточное устройство должно быть физически подключено к компьютеру, на котором запущен экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Резервное копирование на удаленный ленточный накопитель не поддерживается.  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Требует членства в предопределенной роли сервера **diskadmin** .  
  
 Необходимо разрешение на запись на жесткий диск.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-define-a-logical-backup-device-for-a-tape-drive"></a>Определение логического устройства резервного копирования для ленточного накопителя  
  
1.  После соединения с соответствующим экземпляром компонента [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]в обозревателе объектов разверните дерево сервера, щелкнув его имя.  
  
2.  Разверните узел **Объекты сервера**и щелкните правой кнопкой мыши пункт **Устройства резервного копирования**.  
  
3.  Выберите пункт **Новое устройство резервного копирования**, в результате чего появится диалоговое окно **Устройство резервного копирования** .  
  
4.  Введите имя устройства.  
  
5.  В разделе «Расположение» установите переключатель **Лента** и выберите ленточный накопитель, который еще не связан с другим устройством резервного копирования. Если таких накопителей нет, не устанавливайте переключатель **Лента** .  
  
6.  Чтобы определить новое устройство, нажмите кнопку **OK**.  
  
 Чтобы выполнить резервное копирование на новое устройство, добавьте его в поле **Создать резервную копию на** в диалоговом окне **Резервное копирование базы данных** (**Общие**). Дополнительные сведения см. в разделе [Создание полной резервной копии базы данных (SQL Server)](create-a-full-database-backup-sql-server.md).  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-define-a-logical-backup-device-for-a-tape-drive"></a>Определение логического устройства резервного копирования для ленточного накопителя  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. Этот пример иллюстрирует использование процедуры [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql) в целях определения логического устройства резервного копирования для ленточного накопителя. В этом примере добавляется ленточное устройство резервного копирования с именем `tapedump1`, которое имеет физическое имя `\\.\tape0`.  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_addumpdevice 'tape', 'tapedump1', '\\.\tape0' ;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [BACKUP (Transact-SQL)](/sql/t-sql/statements/backup-transact-sql)   
 [sys.backup_devices (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-backup-devices-transact-sql)   
 [sp_addumpdevice (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql)   
 [sp_dropdevice (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-dropdevice-transact-sql)   
 [Устройства резервного копирования (SQL Server)](backup-devices-sql-server.md)   
 [Определение логического устройства резервного копирования для дискового файла (SQL Server)](define-a-logical-backup-device-for-a-disk-file-sql-server.md)   
 [Просмотр свойств и содержимого логического устройства резервного копирования (SQL Server)](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
  
