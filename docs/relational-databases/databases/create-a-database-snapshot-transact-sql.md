---
title: Создание моментального снимка базы данных (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: databases
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- database snapshots [SQL Server], creating
ms.assetid: 187fbba3-c555-4030-9bdf-0f01994c5230
caps.latest.revision: 56
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: f25cffe0f57d1600e4d72eb1d061e27caaec4371
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="create-a-database-snapshot-transact-sql"></a>создать моментальный снимок базы данных (Transact-SQL)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Единственный способ создания моментального снимка базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] состоит в использовании [!INCLUDE[tsql](../../includes/tsql-md.md)]. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] не поддерживает создание моментальных снимков базы данных.  
  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Prerequisites"></a> Предварительные требования  
 База данных-источник, в которой может применяться любая модель восстановления, должна соответствовать следующим предварительным требованиям.  
  
-   На экземпляре сервера должен быть запущен выпуск [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , который поддерживает моментальные снимки баз данных. Сведения о поддержке снимков баз данных в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]см. в разделе [Функции, поддерживаемые выпусками SQL Server 2016](~/sql-server/editions-and-supported-features-for-sql-server-2016.md).  
  
-   База данных-источник должна быть в режиме в сети, если база данных не является зеркальной в сеансе зеркального отображения базы данных.  
  
-   Для создания снимка базы данных в зеркальной базе данных необходимо привести эту базу данных в синхронизированное [состояние зеркального отображения](../../database-engine/database-mirroring/mirroring-states-sql-server.md).  
  
-   База данных-источник не может быть настроена в качестве масштабируемой общей базы данных.  

- База данных-источник не должна содержать файловую группу MEMORY_OPTIMIZED_DATA. Дополнительные сведения см. в разделе [Неподдерживаемые функции SQL Server для выполняющейся в памяти OLTP](../../relational-databases/in-memory-oltp/unsupported-sql-server-features-for-in-memory-oltp.md).

>  [!IMPORTANT]
> Сведения о других существенных соображениях см. в разделе [Моментальные снимки базы данных (SQL Server)](../../relational-databases/databases/database-snapshots-sql-server.md).  
  
##  <a name="Recommendations"></a> Рекомендации  
 В этом разделе обсуждаются следующие рекомендации:  
  
