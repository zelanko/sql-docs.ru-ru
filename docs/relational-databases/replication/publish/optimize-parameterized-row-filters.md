---
title: "Оптимизация параметризованных фильтров строк | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- precomputed partitions [SQL Server replication]
- filters [SQL Server replication], parameterized
- merge replication precomputed partitions [SQL Server replication], SQL Server Management Studio
- parameterized filters [SQL Server replication], optimizing
ms.assetid: 49349605-ebd0-4757-95be-c0447f30ba13
caps.latest.revision: 44
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 891399921dc50cc1a5463f9735462c94ce442df4
ms.contentlocale: ru-ru
ms.lasthandoff: 04/11/2017

---
# <a name="optimize-parameterized-row-filters"></a>Оптимизация параметризованных фильтров строк
  В этом разделе описывается оптимизация параметризованных фильтров строк в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы выполните следующие действия.**  
  
     [Рекомендации](#Recommendations)  
  
-   **Для оптимизации параметризованных фильтров строк используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Recommendations"></a> Рекомендации  
  
-   При использовании параметризованных фильтров можно управлять обработкой фильтрами репликацией слиянием, если указать параметр **use partition groups** или **keep partition changes** при создании публикации. Эти параметры повышают производительность синхронизации для публикаций с отфильтрованными статьями, сохраняя дополнительные метаданные в базе данных публикации. Можно управлять совместным использованием данных подписчиками, настроив параметр **partition options** при создании статьи. Дополнительные сведения об этих требованиях см. в разделе [параметризованные фильтры строк](../../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md).  
  
     При работе с подписчиками [!INCLUDE[ssEW](../../../includes/ssew-md.md)]SQL Server Compact параметр keep_partition_changes необходимо установить в значение true, чтобы обеспечить правильное распределение удалений. При установке значения false подписчик может получить больше строк, чем ожидается.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 Для оптимизации параметризованных фильтров строк можно воспользоваться следующими настройками:  
  
 **Partition Options**  
 Установите этот параметр на странице **Свойства** диалогового окна **Свойства статьи — \<статья>** или в диалоговом окне **Добавление фильтра**. Оба диалоговых окна доступны в мастере создания публикаций и в диалоговом окне **Свойства публикации — \<публикация>**. В диалоговом окне **Свойства статьи — \<статья>** можно указать дополнительные значения этого параметра, которые недоступны в диалоговом окне **Добавление фильтра**.  
  
 **Предварительное вычисление секций**  
 Если статьи публикации соблюдают ряд требований, то этот параметр по умолчанию имеет значение **True** . Дополнительные сведения об этих требованиях см. в статье [Оптимизация производительности параметризованного фильтра с помощью предварительно вычисляемых секций](../../../relational-databases/replication/merge/parameterized-filters-optimize-for-precomputed-partitions.md). Измените этот параметр на странице **Параметры подписки** диалогового окна **Свойства публикации — \<публикация>**.  
  
 **Оптимизировать синхронизацию**  
 Этот параметр должен иметь значение **True** только в том случае, если значение параметра **Предварительное вычисление секций** установлено равным **False**. Установите этот параметр на странице **Параметры подписки** диалогового окна **Свойства публикации — \<публикация>**.  
  
 Дополнительные сведения об использовании мастера создания публикаций и доступе к диалоговому окну **Свойства публикации — \<публикация>** см. в статьях [Создание публикации](../../../relational-databases/replication/publish/create-a-publication.md) и [Просмотр и изменение свойств публикации](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
#### <a name="to-set-partition-options-in-the-add-filter-or-edit-filter-dialog-box"></a>Задание настройки «Параметры секционирования» в диалоговом окне «Добавить фильтр» или «Редактировать фильтр»  
  
1.  На странице **Фильтрация строк таблицы** мастера создания публикаций или на странице **Фильтрация строк** диалогового окна **Свойства публикации — \<публикация>** щелкните **Добавить**, а затем **Добавить фильтр**.  
  
2.  Создайте параметризованный фильтр. Дополнительные сведения см. в статье [Определение и изменение параметризованного фильтра строк для статьи публикации слиянием](../../../relational-databases/replication/publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md).  
  
3.  Выберите параметр, который соответствует способу совместного использования данных подписчиками:  
  
    -   **Строка из этой таблицы будет отправлена нескольким подпискам**  
  
    -   **Строка из этой таблицы будет отправлена только одной подписке**  
  
     Если выбрана настройка **Строка из этой таблицы будет отправлена только одной подписке**, производительность репликации слиянием будет оптимизирована путем уменьшения объема хранимых и обрабатываемых метаданных. Однако следует убедиться, что данные секционированы таким образом, что одна строка не может быть реплицирована более чем одному подписчику. Дополнительные сведения см. в подразделе «Настройка параметров секционирования» раздела [параметризованные фильтры строк](../../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md).  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  Если вы находитесь в диалоговом окне **Свойства публикации — \<публикация>**, нажмите кнопку **ОК**, чтобы сохранить изменения и закрыть диалоговое окно.  
  
#### <a name="to-set-partition-options-in-the-article-properties---article-dialog-box"></a>Настройка параметров секционирования в диалоговом окне "Свойства статьи — \<статья>"  
  
1.  На странице **Статьи** мастера создания публикаций или в диалоговом окне **Свойства публикации — \<публикация>** выберите таблицу и щелкните **Свойства статьи**.  
  
2.  Щелкните **Указать свойства выделенной статьи таблицы** или **Указать свойства всех статей таблиц**.  
  
3.  В разделе **Целевой объект** вкладки **Свойства** диалогового окна **Свойства статьи — \<статья>** укажите одно из следующих значений в подразделе **Параметры секции**:  
  
    -   **Перекрывающиеся**  
  
    -   **Перекрывающиеся, с запретом на изменение данных вне секции**  
  
    -   **Неперекрывающаяся, одиночная подписка**  
  
    -   **Неперекрывающиеся, общие для нескольких подписок**  
  
     Дополнительные сведения об этих параметрах и о том, как они связаны с параметрами, доступными в диалоговых окнах **Добавление фильтра** и **Изменение фильтра** , см. в подразделе «Установка параметров секционирования» раздела [параметризованные фильтры строк](../../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md).  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  Если вы находитесь в диалоговом окне **Свойства публикации — \<публикация>**, нажмите кнопку **ОК**, чтобы сохранить изменения и закрыть диалоговое окно.  
  
#### <a name="to-set-precompute-partitions"></a>Задание настройки «Предварительное вычисление секций»  
  
1.  На странице **Параметры подписки** диалогового окна **Свойства публикации — \<публикация>** установите значение параметра **Предварительное вычисление секций**. Это свойство доступно только для чтения если:  
  
    -   Публикация не отвечает требованиям, предъявляемым к предварительно вычисляемым секциям.  
  
    -   Для данной публикации еще не был создан моментальный снимок. В этом случае для данного параметра отображается значение **Устанавливается автоматически при создании моментального снимка**.  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### <a name="to-set-optimize-synchronization"></a>Задание настройки «Оптимизировать синхронизацию»  
  
1.  На странице **Параметры подписки** диалогового окна **Свойства публикации — \<публикация>** установите значение **True** для параметра **Оптимизировать синхронизацию**.  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 Определения параметров фильтрации для параметров **@keep_partition_changes** и **@use_partition_groups**см. в разделе [sp_addmergepublication](../../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md).  
  
#### <a name="to-specify-merge-filter-optimizations-when-creating-a-new-publication"></a>Указание оптимизации фильтра слияния при создании публикации  
  
1.  На издателе в базе данных публикации выполните процедуру [sp_addmergepublication](../../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md). Укажите параметр **@publication** и значение **true** для одного из следующих параметров.  
  
    -   **@use_partition_groups**— оптимизация для наивысшей производительности при условии, что статьи соответствуют требованиям предварительно вычисляемых секций. Дополнительные сведения см. в статье [Оптимизация производительности параметризованного фильтра с помощью предварительно вычисляемых секций](../../../relational-databases/replication/merge/parameterized-filters-optimize-for-precomputed-partitions.md).  
  
    -   **@keep_partition_changes** — применяется, если невозможно использовать предварительно вычисляемые секции.  
  
2.  Добавьте задание моментального снимка для публикации. Дополнительные сведения см. в статье [о создании публикации](../../../relational-databases/replication/publish/create-a-publication.md).  
  
3.  На издателе в базе данных публикации выполните хранимую процедуру [sp_addmergearticle](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md), указав следующие параметры:  
  
    -   **@publication** — имя публикации из шага 1;  
  
    -   **@article** — имя статьи;  
  
    -   **@source_object** — публикуемый объект базы данных;  
  
    -   **@subset_filterclause** — необязательное предложение параметризованного фильтра, которое используется для горизонтальной фильтрации статьи;  
  
    -   **@partition_options** — параметры секционирования для фильтруемой статьи.  
  
4.  Повторите шаг 3 для каждой статьи в публикации.  
  
5.  Чтобы определить фильтр соединения между двумя статьями, на издателе в базе данных публикации выполните процедуру [sp_addmergefilter](../../../relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql.md) (необязательно). Дополнительные сведения см. в разделе [Определение и изменение фильтра соединения между статьями публикации слиянием](../../../relational-databases/replication/publish/define-and-modify-a-join-filter-between-merge-articles.md).  
  
#### <a name="to-view-and-modify-merge-filter-behaviors-for-an-existing-publication"></a>Просмотр и изменение поведения фильтра слияния для существующей публикации  
  
1.  Чтобы определить фильтр соединения между двумя статьями, на издателе в базе данных публикации выполните процедуру [sp_helpmergepublication](../../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md), указав параметр **@publication**. Запомните значения **keep_partition_changes** и **use_partition_groups** в результирующем наборе.  
  
2.  На издателе в базе данных публикации выполните процедуру [sp_changemergepublication](../../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md)(необязательно). Укажите значение **use_partition_groups** в параметре **@property** и **true** или **false** в параметре **@value**.  
  
3.  На издателе в базе данных публикации выполните процедуру [sp_changemergepublication](../../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md)(необязательно). Укажите значение **keep_partition_changes** в параметре **@property** и **true** или **false** в параметре **@value**.  
  
    > [!NOTE]  
    >  При включении параметра **keep_partition_changes**необходимо вначале отключить параметр **use_partition_groups** и указать значение **1** в параметре **@force_reinit_subscription**.  
  
4.  На издателе в базе данных публикации выполните хранимую процедуру [sp_changemergearticle](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md)(необязательно). Укажите значение **partition_options** в параметре **@property** и соответствующее значение в параметре **@value**. Определения этих параметров фильтрации см. в разделе [sp_addmergearticle](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md) .  
  
5.  При необходимости запустите агент моментальных снимков для повторного создания моментального снимка (необязательно). Сведения об изменениях, после которых необходимо повторно создавать моментальный снимок, см. в статье [Изменение свойств публикации и статьи](../../../relational-databases/replication/publish/change-publication-and-article-properties.md).  
  
## <a name="see-also"></a>См. также:  
 [Automatically Generate Join Filters Between Merge Articles](../../../relational-databases/replication/publish/automatically-generate-join-filters-between-merge-articles.md)  (Автоматическое создание фильтров соединения между статьями публикации слиянием)  
 [Определение и изменение параметризованного фильтра строк для статьи публикации слиянием](../../../relational-databases/replication/publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)   
 [Параметризованные фильтры строк](../../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md)  
  
  
