---
title: Определение и изменение параметризованного фильтра строк (слияние)
description: Узнайте, как определить и изменить параметризованный фильтр строк для статьи публикации слиянием для SQL Server.
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- parameterized filters [SQL Server replication], defining
- parameterized filters [SQL Server replication], modifying
- merge replication [SQL Server replication], dynamic filters
- merge replication parameterized filters [SQL Server replication]
- filters [SQL Server replication], parameterized
- modifying filters, parameterized row
- dynamic filters [SQL Server replication]
ms.assetid: de0482a2-3cc8-4030-8a4a-14364549ac9f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 64e7dc7e271b50b5dc23b97be81b420df2176fdd
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85882078"
---
# <a name="define-and-modify-a-parameterized-row-filter-for-a-merge-article"></a>Определение и изменение параметризованного фильтра строк для статьи публикации слиянием
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  В этом разделе описывается определение и изменение параметризованного фильтра строк в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] при помощи среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
 При создании статей таблицы можно применять параметризованные фильтры строк. Эти фильтры используют предложение [WHERE](../../../t-sql/queries/where-transact-sql.md) , чтобы выбрать необходимые данные для публикации. Вместо того чтобы задавать буквенное значение в предложении (так, как в случае статического фильтра строк), вы указываете одну или обе следующие системные функции: [SUSER_SNAME](../../../t-sql/functions/suser-sname-transact-sql.md) и [HOST_NAME](../../../t-sql/functions/host-name-transact-sql.md). Дополнительные сведения см. в разделе [Параметризованные фильтры строк](../../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md).  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
-   **Для определения и изменения параметризованного фильтра строк используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Ограничения  
  
-   Если добавление, изменение или удаление параметризованного фильтра строк выполняется после инициализации подписок на публикацию, следует создать новый моментальный снимок и повторно инициализировать все подписки после внесения изменений. Дополнительные сведения о требованиях к изменениям свойств см. в статье [Изменение свойств публикации и статьи](../../../relational-databases/replication/publish/change-publication-and-article-properties.md).  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> Рекомендации  
  