-   [Рекомендации. Присвоение имен моментальным снимкам базы данных](#Naming)  
  
-   [Рекомендации. Ограничение количества моментальных снимков базы данных](#Limiting_Number)  
  
-   [Рекомендации. Клиентские соединения с моментальным снимком базы данных](#Client_Connections)  
  
####  <a name="Naming"></a> Рекомендации. Присвоение имен моментальным снимкам базы данных  
 Перед созданием моментальных снимков важно присвоить им правильные имена. Имя каждого моментального снимка базы данных должно быть уникальным в пределах базы данных. Чтобы упростить управление, моментальному снимку следует присвоить имя, которое позволяет определить базу данных, например:  
  
-   Определяет имя исходной базы данных.  
  
-   признак того, что новое имя предназначено для моментального снимка;  
  
-   дату и время создания моментального снимка, порядковый номер или другие сведения, например время в течение дня, которые позволяют отличить моментальные снимки этой базы данных друг от друга.  
  
 Допустим, требуется создать последовательность моментальных снимков базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] . Три ежесуточных моментальных снимка были созданы через шестичасовые интервалы между 6:00. и 18:00 на основе 24-часового отсчета времени. Каждый моментальный снимок хранится 24 часа, после этого он удаляется и заменяется одноименным снимком. Обратите внимание, что имя моментального снимка обозначает час, но не дату создания:  
  
```  
AdventureWorks_snapshot_0600  
AdventureWorks_snapshot_1200  
AdventureWorks_snapshot_1800  
```  
  
 Если время создания моментального снимка изменяется, можно использовать менее точные обозначения, например:  
  
```  
AdventureWorks_snapshot_morning  
AdventureWorks_snapshot_noon  
AdventureWorks_snapshot_evening  
```  
  
#### <a name="Limiting_Number"></a> Рекомендации. Ограничение количества моментальных снимков базы данных  
 Благодаря созданию моментальных снимков через определенные промежутки времени формируется последовательность снимков базы данных-источника. Каждый моментальный снимок существует до тех пор, пока явно не удаляется. Поскольку каждый моментальный снимок будет продолжать расти по мере обновления первоначальных страниц, возможно, потребуется освободить место на диске для новых снимков за счет удаления старых.  
  

**Примечание.** Чтобы восстановить моментальный снимок базы данных, необходимо удалить все другие снимки из базы данных.  
  
####  <a name="Client_Connections"></a> Рекомендации. Клиентские соединения с моментальным снимком базы данных  
 Чтобы подключиться к моментальному снимку базы данных, клиенты должны знать, где его найти. Пользователи могут работать с одним моментальным снимком базы данных во время создания или удаления другого. Тем не менее при замене существующего снимка новым необходимо перенаправить клиентов на новый снимок. Пользователи могут вручную подключиться к моментальному снимку базы данных средствами среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Тем не менее в рабочей среде следует создать программное решение, которое неявным для клиента образом направляет приложения, формирующие отчеты, к последнему моментальному снимку базы данных.  
  

  
####  <a name="Permissions"></a> Permissions  
 Любой пользователь, который может создать базу данных, может создать и моментальный снимок базы данных. Однако для создания моментального снимка зеркальной базы данных необходимо быть членом предопределенной роли сервера **sysadmin** .  
  
##  <a name="TsqlProcedure"></a> Как создать моментальный снимок базы данных (с использованием языка Transact-SQL)  
 **Создание моментального снимка базы данных**  
  
>  Пример этой процедуры см. в подразделе [Примеры (Transact-SQL)](#TsqlExample)далее в этом разделе.  
  
1.  На основании текущего размера базы данных-источника убедитесь, что на диске достаточно места для хранения моментального снимка базы данных. При создании моментального снимка максимальный размер моментального снимка базы данных равен размеру базы данных-источника. Дополнительные сведения см. в разделе [Просмотр размера разреженного файла снимка базы данных (Transact-SQL)](../../relational-databases/databases/view-the-size-of-the-sparse-file-of-a-database-snapshot-transact-sql.md).  
  
2.  Используйте инструкцию CREATE DATABASE для файлов с помощью предложения AS SNAPSHOT OF. Создание моментального снимка требует указания логического имени каждого файла базы данных-источника. Синтаксис:  
  
     CREATE DATABASE *имя_снимка_базы_данных*  
  
     ON  
  
     (  
  
     NAME =*логическое_имя_файла*,  
  
     FILENAME ='*имя_файла_ОС*'  
  
     ) [ ,...*n* ]  
  
     AS SNAPSHOT OF *имя_исходной_базы_данных*  
  
     [;]  
  
     Здесь *имя_**исходной_базы_данных* — это исходная база данных, *логическое_имя_файла* — это логическое имя, используемое в SQL Server при ссылке на файл, *имя_файла_ОС* — это путь и имя файла, используемые операционной системой при создании файла, а *имя_снимка_базы данных* — это имя снимка, на основе которого требуется восстановить базу данных. Полное описание этого синтаксиса см. в разделе [CREATE DATABASE (SQL Server Transact-SQL)](../../t-sql/statements/create-database-sql-server-transact-sql.md).  
  
    > [!NOTE]  
    >  При создании моментального снимка базы данных файлы журнала файлы в режиме вне сети, восстанавливаемые из копии файлы и нефункционирующие файлы являются недопустимыми в инструкции CREATE DATABASE.  
  
###  <a name="TsqlExample"></a> Примеры (Transact-SQL)  
  
> [!NOTE]  
>  Расширение `.ss` , используемое в примерах, выбрано произвольно.  
  
 Этот раздел содержит следующие примеры.  
  
-   A. [Создание моментального снимка по базе данных AdventureWorks](#Creating_on_AW)  
  
-   Б. [Создание моментального снимка по базе данных Sales](#Creating_on_Sales)  
  
####  <a name="Creating_on_AW"></a> A. Создание моментального снимка по базе данных AdventureWorks  
 В этом примере создается моментальный снимок базы данных по базе данных `AdventureWorks` . Имя моментального снимка `AdventureWorks_dbss_1800`и имя файла его разреженного файла `AdventureWorks_data_1800.ss`указывают на время создания — 18:00.  
  
```  
CREATE DATABASE AdventureWorks_dbss1800 ON  
( NAME = AdventureWorks_Data, FILENAME =   
'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Data\AdventureWorks_data_1800.ss' )  
AS SNAPSHOT OF AdventureWorks;  
GO  
```  
  
####  <a name="Creating_on_Sales"></a> Б. Создание моментального снимка по базе данных Sales  
 Этот пример создает моментальный снимок `sales_snapshot1200`базы данных `Sales` . Эта база данных была создана в примере "Создание базы данных, которая содержит файловые группы" раздела [CREATE DATABASE (SQL Server Transact-SQL)](../../t-sql/statements/create-database-sql-server-transact-sql.md).  
  
```  
--Creating sales_snapshot1200 as snapshot of the  
--Sales database:  
CREATE DATABASE sales_snapshot1200 ON  
( NAME = SPri1_dat, FILENAME =   
'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\data\SPri1dat_1200.ss'),  
( NAME = SPri2_dat, FILENAME =   
'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\data\SPri2dt_1200.ss'),  
( NAME = SGrp1Fi1_dat, FILENAME =   
'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\mssql\data\SG1Fi1dt_1200.ss'),  
( NAME = SGrp1Fi2_dat, FILENAME =   
'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\data\SG1Fi2dt_1200.ss'),  
( NAME = SGrp2Fi1_dat, FILENAME =   
'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\data\SG2Fi1dt_1200.ss'),  
( NAME = SGrp2Fi2_dat, FILENAME =   
'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\data\SG2Fi2dt_1200.ss')  
AS SNAPSHOT OF Sales;  
GO  
```  
  
##  <a name="RelatedTasks"></a> Связанные задачи  
  
-   [Просмотр моментального снимка базы данных (SQL Server)](../../relational-databases/databases/view-a-database-snapshot-sql-server.md)  
  
-   [Восстановление базы данных до состояния, сохраненного в моментальном снимке](../../relational-databases/databases/revert-a-database-to-a-database-snapshot.md)  
  
-   [Удаление моментального снимка базы данных (Transact-SQL)](../../relational-databases/databases/drop-a-database-snapshot-transact-sql.md)  
  
## <a name="see-also"></a>См. также:  
 [CREATE DATABASE (SQL Server Transact-SQL)](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [Моментальные снимки базы данных (SQL Server)](../../relational-databases/databases/database-snapshots-sql-server.md)  
  
  

