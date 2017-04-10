---
title: "Указание сопоставления типов данных для издателя Oracle | Microsoft Docs"
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
  - "публикация Oracle [репликация SQL Server], сопоставление типов данных"
  - "типы данных [репликация SQL Server], публикация Oracle"
  - "сопоставление типов данных [репликация SQL Server]"
ms.assetid: f172d631-3b8c-4912-bd0f-568366cd9870
caps.latest.revision: 37
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 37
---
# Указание сопоставления типов данных для издателя Oracle
  В данном разделе описывается указание сопоставления типов данных для издателя Oracle в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../../includes/tsql-md.md)]. Хотя в списке для издателей Oracle имеется набор сопоставлений типов данных, для отдельных публикаций может потребоваться создание дополнительных сопоставлений.  
  
 **В этом разделе**  
  
-   **Для указания сопоставления типов данных для издателя Oracle используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 Указание сопоставления типов данных на **Сопоставление данных** вкладке **Свойства статьи — \< статья>** диалоговое окно. Его можно получить из **статьи** страницы мастера публикации и **Свойства публикации — \< публикация>** диалоговое окно. Дополнительные сведения об использовании мастера и о доступе к диалоговому окну см. в разделе [Создание публикации из базы данных Oracle](../../../relational-databases/replication/publish/create-a-publication-from-an-oracle-database.md) и [Просмотр и изменение свойств публикации](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
#### Указание сопоставления типов данных  
  
1.  На **статьи** страница мастера создания публикаций или **Свойства публикации — \< публикация>** диалоговое окно, выберите таблицу и нажмите кнопку **Свойства статьи**.  
  
2.  Щелкните **Указать свойства выделенной статьи таблицы**.  
  
3.  На **Сопоставление данных** вкладке **Свойства статьи — \< статья>** диалоговое окно, выберите сопоставления из **тип данных подписчика** столбца:  
  
    -   Для некоторых типов данных существует только одно возможное сопоставление, при этом столбец в сетке свойств доступен только для чтения.  
  
    -   Для некоторых типов данных можно осуществить выбор из нескольких типов. [!INCLUDE[msCoName](../../../includes/msconame-md.md)] рекомендует использовать сопоставление по умолчанию, если приложению не требуется другого сопоставления. Дополнительные сведения см. в статье [Data Type Mapping for Oracle Publishers](../../../relational-databases/replication/non-sql/data-type-mapping-for-oracle-publishers.md).  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 Пользовательские сопоставления типов данных могут быть заданы программно с помощью хранимых процедур репликации. Можно также задать сопоставления по умолчанию, которые используются, если типы данных сопоставления между [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и не[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] базами данных (СУБД). Дополнительные сведения см. в статье [Data Type Mapping for Oracle Publishers](../../../relational-databases/replication/non-sql/data-type-mapping-for-oracle-publishers.md).  
  
#### Определение пользовательского сопоставления данных при создании статьи, принадлежащей публикации Oracle  
  
1.  Если публикация Oracle не существует, ее необходимо создать.  
  
2.  На распространителе выполните хранимую процедуру [sp_addarticle](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md). Укажите значение **0** для **@use_default_datatypes**. Дополнительные сведения см. в статье [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
3.  На распространителе выполните хранимую процедуру [sp_helparticlecolumns](../../../relational-databases/system-stored-procedures/sp-helparticlecolumns-transact-sql.md) для просмотра существующего сопоставления для столбца в опубликованную статью.  
  
4.  На распространителе выполните хранимую процедуру [sp_changearticlecolumndatatype](../../../relational-databases/system-stored-procedures/sp-changearticlecolumndatatype-transact-sql.md). Чтобы определить опубликованный столбец, укажите имя издателя Oracle в параметре **@publisher**и задайте значения параметров **@publication**, **@article**и **@column** . Укажите имя типа данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , сопоставляемого с типом **@type**, и при необходимости задайте значения параметров **@length**, **@precision**и **@scale**.  
  
5.  На распространителе выполните хранимую процедуру [sp_articleview](../../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md). Она создаст представление, используемое для создания моментального снимка из публикации Oracle.  
  
#### Назначение для типа данных сопоставления по умолчанию  
  
1.  (Необязательно) На распространителе в любой базе данных, выполнение [sp_getdefaultdatatypemapping](../../../relational-databases/system-stored-procedures/sp-getdefaultdatatypemapping-transact-sql.md). Укажите **@source_dbms**, **@source_type**, **@destination_dbms**, **@destination_version**, и другие параметры, необходимые для определения исходной СУБД. Сведения о текущем сопоставлении типа данных в целевой базе данных возвращаются в выходных параметрах.  
  
2.  (Необязательно) На распространителе в любой базе данных, выполнение [sp_helpdatatypemap](../../../relational-databases/system-stored-procedures/sp-helpdatatypemap-transact-sql.md). Укажите **@source_dbms** и других параметров, необходимых для фильтрации результирующего набора. Обратите внимание на значение **mapping_id** сопоставления в результирующий набор.  
  
3.  На распространителе в любой базе данных, выполнение [sp_setdefaultdatatypemapping](../../../relational-databases/system-stored-procedures/sp-setdefaultdatatypemapping-transact-sql.md).  
  
    -   Если известно необходимое значение параметра **mapping_id** полученное на шаге 2, укажите его в параметре **@mapping_id**.  
  
    -   Если вы не знаете **mapping_id**, укажите параметры **@source_dbms**, **@source_type**, **@destination_dbms**, **@destination_type**, и другие параметры, необходимые для идентификации существующего сопоставления.  
  
#### Определение допустимых типов данных, соответствующих типу данных Oracle  
  
1.  На распространителе в любой базе данных, выполнение [sp_helpdatatypemap](../../../relational-databases/system-stored-procedures/sp-helpdatatypemap-transact-sql.md). Укажите значение **ORACLE** для **@source_dbms** и других параметров, необходимых для фильтрации результирующего набора.  
  
###  <a name="TsqlExample"></a> Примеры (Transact-SQL)  
 В этом примере изменяется столбец с типом данных Oracle, числа, оно сопоставляется с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] типа данных **числовых**(38,38) вместо типа данных по умолчанию **float**.  
  
 [!code-sql[HowTo#sp_changecolumndatatype](../../../relational-databases/replication/codesnippet/tsql/specify-data-type-mappin_1.sql)]  
  
 Следующий пример запроса возвращает два сопоставления для типа данных Oracle 9 **CHAR**: определенное по умолчанию и альтернативное.  
  
 [!code-sql[HowTo#sp_helpcolumndatatype_char](../../../relational-databases/replication/codesnippet/tsql/specify-data-type-mappin_2.sql)]  
  
 Следующий пример запроса возвращает сопоставления по умолчанию для типа данных Oracle 9 **NUMBER** , когда он указан без масштаба и точности.  
  
 [!code-sql[HowTo#sp_helpcolumndatatype_number](../../../relational-databases/replication/codesnippet/tsql/specify-data-type-mappin_3.sql)]  
  
## См. также:  
 [Сопоставление типов данных для издателей Oracle](../../../relational-databases/replication/non-sql/data-type-mapping-for-oracle-publishers.md)   
 [Разнородная репликация базы данных](../../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Основные понятия системных хранимых процедур репликации](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)   
 [Настройка издателя Oracle](../../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md)  
  
  