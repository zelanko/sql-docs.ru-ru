---
title: Включение инициализации с помощью резервной копии для публикаций транзакций (SQL Server Management Studio) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- manual subscription initialization [SQL Server replication]
- subscriptions [SQL Server replication], initializing
- initializing subscriptions [SQL Server replication], without snapshots
- transactional replication, backup and restore
- backups [SQL Server replication], transactional replication
ms.assetid: 9df00514-aa9d-4ac6-9766-d226c9958175
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f5e22614c8c4f5250db3966e747b686091512774
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85010724"
---
# <a name="enable-initialization-with-a-backup-for-transactional-publications-sql-server-management-studio"></a>включить инициализацию из резервной копии для публикаций транзакций (среда SQL Server Management Studio)
  Для инициализации подписки на публикацию транзакций из резервной копии сначала активизируйте публикацию, чтобы разрешить инициализацию из резервной копии, а затем, создавая подписку, укажите сведения о резервной копии:  
  
-   Включите публикацию на странице **Параметры подписки** диалогового окна **Свойства публикации — \<Publication> ** . Дополнительные сведения о доступе к этому диалоговому окну см. в разделе [Просмотр и изменение свойств публикации](publish/view-and-modify-publication-properties.md).  
  
-   Укажите сведения о резервной копии с помощью хранимой процедуры [sp_addsubscription (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql). Дополнительные сведения о параметрах **sp_addsubscription** можно найти в статье [Инициализация транзакционной подписки из резервной копии (программирование репликации на языке Transact-SQL)](initialize-a-transactional-subscription-from-a-backup.md).  
  
### <a name="to-enable-initialization-with-a-backup"></a>Включение инициализации с помощью резервной копии  
  
1.  На странице **Параметры подписки** диалогового окна **Свойства публикации — \<Publication> ** выберите значение **true** для параметра **разрешить инициализацию из файлов резервных копий** .  
  
## <a name="see-also"></a>См. также:  
 [Инициализация подписки на публикацию транзакций без моментального снимка](initialize-a-transactional-subscription-without-a-snapshot.md)  
  
  
