---
title: "Сопоставители на основе технологии COM | Документация Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- COM-based resolvers [SQL Server replication]
- custom resolvers [SQL Server replication]
ms.assetid: 94195797-ad7a-4962-a8e3-b259cd13aa38
caps.latest.revision: 36
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 88ccc09da5973beffdfa8b2595b1354c95b4cbb1
ms.lasthandoff: 04/11/2017

---
# <a name="advanced-merge-replication-conflict---com-based-custom-resolvers"></a>Конфликт расширенной репликации слиянием: пользовательские сопоставители на основе технологии COM
  Пользовательские сопоставители предоставляют большую гибкость по сравнению с механизмом разрешения конфликтов по умолчанию, и они могут реализовать бизнес-логику, необходимую для приложений, использующих реплицированные данные. Пользовательский сопоставитель на основе COM — это динамически подключаемая библиотека (DLL), которая реализует COM-интерфейс **ICustomResolver** , его методы и свойства, а также другие поддерживаемые интерфейсы и определения типов, разработанные специально для устранения конфликтов.  
  
> [!NOTE]  
>  Рекомендуется использовать обработчик бизнес-логики вместо пользовательского сопоставителя на основе COM, если это возможно. Дополнительные сведения об обработчиках бизнес-логики см. в статье [Выполнение бизнес логики во время синхронизации слияния](../../../relational-databases/replication/merge/execute-business-logic-during-merge-synchronization.md).  
  
 Для создания пользовательского COM-сопоставителя можно использовать библиотеку типов, которая содержится в файле replrec.dll. По умолчанию эта библиотека устанавливается в каталог [!INCLUDE[ssInstallPath](../../../includes/ssinstallpath-md.md)]COM.  
  
 Перед написанием пользовательского COM-сопоставителя необходимо определиться по следующим вопросам:  
  
-   Типы изменений строк, конфликты которых необходимо разрешить, например обновления, вставки и удаления, а также, должен ли сопоставитель вызываться во время передачи изменений слияния, загрузки изменений слияния, или его необходимо вызывать в обеих ситуациях. Можно указать один тип изменений, все изменения, или любое их сочетание. Сопоставитель конфликтов слияния по умолчанию обрабатывает любые конфликты, не охваченные пользовательским арбитром конфликтов.  
  
-   Надо ли использовать отслеживание столбца при разрешении конфликта. Когда включено отслеживание на уровне столбцов, только данные в тех столбцах, где существует конфликт, помечаются как конфликт, иначе данные объединяются. Однако конфликты разрешаются таким же способом, как и при отслеживании на уровне строк: победитель по приоритету перезаписывает всю строку данных (однако данные могут быть смесью значений от издателя, подписчиков или измененными значениями, которые не были получены ни от издателя, ни от подписчиков). Дополнительные сведения см. в статье [Detect and Resolve Merge Replication Conflicts](../../../relational-databases/replication/merge/advanced-merge-replication-resolve-merge-replication-conflicts.md).  
  
 Чтобы реализовать пользовательский арбитр конфликтов на основе технологии COM, см. раздел [Implement a Custom Conflict Resolver for a Merge Article](../../../relational-databases/replication/implement-a-custom-conflict-resolver-for-a-merge-article.md).  
  
 Пользовательский сопоставитель указывается для статьи, а не для всей публикации. Тот же самый сопоставитель может использоваться с более чем одной статьей, однако логика разрешения конфликтов в пользовательских сопоставителях часто характерна для определенной таблицы. Если используемая в статье таблица изменена после создания сопоставителя (например, изменено имя столбца, используемого при устранении конфликта), может потребоваться изменение и повторная компиляция пользовательского сопоставителя.  
  
 Чтобы указать пользовательский сопоставитель, см. раздел [Specify a Merge Article Resolver](../../../relational-databases/replication/publish/specify-a-merge-article-resolver.md).  
  
## <a name="see-also"></a>См. также:  
 [Advanced Merge Replication Conflict Detection and Resolution](../../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)   
 [Microsoft COM-Based Resolvers](../../../relational-databases/replication/merge/advanced-merge-replication-conflict-com-based-resolvers.md)  
  
  