-   Для обеспечения высокой производительности не рекомендуется применять функции к именам столбцов в выражениях параметризованных фильтров строк, таких как `LEFT([MyColumn]) = SUSER_SNAME()`. Если в предложении фильтра используется HOST_NAME и переопределяется значение HOST_NAME, может быть, необходимо выполнить преобразование типов данных при помощи инструкции CONVERT. Дополнительные сведения см. в подразделе «Переопределение значения HOST_NAME()» раздела [Parameterized Row Filters](../../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md).  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 Операции определения, изменения и удаления параметризованных фильтров строк выполняются на странице **Фильтрация строк таблицы** мастера создания публикаций или на странице **Фильтрация строк** диалогового окна **Свойства публикации — \<Publication>** . Дополнительные сведения об использовании мастера и доступе к этому диалоговому окну см. в статьях [Создание публикации](../../../relational-databases/replication/publish/create-a-publication.md) и [Просмотр и изменение свойств публикации](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
#### <a name="to-define-a-parameterized-row-filter"></a>Определение параметризованного фильтра строк  
  
1.  На странице **Фильтрация строк таблицы** мастера создания публикаций или на странице **Фильтрация строк** диалогового окна **Свойства публикации — \<Publication>** нажмите кнопку **Добавить**, а затем — **Добавить фильтр**.  
  
2.  В окне **Добавление фильтра** выберите в раскрывающемся списке таблицу для фильтрации.  
  
3.  Создайте инструкцию фильтра в текстовом поле **Инструкция фильтра** . Можно ввести текст в тестовом поле или перетащить столбцы из списка **Столбцы** .  
  
    -   Текстовая область **Инструкция фильтра** содержит текст по умолчанию, в виде:  
  
        ```  
        SELECT <published_columns> FROM [tableowner].[tablename] WHERE  
        ```  
  
    -   Текст по умолчанию изменять нельзя. Введите предложение фильтра после ключевого слова WHERE, используя стандартный синтаксис SQL. Параметризованный фильтр включает вызов функции системы **HOST_NAME()** и/или **SUSER_SNAME()** либо пользовательской функции, которая ссылается на одну или обе эти функции. Ниже приведен пример полного выражения для параметризованного фильтра строк:  
  
        ```  
        SELECT <published_columns> FROM [HumanResources].[Employee] WHERE LoginID = SUSER_SNAME()  
        ```  
  
         В предложении WHERE необходимо использовать имена, состоящие из двух частей; имена, состоящие из трех или четырех частей, не поддерживаются.  
  
4.  Выберите параметр, который соответствует способу совместного использования данных подписчиками:  
  
    -   **Строка из этой таблицы будет отправлена нескольким подпискам**  
  
    -   **Строка из этой таблицы будет отправлена только одной подписке**  
  
     Если выбрана настройка **Строка из этой таблицы будет отправлена только одной подписке**, производительность репликации слиянием будет оптимизирована путем уменьшения объема хранимых и обрабатываемых метаданных. Однако следует убедиться, что данные секционированы таким образом, что одна строка не может быть реплицирована более чем одному подписчику. Дополнительные сведения см. в подразделе «Настройка параметров секционирования» раздела [Параметризованные фильтры строк](../../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md).  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
6.  Если вы находитесь в диалоговом окне **Свойства публикации — \<Publication>** , нажмите кнопку **OK**, чтобы сохранить результаты и закрыть диалоговое окно.  
  
#### <a name="to-modify-a-parameterized-row-filter"></a>Изменение параметризованного фильтра строк  
  
1.  На странице **Фильтрация строк таблицы** мастера создания публикаций или странице **Фильтрация строк** диалогового окна **Свойства публикации — \<Publication>** выберите фильтр в области **Отфильтрованные таблицы**, а затем нажмите кнопку **Правка**.  
  
2.  В окне **Изменение фильтра** измените фильтр.  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### <a name="to-delete-a-parameterized-row-filter"></a>Удаление параметризованного фильтра строк  
  
1.  На странице **Фильтрация строк таблицы** мастера создания публикаций или странице **Фильтрация строк** диалогового окна **Свойства публикации — \<Publication>** выберите фильтр в области **Отфильтрованные таблицы**, а затем нажмите кнопку **Удалить**.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
 Параметризованные фильтры строк можно создавать и изменять программно с помощью хранимых процедур репликации.  
  
#### <a name="to-define-a-parameterized-row-filter-for-an-article-in-a-merge-publication"></a>Определение параметризованного фильтра строк для статьи в публикации слиянием  
  
1.  В базе данных публикации на издателе выполните процедуру [sp_addmergearticle (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md). Укажите параметр **\@publication**, имя статьи в параметре **\@article**, публикуемую таблицу в параметре **\@source_object**, предложение WHERE, определяющее параметризованный фильтр в параметре **\@subset_filterclause** (исключая `WHERE`), и одно из следующих значений в параметре **\@partition_options**, описывающее тип секционирования, которое будет получено в результате применения параметризованного фильтра строк.  
  
    -   **0** — фильтрация для данной статьи либо является статической, либо не возвращает уникального подмножества данных для каждой из секций (то есть имеются перекрывающиеся секции).  
  
    -   **1** — результирующие секции перекрываются, и произведенные на подписчике изменения не могут быть внесены в секцию, которой принадлежит строка.  
  
    -   **2** — фильтрация для статьи дает неперекрывающиеся секции, но несколько подписчиков могут получить одну и ту же секцию.  
  
    -   **3** — фильтрация для статьи дает неперекрывающиеся секции, уникальные для каждой из подписок.  
  
#### <a name="to-change-a-parameterized-row-filter-for-an-article-in-a-merge-publication"></a>Изменение параметризованного фильтра строк для статьи в публикации слиянием  
  
1.  В базе данных публикации на издателе выполните процедуру [sp_changemergearticle](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md). Укажите параметр **\@publication**, **\@article**, значение **subset_filterclause** в параметре **\@property**, выражение, определяющее параметризованный фильтр в параметре **\@value** (исключая `WHERE`), и значение **1** в параметре как в параметре **\@force_invalidate_snapshot**, так и в параметре **\@force_reinit_subscription**.  
  
2.  Если это изменение приведет к разному поведению секционирования, еще раз выполните хранимую процедуру [sp_changemergearticle](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md) . Укажите параметры **\@publication**, **\@article**, значение **partition_options** в параметре **\@property** и наиболее оптимальный параметр секционирования в параметре **\@value**, например один из следующих:  
  
    -   **0** — фильтрация для данной статьи либо является статической, либо не возвращает уникального подмножества данных для каждой из секций (то есть имеются перекрывающиеся секции).  
  
    -   **1** — результирующие секции перекрываются, и произведенные на подписчике изменения не могут быть внесены в секцию, которой принадлежит строка.  
  
    -   **2** — фильтрация для статьи дает неперекрывающиеся секции, но несколько подписчиков могут получить одну и ту же секцию.  
  
    -   **3** — фильтрация для статьи дает неперекрывающиеся секции, уникальные для каждой из подписок.  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> Примеры (Transact-SQL)  
 В этом примере определяется группа статей в публикации слиянием. К статьям применяется последовательность фильтров соединения для таблицы `Employee` , которая в свою очередь фильтруется по столбцу **LoginID** с помощью параметризованного фильтра строк. Во время синхронизации переопределяется значение, возвращаемое функцией [HOST_NAME](../../../t-sql/functions/host-name-transact-sql.md) . Дополнительные сведения см. в подразделе «Переопределение значения функции HOST_NAME()» раздела [Parameterized Row Filters](../../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md).  
  
 [!code-sql[HowTo#sp_MergeDynamicPub1](../../../relational-databases/replication/codesnippet/tsql/define-and-modify-a-para_1.sql)]  
  
## <a name="see-also"></a>См. также:  
 [Определение и изменение фильтра соединения между статьями публикации слиянием](../../../relational-databases/replication/publish/define-and-modify-a-join-filter-between-merge-articles.md)   
 [Изменение свойств публикации и статьи](../../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [Join Filters](../../../relational-databases/replication/merge/join-filters.md)   
 [Параметризованные фильтры строк](../../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md)  
  
  
