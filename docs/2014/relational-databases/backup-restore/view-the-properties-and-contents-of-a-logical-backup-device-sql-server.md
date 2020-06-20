---
title: Просмотр свойств и содержимого логического устройства резервного копирования (SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- displaying backup content
- viewing backup content
- database backups [SQL Server], viewing content
- backing up databases [SQL Server], viewing content
- backing up databases [SQL Server], properties
- displaying backup properties
- backup devices [SQL Server], viewing information
- viewing backup properties
- database backups [SQL Server], properties
ms.assetid: 3a309074-e816-454d-b6c3-fcfdde0cbf74
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f2bdf41e3dbda079e3627ff7a7c1c3c78103b728
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84956110"
---
# <a name="view-the-properties-and-contents-of-a-logical-backup-device-sql-server"></a>Просмотр свойств и содержимого логического устройства резервного копирования (SQL Server)
  В этом разделе описывается просмотр свойств и содержимого логического устройства резервного копирования в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Безопасность](#Security)  
  
-   **Просмотр свойств и содержимого логического устройства резервного копирования с помощью:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
 Сведения о безопасности см. в статье [RESTORE LABELONLY (Transact-SQL)](/sql/t-sql/statements/restore-statements-labelonly-transact-sql).  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 В [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] и более поздних версиях для получения сведений о резервном наборе данных или устройстве резервного копирования необходимо разрешение CREATE DATABASE. Дополнительные сведения см. в разделе [GRANT, предоставление разрешений для базы данных (Transact-SQL)](/sql/t-sql/statements/grant-database-permissions-transact-sql).  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-view-the-properties-and-contents-of-a-logical-backup-device"></a>Просмотр свойств и содержимого логического устройства резервного копирования  
  
1.  После подключения к соответствующему экземпляру [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] в обозревателе объектов разверните дерево сервера, щелкнув его имя.  
  
2.  Разверните узел **Объекты сервера**, затем разверните узел **Устройства резервного копирования**.  
  
3.  Щелкните иконку устройства и правой клавишей мыши щелкните элемент **Свойства**. В результате откроется диалоговое окно **Устройство резервного копирования** .  
  
4.  На странице **Общие** отображается имя устройства и место назначения — ленточное устройство или путь к файлу.  
  
5.  На панели **Выбор страницы** щелкните элемент **Содержимое носителя**.  
  
6.  В правом окне отображаются следующие панели свойств.  
  
    -   **Носитель**  
  
         Сведения о порядке носителей (порядковый номер носителя, порядковый номер семейства, идентификатор зеркального сервера, если таковой существует), а также дата и время создания носителя.  
  
    -   **Набор носителей**  
  
         Сведения о наборе носителей: имя и описание набора носителей (если указано), а также число семейств в наборе носителей.  
  
7.  Сетка **Резервные наборы данных** отображает сведения о содержимом данного набора носителей.  
  
> [!NOTE]  
>  Дополнительные сведения см. в разделе [Страница "Содержимое носителя"](backup-device-media-contents-page.md).  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-view-the-properties-and-contents-of-a-logical-backup-device"></a>Просмотр свойств и содержимого логического устройства резервного копирования  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Используйте инструкцию [RESTORE LABELONLY](/sql/t-sql/statements/restore-statements-labelonly-transact-sql) . В этом примере возвращаются сведения о логическом устройстве резервного копирования `AdvWrks2008R2Backup` .  
  
```sql  
USE AdventureWorks2012 ;  
RESTORE LABELONLY  
   FROM AdvWrks2008R2Backup ;  
GO  
  
```  
  
## <a name="see-also"></a>См. также:  
 [backupfilegroup (Transact-SQL)](/sql/relational-databases/system-tables/backupfilegroup-transact-sql)   
 [backupfile (Transact-SQL)](/sql/relational-databases/system-tables/backupfile-transact-sql)   
 [backupset (Transact-SQL)](/sql/relational-databases/system-tables/backupset-transact-sql)   
 [backupmediaset (Transact-SQL)](/sql/relational-databases/system-tables/backupmediaset-transact-sql)   
 [backupmediafamily (Transact-SQL)](/sql/relational-databases/system-tables/backupmediafamily-transact-sql)   
 [sp_addumpdevice (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql)   
 [Устройства резервного копирования (SQL Server)](backup-devices-sql-server.md)  
  
  
