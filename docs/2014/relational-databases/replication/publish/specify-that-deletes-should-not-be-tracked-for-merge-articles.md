---
title: Укажите, что операции удаления не должны отслеживаться для статей публикации слиянием (Программирование репликации Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- conditional delete tracking [SQL Server replication]
- merge replication [SQL Server replication], conditional delete tracking
ms.assetid: 0fe330ca-5fb5-422e-ad6f-92fb5d6a3b6c
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 25e0eb6e257098d075cca4fb4d36d586efa1841b
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2018
ms.locfileid: "52772486"
---
# <a name="specify-that-deletes-should-not-be-tracked-for-merge-articles-replication-transact-sql-programming"></a>отключить отслеживание операций удаления для статей публикации слиянием (программирование репликации на языке Transact-SQL)
    
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
 По умолчанию репликация слиянием производит синхронизацию команд DELETE между издателем и подписчиком. Репликация слиянием позволяет извлекать строки из базы данных подписки даже в том случае, если они были удалены из публикации (и наоборот). При создании новой статьи можно отключить выполнение команд DELETE программным путем, либо сделать это позже с помощью хранимых процедур репликации.  
  
> [!IMPORTANT]  
>  Включение этой функции приведет к потере конвергенции, то есть возникнет несоответствие данных, содержащихся на подписчике и на издателе. Потребуется реализация собственного механизма очистки удаленных строк.  
  
### <a name="to-specify-that-deletes-be-ignored-for-a-new-merge-article"></a>Отключение обработки команд удаления для новой статьи слияния  
  
1.  В базе данных публикации на издателе выполните процедуру [sp_addmergearticle (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql). Укажите значение `false` для **@delete_tracking**. Дополнительные сведения см. в статье [определить статью](define-an-article.md).  
  
    > [!NOTE]  
    >  Если исходная таблица для статьи уже опубликована в другой публикации, значение **delete_tracking** должно быть одинаковым для обеих статей.  
  
### <a name="to-specify-that-deletes-be-ignored-for-an-existing-merge-article"></a>Отключение обработки команд удаления для существующих статей слияния  
  
1.  Чтобы определить, включена ли компенсация ошибок для статьи, выполните хранимую процедуру [sp_helpmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql) и в полученных результатах проверьте значение параметра **delete_tracking**. Если это значение равно **0**, то команды удаления уже не обрабатываются.  
  
2.  Если на шаге 1 получено значение **1** [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql), в базе данных публикации на издателе выполните процедуру Transact-SQL. Укажите значение **delete_tracking** для **@property**и значение `false` для **@value**.  
  
    > [!NOTE]  
    >  Если исходная таблица для статьи уже опубликована в другой публикации, значение **delete_tracking** должно быть одинаковым для обеих статей.  
  
## <a name="see-also"></a>См. также  
 [Оптимизация производительности репликации слиянием с помощью отслеживания условного удаления](../merge/optimize-merge-replication-performance-with-conditional-delete-tracking.md)  
  
  
