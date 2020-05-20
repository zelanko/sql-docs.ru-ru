---
title: Настройка параметров схемы для репликации SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
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
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: 1ce8df82856f7a6a495fdd026dec0d46eaba4c89
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "76287533"
---
# <a name="specify-schema-options-for-sql-server-replication"></a>Настройка параметров схемы для репликации SQL Server
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
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
  
-   Полный список параметров схемы см. в описании параметра `@schema_option` для хранимых процедур [sp_addarticle &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md) и [sp_addmergearticle &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md).  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 На вкладке **Свойства** диалогового окна **Свойства статьи - \<статья>** задайте параметры схемы, например укажите, необходимо ли копировать ограничения и триггеры для подписчиков. Эта вкладка доступна в мастере создания публикаций, а также в диалоговом окне **Свойства публикации - \<публикация>** . Дополнительные сведения об использовании мастера и доступе к этому диалоговому окну см. в статьях [Создание публикации](../../../relational-databases/replication/publish/create-a-publication.md) и [Просмотр и изменение свойств публикации](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
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
 Параметры схемы указываются в виде шестнадцатеричных значений, которые являются результатом выполнения операции [| (побитовое ИЛИ)](../../../t-sql/language-elements/bitwise-or-transact-sql.md) к одному или нескольким параметрам. Дополнительные сведения см. в разделах [sp_addarticle](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md) и [sp_addmergearticle](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md).  
  
> [!NOTE]  
>  Прежде чем применять битовые операции к значениям параметров схемы, необходимо преобразовать их значения из типа **binary** в тип **int** . Дополнительные сведения см. в разделе [Функции CAST и CONVERT (Transact-SQL)](../../../t-sql/functions/cast-and-convert-transact-sql.md).  
  
#### <a name="to-specify-schema-options-when-defining-an-article-for-a-snapshot-or-transactional-publication"></a>Задание параметров схемы при определении статьи для публикации моментальных снимков или транзакций  
  
1.  Выполните процедуру [sp_addarticle](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)на издателе в базе данных публикации. В параметре `@publication` задайте имя публикации, к которой принадлежит статья, в параметре `@article` — имя статьи, в параметре `@source_object` — публикуемый объект базы данных, в параметре `@type` — тип объекта базы данных, а в параметре `@schema_option` — результат операции [| (побитовое ИЛИ)](../../../t-sql/language-elements/bitwise-or-transact-sql.md) для одного из параметров схемы. Дополнительные сведения см. в статье [определить статью](../../../relational-databases/replication/publish/define-an-article.md).  
  
#### <a name="to-specify-schema-options-when-defining-an-article-for-a-merge-publication"></a>Задание параметров схемы при определении статьи для публикации слиянием  
  
1.  В базе данных публикации на издателе выполните процедуру [sp_addmergearticle](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md). В параметре `@publication` задайте имя публикации, к которой принадлежит статья, в параметре `@article` — имя статьи, в параметре `@source_object` — публикуемый объект базы данных, а в параметре `@schema_option` — результат операции [| (побитовое ИЛИ)](../../../t-sql/language-elements/bitwise-or-transact-sql.md) для одного из параметров схемы. Дополнительные сведения см. в статье [определить статью](../../../relational-databases/replication/publish/define-an-article.md).  
  
#### <a name="to-change-schema-options-for-an-existing-article-in-a-snapshot-or-transactional-publication"></a>Изменение параметров схемы в существующей статье публикации моментальных снимков или транзакций  
  
1.  В базе данных публикации на издателе выполните процедуру [sp_helparticle](../../../relational-databases/system-stored-procedures/sp-helparticle-transact-sql.md). Укажите имя публикации, которой принадлежит статья, в параметре `@publication` и имя статьи в параметре `@article`. Запомните значение столбца `schema_option` в результирующем наборе.  
  
2.  Чтобы определить, установлен ли определенный параметр, выполните операцию [побитового сложения (&)](../../../t-sql/language-elements/bitwise-and-transact-sql.md) требуемого значения параметра схемы со значением, полученным на шаге 1.  
  
    -   Если результат равен **0**, параметр не установлен.  
  
    -   Если результатом является значение параметра, то он уже установлен.  
  
3.  Если параметр не установлен, выполните операцию [| (побитовое ИЛИ)](../../../t-sql/language-elements/bitwise-or-transact-sql.md) , используя значение из шага 1 и требуемое значение параметра схемы.  
  
4.  Выполните процедуру [sp_changearticle](../../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md)на издателе в базе данных публикации. Укажите имя публикации, которой принадлежит статья, в параметре `@publication`, имя статьи в параметре `@article`, значение `schema_option` в параметре `@property` и шестнадцатеричный результат из шага 3 в параметре `@value`.  
  
5.  Запустите агент моментальных снимков, чтобы создать новый моментальный снимок. Дополнительные сведения см. в разделе [Create and Apply the Initial Snapshot](../../../relational-databases/replication/create-and-apply-the-initial-snapshot.md).  
  
#### <a name="to-change-schema-options-for-an-existing-article-in-a-merge-publication"></a>Изменение параметров схемы для существующей статьи в публикации слиянием  
  
1.  В базе данных публикации на издателе выполните процедуру [sp_helpmergearticle](../../../relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql.md). Укажите имя публикации, которой принадлежит статья, в параметре `@publication` и имя статьи в параметре `@article`. Запомните значение столбца **schema_option** в результирующем наборе.  
  
2.  Чтобы определить, установлен ли определенный параметр, выполните операцию [побитового сложения (&)](../../../t-sql/language-elements/bitwise-and-transact-sql.md) требуемого значения параметра схемы со значением, полученным на шаге 1.  
  
    -   Если результат равен **0**, параметр не установлен.  
  
    -   Если результатом является значение параметра, то он уже установлен.  
  
3.  Если параметр не установлен, выполните операцию [| (побитовое ИЛИ)](../../../t-sql/language-elements/bitwise-or-transact-sql.md) , используя значение из шага 1 и требуемое значение параметра схемы.  
  
4.  В базе данных публикации на издателе выполните процедуру [sp_changemergearticle](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md). Укажите имя публикации, которой принадлежит статья, в параметре `@publication`, имя статьи в параметре `@article`, значение `schema_option` в параметре `@property` и шестнадцатеричный результат из шага 3 в параметре `@value`.  
  
5.  Запустите агент моментальных снимков, чтобы создать новый моментальный снимок. Дополнительные сведения см. в разделе [Create and Apply the Initial Snapshot](../../../relational-databases/replication/create-and-apply-the-initial-snapshot.md).  
  
## <a name="see-also"></a>См. также:  
 [Публикация данных и объектов базы данных](../../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [Article Options for Transactional Replication](../../../relational-databases/replication/transactional/article-options-for-transactional-replication.md)  
  
  
