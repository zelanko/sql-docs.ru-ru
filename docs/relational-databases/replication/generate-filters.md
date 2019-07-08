---
title: Формирование фильтров | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.newpubwizard.generatefilters.f1
ms.assetid: be28515c-5d6d-467b-b933-d7c8d97a45b4
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 14ccac181a4b76f8fc0423d6e00b20f91f8ea9cc
ms.sourcegitcommit: cff8dd63959d7a45c5446cadf1f5d15ae08406d8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/05/2019
ms.locfileid: "67581362"
---
# <a name="generate-filters"></a>Формирование фильтров
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Диалоговое окно **Формирование фильтров** позволяет определить фильтр строк на одной таблице в публикации слиянием. Далее репликация автоматически распространяет фильтр на другие таблицы, связанные через связи внешних ключей. Например, если фильтр определяется на таблице заказчика таким образом, чтобы в результате фильтрации оставались только данные о французских заказчиках, репликация распространяет этот фильтр таким образом, что соответствующие заказы и таблицы с подробностями заказов будут содержать только данные, относящиеся к французским заказчикам.  
  
## <a name="options"></a>Параметры  
 В этом диалоговом окне используется трехступенчатый процесс создания фильтра строк на таблице. Затем фильтр распространяется на таблицы, связанные с фильтруемой таблицей связями первичного и внешнего ключей. Допустим, имеются три таблицы: **Customer**, **SalesOrderHeader**и **SalesOrderDetail**. Допустим, имеются связи между таблицами **Customer** и **SalesOrderHeader**, а также между **SalesOrderHeader** и **SalesOrderDetail**. Тогда, если фильтр строк применяется к таблице **Customer**, репликация распространяет этот фильтр на таблицы **SalesOrderHeader** и **SalesOrderDetail**.  
  
1.  **Выберите таблицу для фильтрации.**  
  
     Выберите таблицу из раскрывающегося списка. В этом списке присутствуют только те таблицы, которые были выбраны на странице **Статьи** .  
  
2.  **Завершите инструкцию фильтра, чтобы указать те строки таблицы, которые будут получать подписчики.**  
  
     Определите новую инструкцию фильтра. Список **Столбцы** содержит все столбцы, публикуемые из выбранной таблицы в поле **Выберите таблицу для фильтрации**. Текстовая область **Инструкция фильтра** содержит текст по умолчанию, в виде:  
  
     `SELECT <published_columns> FROM [tableowner].[tablename] WHERE`  
  
     Этот текст не может быть изменен; введите предложение фильтра после ключевого слова WHERE, используя обычный синтаксис [!INCLUDE[tsql](../../includes/tsql-md.md)] .  
  
    > [!IMPORTANT]  
    >  По соображениям производительности не рекомендуется применять функции к именам столбцов в предложениях параметризованных фильтров строк, например `LEFT([MyColumn]) = SUSER_SNAME()`. Если в предложении фильтра используется HOST_NAME и переопределяется значение HOST_NAME, может быть, необходимо выполнить преобразование типов данных при помощи инструкции CONVERT. Дополнительные сведения см. в подразделе «Переопределение значения HOST_NAME()» раздела [Parameterized Row Filters](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md).  
  
3.  **Укажите, сколько подписок будет получать данные из этой таблицы.**  

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

     [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions only. Merge replication allows you to specify the type of partitions that are best suited to your data and application. If you select **A row from this table will go to only one subscription**, merge replication sets the nonoverlapping partitions option. Nonoverlapping partitions work in conjunction with precomputed partitions to improve performance, with nonoverlapping partitions minimizing the upload cost associated with precomputed partitions. The performance benefit of nonoverlapping partitions is more noticeable when the parameterized filters and join filters used are more complex. If you select this option, you must ensure that the data is partitioned in such a way that a row cannot be replicated to more than one Subscriber. For more information, see the section "Setting 'partition options'" in the topic [Parameterized Row Filters](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md).  
  
 После добавления фильтра нажмите кнопку **ОК** для выхода и закрытия диалогового окна. Проводится синтаксический анализ указанного фильтра, после чего фильтр применяется к таблице в предложении SELECT. Если оператор фильтра содержит синтаксические ошибки или встречаются другие проблемы, пользователь уведомляется, после чего может отредактировать эту инструкцию фильтра.  
  
 После выполнения синтаксического анализа инструкции репликация создает необходимые фильтры соединения. Если распространитель еще не настроен на издателя, на котором выполняется этот мастер, пользователю предлагается настроить распространитель.  
  
## <a name="see-also"></a>См. также:  
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [Просмотр и изменение свойств публикации](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [Фильтрация опубликованных данных](../../relational-databases/replication/publish/filter-published-data.md)   
 [Join Filters](../../relational-databases/replication/merge/join-filters.md)   
 [Parameterized Row Filters](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md)   
 [Публикация данных и объектов базы данных](../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  
