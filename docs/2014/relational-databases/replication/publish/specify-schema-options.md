---
title: Указание параметров схемы | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- schemas [SQL Server replication], options
- articles [SQL Server replication], transactional replication options
- articles [SQL Server replication], merge replication options
- articles [SQL Server replication], schema options
ms.assetid: 1f85a479-bd6e-4023-abf7-7435a7e5b567
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e6826d28ec923de221e94b985b740a172bdaa7d5
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "73882165"
---
# <a name="specify-schema-options"></a>Указание параметров схемы
  В этом разделе описывается указание параметров схемы в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../../includes/tsql-md.md)]. При публикации таблицы или представления можно управлять параметрами создания объектов, применяемых к опубликованному объекту. Эти параметры можно задать при создании статьи, а также изменить их позднее. Если эти параметры не заданы в явном виде, то применяется набор параметров по умолчанию.  
  
> [!NOTE]  
>  Параметры схемы по умолчанию при использовании хранимых процедур репликации могут отличаться от параметров по умолчанию, применяемых для добавления статей с помощью среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [Рекомендации](#Recommendations)  
  
-   **Для указания параметров схемы используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Ограничения  
  
-   Если изменить параметры схемы после создания публикации, то необходимо создать новый моментальный снимок.  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> Рекомендации  
  
-   Полный список параметров схемы см. в ** \@разделе schema_option** параметр [sp_addarticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql) и [sp_addmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql).  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 На вкладке **Свойства** диалогового окна **Свойства статьи - \<статья>** задайте параметры схемы, например укажите, необходимо ли копировать ограничения и триггеры для подписчиков. Эта вкладка доступна в мастере создания публикаций, а также в диалоговом окне **Свойства публикации - \<публикация>** . Дополнительные сведения об использовании мастера и доступе к этому диалоговому окну см. в статьях [Создание публикации](create-a-publication.md) и [Просмотр и изменение свойств публикации](view-and-modify-publication-properties.md).  
  
#### <a name="to-specify-schema-options"></a>Указание параметров схемы  
  
1.  На странице **Статьи** мастера создания публикаций или в диалоговом окне **Свойства публикации - \<публикация>** выберите нужную статью и щелкните **Свойства статьи**.  
  
2.  Выберите статьи, для которых необходимо внести изменения в параметры схемы:  
  
    -   Щелкните **Указать свойства выделенной статьи \<тип_объекта>** , чтобы открыть диалоговое окно **Свойства статьи — \<имя_объекта>** . Изменения, внесенные в этом диалоговом окне, применяются только к объекту, который будет выделен на панели объектов на странице **Статьи**.  
  
    -   Щелкните **Указать свойства всех статей \<тип_объекта>** , чтобы открыть диалоговое окно **Свойства всех статей \<тип_объекта>** . Изменения свойств, внесенные в этом диалоговом окне, применяются ко всем объектам этого типа на панели объектов на странице **Статьи**, включая объекты, не выбранные для публикации.  
  
        > [!NOTE]  
        >  Изменения свойств, внесенные в диалоговом окне **Свойства всех статей \<тип_объекта>** переопределяют изменения, сделанные ранее в диалоговом окне **Свойства статьи — \<имя_объекта>** . Например, если нужно установить некоторое количество значений по умолчанию для всех статей типа объекта, но при этом задать некоторые свойства для отдельных объектов, сначала установите значения по умолчанию для всех статей. Затем установите свойства для отдельных объектов.  
  
3.  Укажите значения параметров в разделах **Копировать объекты и установки на подписчик** и **Целевой объект** на вкладке **Свойства** диалогового окна **Свойства статьи - \<статья>** .  
  
4.  Измените свойства, если необходимо, и нажмите кнопку **ОК**.  
  
5.  Если вы находитесь в диалоговом окне **Свойства публикации — \<публикация>** , нажмите кнопку **ОК**, чтобы сохранить изменения и закрыть диалоговое окно.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
 Параметры схемы указываются в виде шестнадцатеричных значений, которые являются результатом выполнения операции [| (побитовое ИЛИ)](/sql/t-sql/language-elements/bitwise-or-transact-sql) к одному или нескольким параметрам. Дополнительные сведения см. в разделах [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql) и [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql).  
  
> [!NOTE]  
>  Прежде чем применять битовые операции к значениям параметров схемы, необходимо преобразовать их значения из типа **binary** в тип **int** . Дополнительные сведения см. в разделе [Функции CAST и CONVERT (Transact-SQL)](/sql/t-sql/functions/cast-and-convert-transact-sql).  
  
#### <a name="to-specify-schema-options-when-defining-an-article-for-a-snapshot-or-transactional-publication"></a>Задание параметров схемы при определении статьи для публикации моментальных снимков или транзакций  
  
1.  Выполните процедуру [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql)на издателе в базе данных публикации. Укажите имя публикации, которой принадлежит статья для ** \@публикации**, имя статьи для ** \@статьи**, публикуемый объект базы данных для ** \@source_object**, тип объекта базы данных для ** \@типа**и объект [| (Побитовое или)](/sql/t-sql/language-elements/bitwise-or-transact-sql) результат одного или нескольких параметров схемы для ** \@schema_option**. Дополнительные сведения см. в статье [определить статью](define-an-article.md).  
  
#### <a name="to-specify-schema-options-when-defining-an-article-for-a-merge-publication"></a>Задание параметров схемы при определении статьи для публикации слиянием  
  
1.  В базе данных публикации на издателе выполните процедуру [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql). Укажите имя публикации, которой принадлежит статья для ** \@публикации**, имя статьи для ** \@статьи**, публикуемый объект базы данных для ** \@source_object**и [| (Побитовое или)](/sql/t-sql/language-elements/bitwise-or-transact-sql) результат одного или нескольких параметров схемы для ** \@schema_option**. Дополнительные сведения см. в статье [определить статью](define-an-article.md).  
  
#### <a name="to-change-schema-options-for-an-existing-article-in-a-snapshot-or-transactional-publication"></a>Изменение параметров схемы в существующей статье публикации моментальных снимков или транзакций  
  
1.  В базе данных публикации на издателе выполните процедуру [sp_helparticle](/sql/relational-databases/system-stored-procedures/sp-helparticle-transact-sql). Укажите имя публикации, которой принадлежит статья для ** \@публикации** , и имя статьи для ** \@статьи**. Запомните значение столбца **schema_option** в результирующем наборе.  
  
2.  Чтобы определить, установлен ли определенный параметр, выполните операцию [побитового сложения (&)](/sql/t-sql/language-elements/bitwise-and-transact-sql) требуемого значения параметра схемы со значением, полученным на шаге 1.  
  
    -   Если результат равен **0**, параметр не установлен.  
  
    -   Если результатом является значение параметра, то он уже установлен.  
  
3.  Если параметр не установлен, выполните операцию [| (побитовое ИЛИ)](/sql/t-sql/language-elements/bitwise-or-transact-sql) , используя значение из шага 1 и требуемое значение параметра схемы.  
  
4.  Выполните процедуру [sp_changearticle](/sql/relational-databases/system-stored-procedures/sp-changearticle-transact-sql)на издателе в базе данных публикации. Укажите имя публикации, которой принадлежит статья для ** \@публикации**, имя статьи для ** \@статьи**, значение **schema_option** для ** \@свойства**и шестнадцатеричный результат из шага 3 в качестве ** \@значения**.  
  
5.  Запустите агент моментальных снимков, чтобы создать новый моментальный снимок. Дополнительные сведения см. в разделе [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md).  
  
#### <a name="to-change-schema-options-for-an-existing-article-in-a-merge-publication"></a>Изменение параметров схемы для существующей статьи в публикации слиянием  
  
1.  В базе данных публикации на издателе выполните процедуру [sp_helpmergearticle](/sql/relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql). Укажите имя публикации, которой принадлежит статья для ** \@публикации** , и имя статьи для ** \@статьи**. Запомните значение столбца **schema_option** в результирующем наборе.  
  
2.  Чтобы определить, установлен ли определенный параметр, выполните операцию [побитового сложения (&)](/sql/t-sql/language-elements/bitwise-and-transact-sql) требуемого значения параметра схемы со значением, полученным на шаге 1.  
  
    -   Если результат равен **0**, параметр не установлен.  
  
    -   Если результатом является значение параметра, то он уже установлен.  
  
3.  Если параметр не установлен, выполните операцию [| (побитовое ИЛИ)](/sql/t-sql/language-elements/bitwise-or-transact-sql) , используя значение из шага 1 и требуемое значение параметра схемы.  
  
4.  В базе данных публикации на издателе выполните процедуру [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql). Укажите имя публикации, которой принадлежит статья для ** \@публикации**, имя статьи для ** \@статьи**, значение **schema_option** для ** \@свойства**и шестнадцатеричный результат из шага 3 в качестве ** \@значения**.  
  
5.  Запустите агент моментальных снимков, чтобы создать новый моментальный снимок. Дополнительные сведения см. в разделе [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md).  
  
## <a name="see-also"></a>См. также:  
 [Публикация данных и объектов базы данных](publish-data-and-database-objects.md)   
 [Article Options for Transactional Replication](../transactional/article-options-for-transactional-replication.md)  
  
  
