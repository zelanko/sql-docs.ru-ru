---
title: Указание сопоставления типов данных для издателя Oracle | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Oracle publishing [SQL Server replication], data type mapping
- data types [SQL Server replication], Oracle publishing
- mapping data types [SQL Server replication]
ms.assetid: f172d631-3b8c-4912-bd0f-568366cd9870
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 99e1d3377cb5ed4afd4577462e0b436bb16d2fee
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68941091"
---
# <a name="specify-data-type-mappings-for-an-oracle-publisher"></a>Указание сопоставления типов данных для издателя Oracle
  В данном разделе описывается указание сопоставления типов данных для издателя Oracle в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../../includes/tsql-md.md)]. Хотя в списке для издателей Oracle имеется набор сопоставлений типов данных, для отдельных публикаций может потребоваться создание дополнительных сопоставлений.  
  
 **В этом разделе**  
  
-   **Указание сопоставлений типов данных для издателя Oracle с помощью:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 Укажите сопоставления типов данных на вкладке **Сопоставление данных** диалогового окна **Свойства статьи — \<статья>**. Она доступно на странице **Статьи** мастера создания публикаций и в диалоговом окне **Свойства публикации — \<публикация>**. Дополнительные сведения об использовании мастера и доступе к этому диалоговому окну см. в статьях [Создание публикации из базы данных Oracle](create-a-publication-from-an-oracle-database.md) и [Просмотр и изменение свойств публикации](view-and-modify-publication-properties.md).  
  
#### <a name="to-specify-a-data-type-mapping"></a>Указание сопоставления типов данных  
  
1.  На странице **Статьи** мастера создания публикаций или в диалоговом окне **Свойства публикации — \<публикация>** выберите таблицу и щелкните **Свойства статьи**.  
  
2.  Щелкните **Указать свойства выделенной статьи таблицы**.  
  
