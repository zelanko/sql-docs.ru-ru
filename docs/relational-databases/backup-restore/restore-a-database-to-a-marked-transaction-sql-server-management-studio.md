---
title: "Восстановление базы данных до помеченной транзакции (среда SQL Server Management Studio) | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-backup-restore
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.restoretlog.markedtransaction.f1
helpviewer_keywords:
- database restores [SQL Server], marked transactions
- restoring databases [SQL Server], marked transactions
- marked transactions [SQL Server], restoring
ms.assetid: 8f0ea144-1819-4832-905f-e5d0f49b066b
caps.latest.revision: 21
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 48529229420d7c2dafad334f3104e01add1a6746
ms.contentlocale: ru-ru
ms.lasthandoff: 04/11/2017

---
# <a name="restore-a-database-to-a-marked-transaction-sql-server-management-studio"></a>Восстановление базы данных до помеченной транзакции (среда SQL Server Management Studio)
  Если база данных находится в состоянии восстановления, то для ее восстановления в какое-либо состояние, доступное среди резервных копий, можно использовать диалоговое окно **Восстановление журнала транзакций** .  
  
> [!NOTE]  
>  Дополнительные сведения см. в статье [Использование помеченных транзакций для согласованного восстановления связанных баз данных (модель полного восстановления)](../../relational-databases/backup-restore/use-marked-transactions-to-recover-related-databases-consistently.md) and [Recovery of Related  Databases That Contain Marked Transaction](../../relational-databases/backup-restore/recovery-of-related-databases-that-contain-marked-transaction.md).  
  
### <a name="to-restore-a-marked-transaction"></a>Восстановление помеченной транзакции  
  
1.  После соединения с соответствующим экземпляром компонента [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]в обозревателе объектов разверните дерево сервера, щелкнув его имя.  
  
2.  Раскройте узел **Базы данных**и в зависимости от типа восстанавливаемой базы данных выберите пользовательскую базу данных или раскройте узел **Системные базы данных** и выберите системную базу данных.  
  
3.  Щелкните правой кнопкой мыши базу данных, укажите на пункт **Задачи**и щелкните **Восстановить**.  
  
4.  Выберите **Журнал транзакций**, после чего откроется диалоговое окно **Восстановление журнала транзакций** .  
  
5.  На странице **Общие** в разделе **Восстановление** выберите пункт **До помеченной транзакции**, после чего откроется диалоговое окно **Выбор помеченной транзакции** . В указанном диалоговом окне содержится список помеченных транзакций, доступных в выбранных резервных копиях журналов транзакций.  
  
     По умолчанию восстановление проводится до помеченной транзакции, не включая ее. Чтобы восстановить и помеченную транзакцию, выберите пункт **Включая помеченную транзакцию**.  
  
     В приведенной ниже таблице перечислены заголовки столбцов сетки, а также даны описания их значений.  
  
    |Заголовок|Значение|  
    |------------|-----------|  
    |\<пусто>|Отображает флажок для выбора маркера.|  
    |**Отметка транзакции**|Имя помеченной транзакции, заданное пользователем при фиксации транзакции.|  
    |**Дата**|Дата и время фиксации транзакции. Дата и время транзакции отображаются, в соответствии с данными в таблице **msdbgmarkhistory** , а не с датой и временем на клиентском компьютере.|  
    |**Описание**|Описание помеченной транзакции, заданное пользователем при ее фиксации (при его наличии).|  
    |**Номер LSN**|Регистрационный номер помеченной транзакции в журнале.|  
    |**База данных**|Имя базы данных, в которой была зафиксирована помеченная транзакция.|  
    |**Имя пользователя**|Имя пользователя базы данных, зафиксировавшего помеченную транзакцию.|  
  
## <a name="see-also"></a>См. также:  
 [Restore a Database Backup Using SSMS](../../relational-databases/backup-restore/restore-a-database-backup-using-ssms.md)   
 [Восстановление резервной копии журнала транзакций (SQL Server)](../../relational-databases/backup-restore/restore-a-transaction-log-backup-sql-server.md)  
  
  
