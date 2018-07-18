---
title: RESTORE DATABASE (Parallel Data Warehouse) | Документы Майкрософт
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: d915bfc1-e392-4a3a-9d94-08682cf3c864
caps.latest.revision: 8
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 0fb3c753e4bde29eb9b5cbb5f287fc18d03a117a
ms.sourcegitcommit: 05e18a1e80e61d9ffe28b14fb070728b67b98c7d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/04/2018
ms.locfileid: "37782435"
---
# <a name="restore-database-parallel-data-warehouse"></a>RESTORE DATABASE (Parallel Data Warehouse)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Восстанавливает пользовательскую базу данных [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] из резервной копии базы данных на устройство [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]. База данных восстанавливается из резервной копии, созданной ранее с помощью команды [!INCLUDE[ssPDW](../../includes/sspdw-md.md)][BACKUP DATABASE (Parallel Data Warehouse)](../../t-sql/statements/backup-database-parallel-data-warehouse.md). Используйте команды резервного копирования и восстановления для создания плана аварийного восстановления или для перемещения баз данных с одного устройства на другое.  
  
> [!NOTE]  
>  Восстановления базы данных master включает восстановление учетных данных для входа на устройство. Чтобы восстановить базу данных master, воспользуйтесь страницей [Восстановление базы данных master (Transact-SQL)](../../relational-databases/backup-restore/restore-the-master-database-transact-sql.md) инструмента **Configuration Manager**. Эту операцию может выполнить администратор, у которого есть доступ к управляющему узлу.  
  
 Дополнительные сведения о резервном копировании баз данных [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] см. в разделе "Резервное копирование и восстановление" в [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL (Transact-SQL)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
      Restore the master database  
-- Use the Configuration Manager tool.  
  
Restore a full user database backup.  
RESTORE DATABASE database_name   
    FROM DISK = '\\UNC_path\full_backup_directory'  
[;]  
  
Restore a full user database backup and then a differential backup.  
RESTORE DATABASE database_name  
    FROM DISK = '\\UNC_path\differential_backup_directory'   
    WITH [ ( ] BASE = '\\UNC_path\full_backup_directory' [ ) ]   
[;]  
  
Restore header information for a full or differential user database backup.  
RESTORE HEADERONLY   
    FROM DISK = '\\UNC_path\backup_directory'  
[;]  
```  
  
## <a name="arguments"></a>Аргументы  
 RESTORE DATABASE *имя_базы_данных*  
 Указывает, что нужно восстановить пользовательскую базу данных в базу данных с заданным *именем*. Имя восстановленной базы данных может отличаться от имени базы данных, для которой была создана резервная копия. База данных с указанным *именем* не должна существовать на устройстве назначения перед восстановлением. Дополнительные сведения о разрешенных именах баз данных см. в разделе "Правила именования объектов" в статье [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
 При восстановлении пользовательской базы данных происходит восстановление полной резервной копии базы данных и затем при необходимости восстановление разностной резервной копии на устройство. Восстановление пользовательской базы данных включает пользователей и роли базы данных.  
  
 FROM DISK = '\\\\*путь_UNC*\\*каталог_резервной_копии*'  
 Сетевой путь к каталогу, из которого [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] восстановит файлы резервной копии. Например, FROM DISK = '\\\xxx.xxx.xxx.xxx\backups\2012\Monthly\08.2012.Mybackup'.  
  
 *каталог_резервной_копии*  
 Указывает имя каталога, который содержит полную или разностную резервную копию. Например, операцию RESTORE HEADERONLY можно выполнить для полной или разностной резервной копии.  
  
 *каталог_полной_резервной_копии*  
 Указывает имя каталога, который содержит полную резервную копию.  
  
 *каталог_разностной_резервной_копии*  
 Указывает имя каталога, который содержит разностную резервную копию.  
  
-   Путь к каталогу резервного копирования должен существовать; его необходимо указать в виде полного пути UNC.  
  
-   Путь к каталогу резервного копирования не может быть локальным путем или расположением на любом из узлов устройства [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].  
  
-   Максимальная длина пути UNC и имени каталога резервного копирования равна 200 символов.  
  
-   Для сервера или узла необходимо указать IP-адрес.  
  
 инструкция RESTORE HEADERONLY  
 Указывает, что необходимо вернуть только сведения заголовка для одной резервной копии пользовательской базы данных. Среди прочего заголовок содержит текстовое описание и имя резервной копии. Имя резервной копии может не совпадать с именем каталога, в котором хранятся файлы резервной копии.  
  
 Результаты инструкции RESTORE HEADERONLY обрабатываются в соответствии с шаблоном после результатов инструкции RESTORE HEADERONLY [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Результат включает более 50 столбцов, и [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] использует не все из этих столбцов. Описание столбцов в результатах инструкции RESTORE HEADERONLY [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] см. в разделе [RESTORE HEADERONLY (Transact-SQL)](../../t-sql/statements/restore-statements-headeronly-transact-sql.md).  
  
## <a name="permissions"></a>Разрешения  
 Требуется разрешение **CREATE ANY DATABASE**.  
  
 Требуется учетная запись Windows с разрешениями на доступ к каталогу резервного копирования и на чтение этого каталога. Необходимо также сохранить имя учетной записи Windows и пароль в [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].  
  
1.  Чтобы проверить наличие учетных данных, воспользуйтесь [sys.dm_pdw_network_credentials (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-network-credentials-transact-sql.md).  
  
2.  Чтобы добавить или обновить учетные данные, используйте [sp_pdw_add_network_credentials (хранилище данных SQL)](../../relational-databases/system-stored-procedures/sp-pdw-add-network-credentials-sql-data-warehouse.md).  
  
3.  Чтобы удалить учетные данные из [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], используйте [sp_pdw_remove_network_credentials (хранилище данных SQL)](../../relational-databases/system-stored-procedures/sp-pdw-remove-network-credentials-sql-data-warehouse.md).  
  
## <a name="error-handling"></a>Обработка ошибок  
 Команда RESTORE DATABASE возвращает ошибки при выполнении следующих условий:  
  
-   Имя базы данных для восстановления уже существует на целевом устройстве. Чтобы избежать этой ошибки, выберите уникальное имя базы данных или удалите существующую базу данных перед началом восстановления.  
  
-   В каталоге резервной копии находится недопустимый набор файлов резервной копии.  
  
-   Разрешений на вход недостаточно для восстановления базы данных.  
  
-   [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] не имеет необходимых разрешений для сетевого расположения, в котором размещаются файлы резервной копии.  
  
-   Сетевое расположение для каталога резервного копирования не существует или недоступно.  
  
-   На вычислительных узлах или на управляющем узле недостаточно места. [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] не подтверждает наличие достаточного места на диске устройства перед началом восстановления. Поэтому при выполнении инструкции RESTORE DATABASE можно получить сообщение о нехватке места на диске. В случае нехватки места на диске [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] выполняет откат операции восстановления.  
  
-   Целевое устройство, на которое восстанавливается база данных, содержит меньшее количество вычислительных узлов по сравнению с исходным устройством, с которого была создана резервная копия.  
  
-   Предпринимается попытка восстановить базу данных в рамках транзакции.  
  
## <a name="general-remarks"></a>Общие замечания  
 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] отслеживает успешность восстановления базы данных. Перед восстановлением разностной резервной копии базы данных [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] проверяет, что полное восстановление всей базы данных успешно завершено.  
  
 После восстановления базы данных пользовательская база данных будет иметь уровень совместимости 120. Это справедливо для всех баз данных независимо от их исходного уровня совместимости.  
  
 **Восстановление на устройство с большим количеством вычислительных узлов**  
Запустите инструкцию [DBCC SHRINKLOG (хранилище данных SQL Azure)](../../t-sql/database-console-commands/dbcc-shrinklog-azure-sql-data-warehouse.md) после восстановления базы данных с устройства меньшего размера на устройство большего размера, так как при повторном распределении увеличится размер журнала транзакций.  

Восстановление резервной копии на устройство с большим числом вычислительных узлов приводит к увеличению размера базы данных пропорционально количеству вычислительных узлов.  
  
Например, при восстановлении базы данных размером 60 ГБ с устройства с двумя узлами (30 ГБ на каждом узле) на устройство с шестью узлами [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] создает базу данных размером 180 ГБ (6 узлов по 30 ГБ на каждом узле) на устройстве с шестью узлами. [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] изначально восстанавливает базу данных на 2 узла, чтобы она соответствовала исходной конфигурации, и затем перераспределяет данные на все 6 узлов.  
  
 После распределения каждый вычислительный узел будет содержать меньше фактических данных и больше свободного пространства, чем каждый исходный узел на исходном устройстве меньшего размера. Используйте дополнительное место для добавления дополнительных данных в базу данных. Если размер восстановленной базы данных больше, чем необходимо, вы можете сжать файлы базы данных с помощью инструкции [ALTER DATABASE (Parallel Data Warehouse)](../../t-sql/statements/alter-database-transact-sql.md?&tabs=sqlpdw).  
  
## <a name="limitations-and-restrictions"></a>Ограничения  
 В этих ограничениях исходное устройство — это устройство, с которого была создана резервная копия базы данных, а целевое устройство — это устройство, на которое будет восстановлена база данных.  
  
 При восстановлении базы данных статистика не пересчитывается автоматически.  
  
 На одном устройстве в один момент времени может быть запущена только одна из инструкций RESTORE DATABASE или BACKUP DATABASE. Если одновременно было отправлено несколько инструкций резервного копирования и восстановления, устройство поместит их в очередь и будет обрабатывать их по одной.  
  
 Восстановить резервную копию базы данных можно только на целевое устройство [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], количество вычислительных узлов на котором не меньше количества узлов на исходном устройстве. Количество вычислительных узлов на целевом устройстве не может быть меньше количества вычислительных узлов на исходном устройстве.  
  
 Вы не можете восстановить резервную копию, которая была создана на устройстве с оборудованием SQL Server 2012 PDW, на устройство с оборудованием SQL Server 2008 R2. Это справедливо даже в том случае, если устройство было изначально приобретено с оборудованием SQL Server 2008 R2 PDW, а сейчас на нем запущено программное обеспечение SQL Server 2012 PDW.  
  
## <a name="locking"></a>Блокировка  
 Осуществляет монопольную блокировку объекта DATABASE.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-simple-restore-examples"></a>A. Простые примеры использования инструкции RESTORE  
 В следующем примере восстанавливается полная резервная копия в базу данных `SalesInvoices2013`. Файлы резервной копии сохраняются в каталоге \\\xxx.xxx.xxx.xxx\backups\yearly\Invoices2013Full. База данных SalesInvoices2013 не может существовать на целевом устройстве, в противном случае команда завершится с ошибкой.  
  
```  
RESTORE DATABASE SalesInvoices2013  
FROM DISK = '\\xxx.xxx.xxx.xxx\backups\yearly\Invoices2013Full';  
```  
  
### <a name="b-restore-a-full-and-differential-backup"></a>Б. Восстановление полной и разностной резервной копии  
 В следующем примере восстанавливается полная и разностная резервная копия базы данных SalesInvoices2013  
  
 Полная резервная копия базы данных восстанавливается из полной резервной копии, которая хранится в каталоге '\\\xxx.xxx.xxx.xxx\backups\yearly\Invoices2013Full'. Если восстановление завершится успешно, разностная резервная копия восстанавливается в базу данных SalesInvoices2013.  Разностная резервная копия сохраняется в каталоге '\\\xxx.xxx.xxx.xxx\backups\yearly\Invoices2013Diff'.  
  
```  
RESTORE DATABASE SalesInvoices2013  
    FROM DISK = '\\xxx.xxx.xxx.xxx\backups\yearly\Invoices2013Diff'  
    WITH BASE = '\\xxx.xxx.xxx.xxx\backups\yearly\Invoices2013Full'  
[;]  
  
```  
  
### <a name="c-restoring-the-backup-header"></a>В. Восстановление заголовка резервной копии  
 В этом примере восстанавливаются данные заголовка для резервной копии базы данных '\\\xxx.xxx.xxx.xxx\backups\yearly\Invoices2013Full'. Результаты выполнения команды в одной строке для резервной копии Invoices2013Full.  
  
```  
RESTORE HEADERONLY  
    FROM DISK = '\\xxx.xxx.xxx.xxx\backups\yearly\Invoices2013Full'  
[;]  
```  
  
 Данные заголовка можно использовать для проверки содержимого резервной копии, или чтобы убедиться в том, что целевое устройство восстановления совместимо с исходным устройством резервного копирования, перед восстановлением резервной копии.  
  
## <a name="see-also"></a>См. также:  
 [BACKUP DATABASE (Parallel Data Warehouse)](../../t-sql/statements/backup-database-parallel-data-warehouse.md)  
  
  
