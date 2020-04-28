---
title: Репликация на подписчиков, оптимизированных для памяти таблиц | Документация Майкрософт
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
ms.assetid: 1a8e6bc7-433e-471d-b646-092dc80a2d1a
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b9f58e472b0b6e6d164e45c2d1136c81bc4a46d6
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68811226"
---
# <a name="replication-to-memory-optimized-table-subscribers"></a>Репликация на подписчиков оптимизированных для памяти таблиц
  Таблицы, выступающие в качестве подписчиков репликации транзакций, за исключением одноранговой репликации транзакций, можно настроить как оптимизированные для памяти таблицы. Другие конфигурации репликации несовместимы с таблицами, оптимизированными для памяти.  
  
## <a name="configuring-a-memory-optimized-table-as-a-subscriber"></a>Настройка оптимизированной для памяти таблицы в качестве подписчика  
 Чтобы настроить оптимизированную для памяти таблицу в качестве подписчика, выполните следующие действия.  
  
 **Создание и включение публикации**  
  
1.  Создание публикации.  
  
2.  Добавьте статьи к публикации. Для параметра `@upd_cmd` используются соглашения SCALL или SQL.  
  
    ```  
    EXEC sp_addarticle  
        @publication = N'Publication1',  
        @article = N'Mem_Table',  
        @source_owner = N'dbo',  
        @source_object = N'Mem_Table',  
        @type = N'logbased',  
        @description = null,  
        @creation_script = null,  
        @pre_creation_cmd = N'none',  
        @schema_option = 0x00000000080050DF,  
        @identityrangemanagementoption = N'manual',  
        @destination_table = N'Mem_Table',  
        @destination_owner = N'dbo',  
        @vertical_partition = N'false',  
        @ins_cmd = N'CALL sp_MSins_Mem_Table',  
        @del_cmd = N'CALL sp_MSdel_Mem_Table',  
        @upd_cmd = N'SCALL sp_MSupd_Mem_Table';  
    GO  
    ```  
  
 **Создание моментального снимка и изменение схемы**  
  
1.  Создайте задание моментального снимка и сформируйте моментальный снимок.  
  
    ```  
    EXEC sp_addpublication_snapshot @publication = N'Publication1', @frequency_type = 1;  
    EXEC sp_startpublication_snapshot @publication = N'Publication1';  
    ```  
  
2.  Перейдите в папку моментальных снимков. Расположение по умолчанию — «C:\Program Files\Microsoft SQL Server\MSSQL12. \<Экземпляр> \мсскл\реплдата\унк\кскскс\ииииммддххммсс\\".  
  
3.  Нахождение **. SCH** File для таблицы и открывается в Management Studio. Измените схему таблицы и обновите хранимую процедуру, как описано ниже.  
  
     Вычислите индексы, определенные в IDX-файле. Измените инструкцию `CREATE TABLE`, чтобы указать необходимые индексы, ограничения, первичный ключ и оптимизированный для памяти синтаксис. В оптимизированных для памяти таблицах столбцы индексов НЕ должны иметь значение NULL, а столбцов индексов с символьными типами данных должны быть представлены в Юникоде и использовать параметры сортировки BIN2. См. пример далее.  
  
    ```  
    SET ANSI_PADDING ON;  
    GO  
  
    SET ANSI_NULLS ON;  
    GO  
  
    SET QUOTED_IDENTIFIER ON;  
    GO  
  
    CREATE TABLE [dbo].[Mem_Table]([c1] [int] NOT NULL,  
        [c2] [float] NOT NULL,  
        [c3] [decimal](10, 2) NOT NULL,  
        [c4] [nvarchar](5) COLLATE SQL_Latin1_General_CP850_BIN2 NOT NULL,  
        INDEX [hash_index_sample_memoryoptimizedtable_c2] HASH (c2) WITH (BUCKET_COUNT = 1024),  
        INDEX [index_sample_memoryoptimizedtable_c3] NONCLUSTERED ([c3]),  
        INDEX [nvarchar_index_sample_memoryoptimizedtable_c4] ([c4]),  
        CONSTRAINT [PK_sample_memoryoptimizedtable] PRIMARY KEY NONCLUSTERED ([c1])) WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_AND_DATA);  
    GO  
    ```  
  
