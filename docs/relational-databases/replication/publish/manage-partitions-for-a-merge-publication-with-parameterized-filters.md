---
title: "Управление секциями для публикации слиянием с параметризованными фильтрами | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "секции [репликация SQL Server]"
  - "секции при репликации слиянием [репликация SQL Server], среда SQL Server Management Studio"
  - "параметризованные фильтры [репликация SQL Server], управление секциями"
ms.assetid: fb5566fe-58c5-48f7-8464-814ea78e6221
caps.latest.revision: 22
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 22
---
# Управление секциями для публикации слиянием с параметризованными фильтрами
  В данном разделе описывается управление секциями для публикации слиянием с параметризованными фильтрами в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)] или объектов RMO. Параметризованные фильтры строк могут быть использованы для формирования неперекрывающихся секций. Такие секции могут быть ограничены таким образом, чтобы каждая данная секция предоставлялась только одной подписке. В таком случае, чем больше число подписчиков, тем большее число секций потребуется, а это, в свою очередь, приведет к необходимости создания такого же числа секционированных моментальных снимков. Дополнительные сведения см. в статье [Parameterized Row Filters](../../../relational-databases/replication/merge/parameterized-row-filters.md).  
  
 **В этом разделе**  
  
-   **Перед началом работы выполните следующие действия.**  
  
     [Рекомендации](#Recommendations)  
  
-   **Для управления секциями для публикации слиянием с параметризованными фильтрами используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [объекты RMO;](#RMOProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Recommendations"></a> Рекомендации  
  
-   Если в соответствии с рекомендациями создается скрипт топологии репликации, скрипты публикации содержат вызовы хранимых процедур для создания секций данных. Скрипт содержит справочную информацию для созданных секций и способ воссоздания одной или нескольких секций в случае необходимости. Дополнительные сведения см. в статье [Scripting Replication](../../../relational-databases/replication/scripting-replication.md).  
  
-   Если публикация имеет параметризованные фильтры, позволяющие получать подписки с неперекрывающимися секциями, то при необходимости повторного создания подписки в случае ее утраты необходимо удалить секцию, которая была на нее подписана, создать заново подписку, а затем повторно создать секцию. Дополнительные сведения см. в статье [Parameterized Row Filters](../../../relational-databases/replication/merge/parameterized-row-filters.md). При формировании скрипта публикации репликация формирует скрипты создания для существующих секций подписчика. Дополнительные сведения см. в статье [Scripting Replication](../../../relational-databases/replication/scripting-replication.md).  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 Управление секциями осуществляется на **секции данных** Страница **Свойства публикации — \< публикация>** диалоговое окно. Дополнительные сведения о доступе к этому диалоговому окну см. в разделе [View and Modify Publication Properties](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md). На этой странице доступны следующие возможности: создание и удаление секций, разрешение подписчикам выполнять создание и доставку моментального снимка, создание моментальных снимков для одной или нескольких секций, очистка моментальных снимков.  
  
#### Создание секции  
  
1.  На **секции данных** Страница **Свойства публикации — \< публикация>** диалоговом нажмите кнопку **Добавить**.  
  
2.  В **Добавление секции данных** диалогового окна введите значение для **HOST_NAME()** или **SUSER_SNAME()** значение, связанное с секцией, необходимо создать.  
  
3.  При необходимости задайте расписание обновления моментальных снимков.  
  
    1.  Выберите **Расписание агента моментальных снимков для этой секции в следующее время выполнения**  
  
    2.  Примите используемое по умолчанию расписание обновления моментальных снимков или щелкните **Изменить** , чтобы указать другое расписание.  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### Удаление секции  
  
1.  На странице **Секции данных** выберите секцию в сетке.  
  
2.  Щелкните **Удалить**.  
  
#### Разрешение подписчикам запускать создание и доставку моментальных снимков  
  
1.  На странице **Секции данных** выберите **Автоматически определять секцию и, при необходимости, создавать моментальный снимок при попытке синхронизации от нового подписчика**.  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### Создание моментального снимка секции  
  
1.  На странице **Секции данных** выберите секцию в сетке.  
  
2.  Щелкните **Создать выбранные моментальные снимки**.  
  
#### Очистка моментального снимка секции  
  
1.  На странице **Секции данных** выберите секцию в сетке.  
  
2.  Щелкните **Очистить существующие моментальные снимки**.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 Программный перебор существующих секций с помощью хранимых процедур репликации позволяет повысить управляемость публикаций с параметризованными фильтрами. Кроме того, секции можно создавать и удалять. Для существующей секции доступны следующие сведения.  
  
-   Способ фильтрации секции (с помощью [SUSER_SNAME & #40; Transact-SQL & #41;](../../../t-sql/functions/suser-sname-transact-sql.md) или [HOST_NAME & #40; Transact-SQL & #41;](../../../t-sql/functions/host-name-transact-sql.md)).  
  
-   Имя задания, которым формируется секционированный моментальный снимок.  
  
-   Время последнего запуска задания секционированного снимка.  
  
 Если вторая часть снимка, состоящего из двух частей, может быть сформирована по запросу в момент инициализации новой подписки, то приведенные ниже процедуры позволят выполнить предварительное формирование снимка в подходящее время и управлять его формированием. Дополнительные сведения см. в статье [Snapshots for Merge Publications with Parameterized Filters](../../../relational-databases/replication/snapshots-for-merge-publications-with-parameterized-filters.md).  
  
#### Просмотр информации о существующих секциях  
  
1.  На издателе в базе данных публикации выполните хранимую процедуру [sp_helpmergepartition & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-helpmergepartition-transact-sql.md). Укажите имя публикации в параметре **@publication**. (Необязательно) Укажите **@suser_sname** или **@host_name** Возврат данных на основе одного критерия фильтрации.  
  
#### Определение новой секции и формирование нового секционированного снимка  
  
1.  На издателе в базе данных публикации выполните хранимую процедуру [sp_addmergepartition & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addmergepartition-transact-sql.md). Укажите в параметре **@publication**имя публикации, а также параметризованное значение определения секции в одном из следующих параметров:  
  
    -   **@suser_sname** — если параметризованный фильтр определяется значение, возвращаемое [SUSER_SNAME & #40; Transact-SQL & #41;](../../../t-sql/functions/suser-sname-transact-sql.md).  
  
    -   **@host_name** — если параметризованный фильтр определяется значение, возвращаемое [HOST_NAME & #40; Transact-SQL & #41;](../../../t-sql/functions/host-name-transact-sql.md).  
  
2.  Создайте и инициализируйте параметризованный снимок для новой секции. Дополнительные сведения см. в статье [Create a Snapshot for a Merge Publication with Parameterized Filters](../../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md).  
  
#### Удаление секции  
  
1.  На издателе в базе данных публикации выполните хранимую процедуру [sp_dropmergepartition & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-dropmergepartition-transact-sql.md). Укажите в параметре **@publication** имя публикации, а также параметризованное значение определения секции в одном из следующих параметров:  
  
    -   **@suser_sname** — если параметризованный фильтр определяется значение, возвращаемое [SUSER_SNAME & #40; Transact-SQL & #41;](../../../t-sql/functions/suser-sname-transact-sql.md).  
  
    -   **@host_name** — если параметризованный фильтр определяется значение, возвращаемое [HOST_NAME & #40; Transact-SQL & #41;](../../../t-sql/functions/host-name-transact-sql.md).  
  
     При этом также будет удалено задание моментального снимка и все файлы снимка для этой секции.  
  
##  <a name="RMOProcedure"></a> При помощи объектов RMO  
 Программное формирование новых, перебор существующих и удаление секций подписчика с помощью объектов RMO обеспечивает большую управляемость публикации с параметризованными фильтрами. Сведения о создании секций подписчика см. в разделе [Create a Snapshot for a Merge Publication with Parameterized Filters](../../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md). Для существующей секции доступны следующие сведения.  
  
-   Значение и функция фильтрации, на которых базируется секция.  
  
-   Имя задания, формирующего параметризованный снимок для подписчика.  
  
-   Время последнего выполнения задания параметризованного моментального снимка.  
  
#### Просмотр информации о существующих секциях  
  
1.  Создайте соединение с издателем с помощью <xref:Microsoft.SqlServer.Management.Common.ServerConnection> класса.  
  
2.  Создайте экземпляр <xref:Microsoft.SqlServer.Replication.MergePublication> класса. Задайте <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> и <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> Свойства для публикации, а также набор <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> Свойства <xref:Microsoft.SqlServer.Management.Common.ServerConnection> созданной на шаге 1.  
  
3.  Вызов <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> метод, чтобы получить свойства объекта. Если этот метод возвращает **false**, то либо на шаге 2 были неверно определены свойства публикации, либо публикация не существует.  
  
4.  Вызов <xref:Microsoft.SqlServer.Replication.MergePublication.EnumMergePartitions%2A> метода и передать результат в массив <xref:Microsoft.SqlServer.Replication.MergePartition> объектов.  
  
5.  Для каждого <xref:Microsoft.SqlServer.Replication.MergePartition> объекта в массиве, получить любые интересующие свойства.  
  
#### Удаление существующих секций  
  
1.  Создайте соединение с издателем с помощью <xref:Microsoft.SqlServer.Management.Common.ServerConnection> класса.  
  
2.  Создайте экземпляр <xref:Microsoft.SqlServer.Replication.MergePublication> класса. Задайте <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> и <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> Свойства для публикации, а также набор <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> Свойства <xref:Microsoft.SqlServer.Management.Common.ServerConnection> созданной на шаге 1.  
  
3.  Вызов <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> метод, чтобы получить свойства объекта. Если этот метод возвращает **false**, то либо на шаге 2 были неверно определены свойства публикации, либо публикация не существует.  
  
4.  Вызов <xref:Microsoft.SqlServer.Replication.MergePublication.EnumMergePartitions%2A> метода и передать результат в массив <xref:Microsoft.SqlServer.Replication.MergePartition> объектов.  
  
5.  Для каждого <xref:Microsoft.SqlServer.Replication.MergePartition> объекта в массиве, определить, следует ли удалять секции. Обычно это решение основано на значение <xref:Microsoft.SqlServer.Replication.MergePartition.DynamicFilterLogin%2A> свойство или <xref:Microsoft.SqlServer.Replication.MergePartition.DynamicFilterHostName%2A> свойство.  
  
6.  Вызов <xref:Microsoft.SqlServer.Replication.MergePublication.RemoveMergePartition%2A> метод <xref:Microsoft.SqlServer.Replication.MergePublication> из шага 2. Передайте <xref:Microsoft.SqlServer.Replication.MergePartition> из шага 5.  
  
7.  Повторите шаг 6 для каждой удаляемой секции.  
  
## См. также:  
 [Параметризованные фильтры строк](../../../relational-databases/replication/merge/parameterized-row-filters.md)   
 [Моментальные снимки для публикаций слиянием с параметризованными фильтрами](../../../relational-databases/replication/snapshots-for-merge-publications-with-parameterized-filters.md)  
  
  