3.  На вкладке **Сопоставление данных** диалогового окна **Свойства статьи — \<статья>** выберите сопоставления из столбца **Тип данных подписчика**:  
  
    -   Для некоторых типов данных существует только одно возможное сопоставление, при этом столбец в сетке свойств доступен только для чтения.  
  
    -   Для некоторых типов данных можно осуществить выбор из нескольких типов. 
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] рекомендует использовать сопоставление по умолчанию, если приложению не требуется другого сопоставления. Дополнительные сведения см. в статье [Data Type Mapping for Oracle Publishers](../non-sql/data-type-mapping-for-oracle-publishers.md).  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 Пользовательские сопоставления типов данных могут быть заданы программно с помощью хранимых процедур репликации. Можно также задать сопоставления по умолчанию, используемые при сопоставлении типов данных между [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и системой управления,[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] отличной от базы данных (СУБД). Дополнительные сведения см. в статье [Data Type Mapping for Oracle Publishers](../non-sql/data-type-mapping-for-oracle-publishers.md).  
  
#### <a name="to-define-custom-data-type-mappings-when-creating-an-article-belonging-to-an-oracle-publication"></a>Определение пользовательского сопоставления данных при создании статьи, принадлежащей публикации Oracle  
  
1.  Если публикация Oracle не существует, ее необходимо создать.  
  
2.  На распространителе выполните хранимую процедуру [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql). Укажите значение **0** в параметре **\@use_default_datatypes**. Дополнительные сведения см. в статье [определить статью](define-an-article.md).  
  
3.  Чтобы просмотреть существующие сопоставления для столбца в опубликованной статье, выполните хранимую процедуру [sp_helparticlecolumns](/sql/relational-databases/system-stored-procedures/sp-helparticlecolumns-transact-sql) .  
  
4.  На распространителе выполните хранимую процедуру [sp_changearticlecolumndatatype](/sql/relational-databases/system-stored-procedures/sp-changearticlecolumndatatype-transact-sql). Укажите имя издателя Oracle для ** \@издателя**, а также ** \@публикацию**, ** \@статью**и ** \@столбец** , чтобы определить опубликованный столбец. Укажите [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] имя типа данных, который будет сопоставляться для ** \@типа**, а также ** \@длину**, ** \@точность**и ** \@масштаб**, где это применимо.  
  
5.  На распространителе выполните хранимую процедуру [sp_articleview](/sql/relational-databases/system-stored-procedures/sp-articleview-transact-sql). Она создаст представление, используемое для создания моментального снимка из публикации Oracle.  
  
#### <a name="to-specify-a-mapping-as-the-default-mapping-for-a-data-type"></a>Назначение для типа данных сопоставления по умолчанию  
  
1.  (Необязательно) На распространителе в любой базе данных выполните хранимую процедуру [sp_getdefaultdatatypemapping](/sql/relational-databases/system-stored-procedures/sp-getdefaultdatatypemapping-transact-sql). Укажите ** \@source_dbms**, ** \@source_type**, ** \@destination_dbms**, ** \@destination_version**и другие параметры, необходимые для определения исходной СУБД. Сведения о текущем сопоставлении типа данных в целевой базе данных возвращаются в выходных параметрах.  
  
2.  На распространителе в любой базе данных выполните хранимую процедуру [sp_helpdatatypemap](/sql/relational-databases/system-stored-procedures/sp-helpdatatypemap-transact-sql)(необязательно). Укажите ** \@source_dbms** и другие параметры, необходимые для фильтрации результирующего набора. В результирующем наборе просмотрите значение параметра **mapping_id** для текущего сопоставления.  
  
3.  На распространителе в любой базе данных выполните хранимую процедуру [sp_setdefaultdatatypemapping](/sql/relational-databases/system-stored-procedures/sp-setdefaultdatatypemapping-transact-sql)(необязательно).  
  
    -   Если известно необходимое значение параметра **mapping_id**, полученное на шаге 2, укажите его в параметре **\@mapping_id**.  
  
    -   Если значение **mapping_id** неизвестно, необходимо указать значения параметров **\@source_dbms**, **\@source_type**, **\@destination_dbms**, **\@destination_type** и других параметров, необходимых для идентификации существующего сопоставления.  
  
#### <a name="to-find-valid-data-types-for-a-given-oracle-data-type"></a>Определение допустимых типов данных, соответствующих типу данных Oracle  
  
1.  На распространителе в любой базе данных выполните хранимую процедуру [sp_helpdatatypemap](/sql/relational-databases/system-stored-procedures/sp-helpdatatypemap-transact-sql). Укажите значение **ORACLE** в параметре **\@source_dbms** и задайте значения других параметров, необходимых для фильтрации результирующего набора.  
  
###  <a name="TsqlExample"></a>Примеры (Transact-SQL)  
 Следующий пример производит сопоставление столбца данных Oracle типа NUMBER с типом данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]`numeric`(38,38) вместо типа данных `float`, используемого по умолчанию.  
  
 [!code-sql[HowTo#sp_changecolumndatatype](../../../snippets/tsql/SQL15/replication/howto/tsql/datatypemapping.sql#sp_changecolumndatatype)]  
  
 Следующий пример запроса возвращает два сопоставления для типа данных Oracle 9 `CHAR`: определенное по умолчанию и альтернативное.  
  
 [!code-sql[HowTo#sp_helpcolumndatatype_char](../../../snippets/tsql/SQL15/replication/howto/tsql/datatypemapping.sql#sp_helpcolumndatatype_char)]  
  
 Следующий пример запроса возвращает сопоставления по умолчанию для типа данных Oracle 9 `NUMBER`, когда он указан без масштаба и точности.  
  
 [!code-sql[HowTo#sp_helpcolumndatatype_number](../../../snippets/tsql/SQL15/replication/howto/tsql/datatypemapping.sql#sp_helpcolumndatatype_number)]  
  
## <a name="see-also"></a>См. также:  
 [Сопоставление типов данных для издателей Oracle](../non-sql/data-type-mapping-for-oracle-publishers.md)   
 [Разнородная репликация базы данных](../non-sql/heterogeneous-database-replication.md)   
 [Основные понятия системных хранимых процедур репликации](../concepts/replication-system-stored-procedures-concepts.md)   
 [Настройка издателя Oracle](../non-sql/configure-an-oracle-publisher.md)  
  
  