4.  При использовании соглашения SCALL для параметра `@upd_cmd` перейдите к файлу схемы (SCH) и измените инструкцию обновления таблицы в `create procedure [sp_MSupd_<SCHEMA><TABLE_NAME>]`, удалив столбцы первичного ключа.  
  
     Для поддержки обновления первичного ключа используйте пользовательскую хранимую процедуру обновления, заменив ей инструкцию обновления первичного ключа, следующим образом.  
  
    1.  Выберите отсутствующие значения столбцов (SCALL предоставляет только столбец, задействованный в операции обновления).  
  
    2.  Удалите существующую запись.  
  
    3.  Вставьте новую запись с новыми значениями, в том числе с новым первичным ключом.  
  
     Первоначальная процедура обновления выглядит следующим образом.  
  
    ```  
    create procedure [sp_MSupd_Mem_Table]  
                   @c1 int = NULL,  
                   @c2 float = NULL,  
                   @c3 decimal(10,2) = NULL,  
                   @c4 nvarchar(5) = NULL,  
                   @pkc1 int = NULL,  
                   @bitmap binary(1)  
    as  
    begin    
    if (substring(@bitmap,1,1) & 1 = 1)  
    begin   
    update [dbo].[Mem_Table] set  
                   [c1] = case substring(@bitmap,1,1) & 1 when 1 then @c1 else [c1] end,  
                   [c2] = case substring(@bitmap,1,1) & 2 when 2 then @c2 else [c2] end,  
                   [c3] = case substring(@bitmap,1,1) & 4 when 4 then @c3 else [c3] end,  
                   [c4] = case substring(@bitmap,1,1) & 8 when 8 then @c4 else [c4] end  
    where [c1] = @pkc1  
    if @@rowcount = 0  
        if @@microsoftversion>0x07320000  
            exec sp_MSreplraiserror 20598  
    end    
    else  
    begin   
    update [dbo].[Mem_Table] set  
                   [c2] = case substring(@bitmap,1,1) & 2 when 2 then @c2 else [c2] end,  
                   [c3] = case substring(@bitmap,1,1) & 4 when 4 then @c3 else [c3] end,  
                   [c4] = case substring(@bitmap,1,1) & 8 when 8 then @c4 else [c4] end  
    where [c1] = @pkc1  
    if @@rowcount = 0  
        if @@microsoftversion>0x07320000  
            exec sp_MSreplraiserror 20598  
    end   
    end   
    go  
    ```  
  
     Если первичный ключ никогда не должен обновляться у издателя. Закомментируйте обновление таких столбцов в процедуре обновления следующим образом.  
  
    ```  
    create procedure [sp_MSupd_Mem_Table]  
                   @c1 int = NULL,  
                   @c2 float = NULL,  
                   @c3 decimal(10,2) = NULL,  
                   @c4 nvarchar(5) = NULL,  
                   @pkc1 int = NULL,  
                   @bitmap binary(1)  
    as  
    begin    
    if (substring(@bitmap,1,1) & 1 = 1)  
    begin   
    update [dbo].[Mem_Table] set  
    --             [c1] = case substring(@bitmap,1,1) & 1 when 1 then @c1 else [c1] end,  
                   [c2] = case substring(@bitmap,1,1) & 2 when 2 then @c2 else [c2] end,  
                   [c3] = case substring(@bitmap,1,1) & 4 when 4 then @c3 else [c3] end,  
                   [c4] = case substring(@bitmap,1,1) & 8 when 8 then @c4 else [c4] end  
    where [c1] = @pkc1  
    if @@rowcount = 0  
        if @@microsoftversion>0x07320000  
            exec sp_MSreplraiserror 20598  
    end    
    else  
    begin   
    update [dbo].[Mem_Table] set  
                   [c2] = case substring(@bitmap,1,1) & 2 when 2 then @c2 else [c2] end,  
                   [c3] = case substring(@bitmap,1,1) & 4 when 4 then @c3 else [c3] end,  
                   [c4] = case substring(@bitmap,1,1) & 8 when 8 then @c4 else [c4] end  
    where [c1] = @pkc1  
    if @@rowcount = 0  
        if @@microsoftversion>0x07320000  
            exec sp_MSreplraiserror 20598  
    end   
    end   
    go  
    ```  
  
     Чтобы разрешить поддержку обновлений первичного ключа, добавьте чтение в процедуру обновления следующим образом.  
  
    ```  
    create procedure [sp_MSupd_Mem_Table]  
                   @c1 int = NULL,  
                   @c2 float = NULL,  
                   @c3 decimal(10,2) = NULL,  
                   @c4 nvarchar(5) = NULL,  
                    @pkc1 int = NULL,  
                   @bitmap binary(1)  
    as  
    begin    
    if (substring(@bitmap,1,1) & 1 = 1)  
    begin   
    select  
                   @c1 = case substring(@bitmap,1,1) & 1 when 1 then @c1 else [c1] end,  
                   @c2 = case substring(@bitmap,1,1) & 2 when 2 then @c2 else [c2] end,  
                   @c3 = case substring(@bitmap,1,1) & 4 when 4 then @c3 else [c3] end,  
                   @c4 = case substring(@bitmap,1,1) & 8 when 8 then @c4 else [c4] end  
    from [dbo].[Mem_Table] where [c1] = @pkc1  
    if @@rowcount <> 0 begin  
            delete [dbo].[Mem_Table] where [c1] = @pkc1  
            if @@rowcount <> 0  
                   insert into [dbo].[Mem_Table]([c1],  
                           [c2],  
                           [c3],  
                           [c4]) values (  
                           @c1,  
                           @c2,  
                           @c3,  
                           @c4  
                   )   
    end  
    if @@rowcount = 0  
        if @@microsoftversion>0x07320000  
            exec sp_MSreplraiserror 20598  
    end    
    else  
    begin   
    update [dbo].[Mem_Table] set  
                   [c2] = case substring(@bitmap,1,1) & 2 when 2 then @c2 else [c2] end,  
                   [c3] = case substring(@bitmap,1,1) & 4 when 4 then @c3 else [c3] end,  
                   [c4] = case substring(@bitmap,1,1) & 8 when 8 then @c4 else [c4] end  
    where [c1] = @pkc1  
    if @@rowcount = 0  
        if @@microsoftversion>0x07320000  
            exec sp_MSreplraiserror 20598  
    end   
    end   
    go  
    ```  
  
