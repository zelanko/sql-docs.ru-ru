---
title: Создание моментального снимка базы данных (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- database snapshots [SQL Server], creating
ms.assetid: 187fbba3-c555-4030-9bdf-0f01994c5230
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3f577f7798da2ba7b7ee4259ecc98994f713cfc5
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/25/2020
ms.locfileid: "62762347"
---
# <a name="create-a-database-snapshot-transact-sql"></a>создать моментальный снимок базы данных (Transact-SQL)
  Единственный способ создания моментального снимка базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] состоит в использовании [!INCLUDE[tsql](../../includes/tsql-md.md)]. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] не поддерживает создание моментальных снимков базы данных.  
  
-   **Перед началом работы**  
  
     [Предварительные условия](#Prerequisites)  
  
     [Безопасность](#Security)  
  
     [Рекомендации. Присвоение имен моментальным снимкам базы данных](#Naming)  
  
-   **Создание моментального снимка базы данных с помощью:**  [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> Предварительные требования  
 База данных-источник, в которой может применяться любая модель восстановления, должна соответствовать следующим предварительным требованиям.  
  
-   На экземпляре сервера должен быть запущен выпуск [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , который поддерживает моментальные снимки баз данных. Сведения о поддержке моментальных снимков базы данных в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]см. в разделе [функции, поддерживаемые различными выпусками SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
-   База данных-источник должна быть в режиме в сети, если база данных не является зеркальной в сеансе зеркального отображения базы данных.  
  
-   Для создания моментального снимка в зеркальной базе данных эта база данных должна быть в синхронизированном[состоянии зеркального отображения](../../database-engine/database-mirroring/mirroring-states-sql-server.md).  
  
-   База данных-источник не может быть настроена в качестве масштабируемой общей базы данных.  
  
> [!IMPORTANT]  
>  Сведения о других существенных соображениях см. в разделе [Моментальные снимки базы данных (SQL Server)](database-snapshots-sql-server.md).  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> Рекомендации  
 В этом разделе обсуждаются следующие рекомендации:  
  
-   [Рекомендации. Присвоение имен моментальным снимкам базы данных](#Naming)  
  
-   [Рекомендации. Ограничение количества моментальных снимков базы данных](#Limiting_Number)  
  
-   [Рекомендации. Клиентские соединения с моментальным снимком базы данных](#Client_Connections)  
  
####  <a name="best-practice-naming-database-snapshots"></a><a name="Naming"></a> Рекомендации. Присвоение имен моментальным снимкам базы данных  
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
  
####  <a name="best-practice-limiting-the-number-of-database-snapshots"></a><a name="Limiting_Number"></a>Рекомендации: ограничение количества моментальных снимков базы данных  
 Благодаря созданию моментальных снимков через определенные промежутки времени формируется последовательность снимков базы данных-источника. Каждый моментальный снимок существует до тех пор, пока явно не удаляется. Поскольку каждый моментальный снимок будет продолжать расти по мере обновления первоначальных страниц, возможно, потребуется освободить место на диске для новых снимков за счет удаления старых.  
  
> [!NOTE]  
>  Чтобы восстановить моментальный снимок базы данных, необходимо удалить все другие снимки из базы данных.  
  
####  <a name="best-practice-client-connections-to-a-database-snapshot"></a><a name="Client_Connections"></a>Рекомендации: клиентские соединения с моментальным снимком базы данных  
 Чтобы подключиться к моментальному снимку базы данных, клиенты должны знать, где его найти. Пользователи могут работать с одним моментальным снимком базы данных во время создания или удаления другого. Тем не менее при замене существующего снимка новым необходимо перенаправить клиентов на новый снимок. Пользователи могут вручную подключиться к моментальному снимку базы данных средствами среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Тем не менее в рабочей среде следует создать программное решение, которое неявным для клиента образом направляет приложения, формирующие отчеты, к последнему моментальному снимку базы данных.  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Любой пользователь, который может создать базу данных, может создать и моментальный снимок базы данных. Однако для создания моментального снимка зеркальной базы данных необходимо быть членом предопределенной роли сервера **sysadmin** .  
  
##  <a name="how-to-create-a-database-snapshot-using-transact-sql"></a><a name="TsqlProcedure"></a> Как создать моментальный снимок базы данных (с использованием языка Transact-SQL)  
 **Создание моментального снимка базы данных**  
  
> [!NOTE]  
>  Пример этой процедуры см. в подразделе [Примеры (Transact-SQL)](#TsqlExample)далее в этом разделе.  
  
1.  На основании текущего размера базы данных-источника убедитесь, что на диске достаточно места для хранения моментального снимка базы данных. При создании моментального снимка максимальный размер моментального снимка базы данных равен размеру базы данных-источника. Дополнительные сведения см. в разделе [Просмотр размера разреженного файла снимка базы данных (Transact-SQL)](view-the-size-of-the-sparse-file-of-a-database-snapshot-transact-sql.md).  
  
2.  Используйте инструкцию CREATE DATABASE для файлов с помощью предложения AS SNAPSHOT OF. Создание моментального снимка требует указания логического имени каждого файла базы данных-источника. Синтаксис:  
  
     CREATE DATABASE *имя_снимка_базы_данных*  
  
     ON  
  
     (  
  
     NAME =*logical_file_name*,  
  
     FILENAME ='*имя_файла_ОС*'  
  
     ) [ ,...*n* ]  
  
     AS SNAPSHOT OF *source_database_name*  
  
     [;]  
  
     Где *source_ * * database_name* является базой данных-источником, *logical_file_name я использую*логическое имя, используемое в SQL Server при обращении к файлу, *os_file_name* — это путь и имя файла, используемые операционной системой при создании файла, а *database_snapshot_name* — имя моментального снимка, в который нужно вернуть базу данных. Полное описание этого синтаксиса см. в разделе [CREATE DATABASE (SQL Server Transact-SQL)](/sql/t-sql/statements/create-database-sql-server-transact-sql).  
  
    > [!NOTE]  
    >  При создании моментального снимка базы данных файлы журнала файлы в режиме вне сети, восстанавливаемые из копии файлы и нефункционирующие файлы являются недопустимыми в инструкции CREATE DATABASE.  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a>Примеры (Transact-SQL)  
  
> [!NOTE]  
>  Расширение `.ss` , используемое в примерах, выбрано произвольно.  
  
 Этот раздел содержит следующие примеры.  
  
-   А) [Создание моментального снимка по базе данных AdventureWorks](#Creating_on_AW)  
  
-   Б) [Создание моментального снимка по базе данных Sales](#Creating_on_Sales)  
  
####  <a name="a-creating-a-snapshot-on-the-adventureworks-database"></a><a name="Creating_on_AW"></a> A. Создание моментального снимка по базе данных AdventureWorks  
 В этом примере создается моментальный снимок базы данных по базе данных `AdventureWorks` . Имя моментального снимка `AdventureWorks_dbss_1800`и имя файла его разреженного файла `AdventureWorks_data_1800.ss`указывают на время создания — 18:00.  
  
```  
CREATE DATABASE AdventureWorks_dbss1800 ON  
( NAME = AdventureWorks_Data, FILENAME =   
'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Data\AdventureWorks_data_1800.ss' )  
AS SNAPSHOT OF AdventureWorks;  
GO  
```  
  
####  <a name="b-creating-a-snapshot-on-the-sales-database"></a><a name="Creating_on_Sales"></a> Б. Создание моментального снимка по базе данных Sales  
 Этот пример создает моментальный снимок `sales_snapshot1200`базы данных `Sales` . Эта база данных была создана в примере «создание базы данных с файловыми группами» в [&#40;«создание базы данных» SQL Server&#41;Transact-SQL ](/sql/t-sql/statements/create-database-sql-server-transact-sql).  
  
```  
--Creating sales_snapshot1200 as snapshot of the  
--Sales database:  
CREATE DATABASE sales_snapshot1200 ON  
( NAME = SPri1_dat, FILENAME =   
'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\data\SPri1dat_1200.ss'),  
( NAME = SPri2_dat, FILENAME =   
'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\data\SPri2dt_1200.ss'),  
( NAME = SGrp1Fi1_dat, FILENAME =   
'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\mssql\data\SG1Fi1dt_1200.ss'),  
( NAME = SGrp1Fi2_dat, FILENAME =   
'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\data\SG1Fi2dt_1200.ss'),  
( NAME = SGrp2Fi1_dat, FILENAME =   
'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\data\SG2Fi1dt_1200.ss'),  
( NAME = SGrp2Fi2_dat, FILENAME =   
'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\data\SG2Fi2dt_1200.ss')  
AS SNAPSHOT OF Sales;  
GO  
```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Связанные задачи  
  
-   [Просмотр моментального снимка базы данных (SQL Server)](view-a-database-snapshot-sql-server.md)  
  
-   [Восстановление базы данных до состояния, сохраненного в моментальном снимке](revert-a-database-to-a-database-snapshot.md)  
  
-   [Удаление моментального снимка базы данных (Transact-SQL)](drop-a-database-snapshot-transact-sql.md)  
  
## <a name="see-also"></a>См. также:  
 [CREATE DATABASE (SQL Server Transact-SQL)](/sql/t-sql/statements/create-database-sql-server-transact-sql)   
 [Моментальные снимки базы данных (SQL Server)](database-snapshots-sql-server.md)  
  
  
