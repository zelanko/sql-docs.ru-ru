---
title: "Репликация на подписчиков оптимизированных для памяти таблиц | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "11/21/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1a8e6bc7-433e-471d-b646-092dc80a2d1a
caps.latest.revision: 23
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 23
---
# Репликация на подписчиков оптимизированных для памяти таблиц
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Таблицы, выступающие в качестве подписчиков моментальных снимков и репликации транзакций, за исключением одноранговой репликации транзакций, можно настроить как оптимизированные для памяти таблицы. Другие конфигурации репликации несовместимы с таблицами, оптимизированными для памяти. Эта функция доступна в [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)].  
  
## <a name="two-configurations-are-required"></a>Требуются две конфигурации  
  
-   **Настройка для поддержки репликации для оптимизированных для памяти таблиц базы данных подписчика**  
  
     Задайте **@memory_optimized** Свойства **значение true,**, с помощью [sp_addsubscription &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md) или [sp_changesubscription &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-changesubscription-transact-sql.md).  
  
-   **Настройка статьи для поддержки репликации для таблицы, оптимизированные для памяти**  
  
     Задать `@schema_option = 0x40000000000` параметра для статьи с помощью [sp_addarticle &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md) или [sp_changearticle &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md).  
  
#### <a name="to-configure-a-memory-optimized-table-as-a-subscriber"></a>Настройка оптимизированной для памяти таблицы в качестве подписчика  
  
1.  Создайте публикацию транзакций. Дополнительные сведения см. в разделе [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md).  
  
2.  Добавьте статьи к публикации. Дополнительные сведения см. в статье [Define an Article](../../relational-databases/replication/publish/define-an-article.md).  
  
     Если настройка с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)] значение **@schema_option** параметр **sp_addarticle** хранимой процедуры   
    **0x40000000000**.  
  
3.  В окне свойств статьи задайте для параметра **Enable Memory optimization** (Включить оптимизацию памяти) значение **true**.  
  
4.  Запустите задание агента моментальных снимков, чтобы создать исходный моментальный снимок для этой публикации. Дополнительные сведения см. в разделе [Create and Apply the Initial Snapshot](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md).  
  
5.  Теперь создайте новую подписку. В **мастере создания подписки** задайте для параметра **Memory Optimized Subscription** (Оптимизированная для памяти подписка) значение **true**.  
  
 После этого оптимизированные для памяти таблицы должны начать получать обновления от издателя.  
  
#### <a name="reconfigure-an-existing-transaction-replication"></a>Перенастройка существующей репликации транзакций  
  
1.  Перейдите к свойствам подписки в [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] и задайте для параметра **Memory Optimized Subscription** (Оптимизированная для памяти подписка) значение **true**. Изменения будут применены после повторной инициализации подписки.  
  
     Если настройка с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)] Укажите новый **@memory_optimized** параметр **sp_addsubscription** хранимой процедуры значение true.  
  
2.  Перейдите к свойствам статьи для публикации в [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] и задайте для параметра **Enable Memory optimization** (Включить оптимизацию памяти) значение true.  
  
     Если настройка с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)] значение **@schema_option** параметр **sp_addarticle** хранимой процедуры   
    **0x40000000000**.  
  
3.  Оптимизированные для памяти таблицы не поддерживают кластеризованные индексы. Чтобы операция репликации обрабатывала их путем преобразования в некластеризованные индексы в целевом расположении, задайте для параметра **Convert clustered index to nonclustered for memory optimized article** (Преобразовывать кластеризованный индекс в некластеризованный для статьи, оптимизированной для памяти) значение true.  
  
     Если настройка с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)] значение **@schema_option** параметр **sp_addarticle** хранимой процедуры  **0x0000080000000000**.  
  
4.  Повторно создайте моментальный снимок.  
  
5.  Повторно инициализируйте подписку.  
  
## <a name="remarks-and-restrictions"></a>Комментарии и ограничения  
 Поддерживается только односторонняя репликация транзакций. Одноранговая репликация транзакций не поддерживается.  
  
 Оптимизированные для памяти таблицы нельзя публиковать.  
  
 Таблицы репликации на распространителе нельзя настраивать в качестве оптимизированных для памяти таблиц.  
  
 Репликация слиянием не может содержать оптимизированные для памяти таблицы.  
  
 Таблицы, участвующие в репликации транзакций можно настроить на подписчике как оптимизированные для памяти таблицы, но таблицы подписчика должны соответствовать требованиям к оптимизированным для памяти таблицам. Для этого необходимы следующие ограничения.  
 
-   В таблицах, которые реплицируются в оптимизированные для памяти таблицы на подписчике, можно использовать только типы данных, разрешенные в оптимизированных для памяти таблицах. Дополнительные сведения см. в статье [Поддерживаемые типы данных для выполняющейся в памяти OLTP](../../relational-databases/in-memory-oltp/supported-data-types-for-in-memory-oltp.md).  
  
-   Не все функции Transact-SQL поддерживаются с таблицами, оптимизированными для памяти. В разделе [Transact-SQL создает поддерживаемые OLTP в памяти](../../relational-databases/in-memory-oltp/transact-sql-constructs-not-supported-by-in-memory-oltp.md) Подробные сведения.  
  
##  <a name="a-nameschemaa-modifying-a-schema-file"></a><a name="Schema"></a> Изменение файла схемы  
  
-   Если используется параметр `DURABILITY = SCHEMA_AND_DATA` оптимизированной для памяти таблицы, то таблица должна иметь некластеризованный индекс первичного ключа.  
  
-   Параметр ANSI_PADDING должен быть установлен в значение ON.  
  
## <a name="see-also"></a>См. также:  
 [Функции и задачи репликации](../../relational-databases/replication/replication-features-and-tasks.md)  
  
  