5.  Создайте базу данных подписчика с помощью параметра " **повысить уровень изоляции моментального снимка** " и задайте для параметров сортировки по умолчанию значение Latin1_General_CS_AS_KS_WS в случае использования символьных типов данных, отличных от Юникода.  
  
    ```  
    CREATE DATABASE [Sub]   
    CONTAINMENT = NONE   
    ON PRIMARY ( NAME = [Sub], FILENAME = [C:\Program Files\Microsoft SQL Server\MSSQL12\MSSQL\DATA\Sub.mdf]),   
    FILEGROUP [mem] CONTAINS MEMORY_OPTIMIZED_DATA ( NAME = [mem],   
    FILENAME = [C:\Program Files\Microsoft SQL Server\MSSQL12\MSSQL\DATA\Sub])  
    LOG ON ( NAME = [Sub_log], FILENAME = [C:\Program Files\Microsoft SQL Server\MSSQL12\MSSQL\DATA\Sub.ldf])  
    COLLATE Latin1_General_CS_AS_KS_WS;  
  
    ALTER DATABASE [Sub] SET MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT = ON;  
    GO  
    ```  
  
6.  Примените схему к базе данных подписчика и сохраните схему для последующего использования.  
  
7.  Загрузка данных издателя (источник) на подписчик. Данные на издателе не должны изменяться до тех пор, пока не будет добавлена подписка.  Можно использовать BCP, как показано ниже.  
  
    ```  
    bcp Pub.dbo.Mem_Table out Mem_Table.bcp -S. -T -C1252 -n  
    bcp Sub.dbo.Mem_Table in Mem_Table.bcp -S. -T -C1252 -n  
    ```  
  
8.  Измените статью, отключив изменения схемы на подписчике.  
  
    ```  
    EXEC sp_changearticle  
        @publication = N'Publication1',  
        @article = N'Mem_Table',  
        @property = N'schema_option',  
        @value = 0,  
        @force_invalidate_snapshot = 1,  
        @force_reinit_subscription = 1;  
    GO  
    ```  
  
 **Добавление подписки no sync**  
  
 Добавьте подписку nosync.  
  
```  
EXEC sp_addsubscription  
    @publication = N' Publication1',  
    @subscriber = @@ServerName,  
    @destination_db = N'Sub',  
    @subscription_type = N'Push',  
    @sync_type = N'replication support only',  
    @article = N'all',  
    @update_mode = N'read only',  
    @subscriber_type = 0;  
GO  
```  
  
 После этого оптимизированные для памяти таблицы должны начать получать обновления от издателя.  
  
## <a name="restrictions"></a>Ограничения  
 Поддерживается только односторонняя репликация транзакций. Одноранговая репликация транзакций не поддерживается.  
  
 Оптимизированные для памяти таблицы нельзя публиковать.  
  
 Таблицы репликации на распространителе нельзя настраивать в качестве оптимизированных для памяти таблиц.  
  
 Репликация слиянием не может содержать оптимизированные для памяти таблицы.  
  
 Таблицы, участвующие в репликации транзакций можно настроить на подписчике как оптимизированные для памяти таблицы, но таблицы подписчика должны соответствовать требованиям к оптимизированным для памяти таблицам. Для этого необходимы следующие ограничения.  
  
-   Чтобы создать оптимизированную для памяти таблицу на подписчике репликации транзакций, файлы схемы моментального снимка, используемые для создания оптимизированных для памяти таблиц, необходимо изменить вручную. Дополнительные сведения см. [в разделе изменение файла схемы](#Schema).  
  
-   На таблицы, которые реплицируются в оптимизированные для памяти таблицы на подписчике, налагается ограничение в 8060 байт на строку оптимизированных для памяти таблиц.  
  
-   В таблицах, которые реплицируются в оптимизированные для памяти таблицы на подписчике, можно использовать только типы данных, разрешенные в оптимизированных для памяти таблицах. Дополнительные сведения см. в разделе [Поддерживаемые типы данных](../in-memory-oltp/supported-data-types-for-in-memory-oltp.md).  
  
-   Имеются ограничения на обновление первичного ключа таблиц, которые реплицируются в оптимизированную для памяти таблицу на подписчике. Дополнительные сведения см. [в разделе Репликация изменений в первичный ключ](#PrimaryKey).  
  
-   Внешний ключ, ограничение уникальности, триггеры, изменения схемы, ROWGUIDCOL, вычисляемые столбцы, сжатие данных, псевдонимы типов данных, управление версиями и блокировки не поддерживаются в оптимизированных для памяти таблицах. Сведения см. в разделе [Transact-SQL Constructs Not Supported by In-Memory OLTP](../in-memory-oltp/transact-sql-constructs-not-supported-by-in-memory-oltp.md) .  
  
##  <a name="modifying-a-schema-file"></a><a name="Schema"></a>Изменение файла схемы  
  
-   Кластеризованные индексы не поддерживаются. Измените любые кластеризованные индексы на некластеризованные индексы.  
  
-   Все столбцы в ключе индекса должна быть определены как `NOT NULL`.  
  
-   Если используется параметр `DURABILITY = SCHEMA_AND_DATA` оптимизированной для памяти таблицы, то таблица должна иметь некластеризованный индекс первичного ключа.  
  
-   Параметр ANSI_PADDING должен быть установлен в значение ON.  
  
##  <a name="replicating-changes-to-a-primary-key"></a><a name="PrimaryKey"></a>Репликация изменений в первичный ключ  
 Первичный ключ оптимизированной для памяти таблицы нельзя обновить. Для репликации обновлений первичного ключа на подписчике измените хранимую процедуру обновления так, чтобы обновления доставлялись в виде пары удаления и вставки.  
  
## <a name="see-also"></a>См. также:  
 [Репликация SQL Server](sql-server-replication.md)  
  
  
