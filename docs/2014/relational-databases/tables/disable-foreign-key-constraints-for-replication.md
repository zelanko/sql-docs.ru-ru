---
title: Отключение ограничений внешнего ключа для репликации | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- constraints [SQL Server], foreign keys
- foreign keys [SQL Server], disabling constraints
- disabling constraints
ms.assetid: 4211f2fd-d16a-4081-995c-43f1f0827f0b
caps.latest.revision: 19
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 03011cafe567a3ef2627d068c838b59cfee4ba81
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36190175"
---
# <a name="disable-foreign-key-constraints-for-replication"></a>Отключение ограничений внешнего ключа для репликации
  Отключить ограничения внешнего ключа для репликации можно в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]. Это может потребоваться при публикации данных из предыдущей версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Если таблица публикуется для репликации, ограничения внешнего ключа для нее автоматически отключаются в случае операций, выполняемых агентами репликации. Когда агент репликации на подписчике выполняет вставку, обновление или удаление, ограничение не проверяется. Если эту же операцию выполняет пользователь, ограничение проверяется. Ограничение отключено для агента репликации по той причине, что оно уже проверено на издателе при выполнении исходной операции вставки, обновления или удаления данных.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [безопасность](#Security)  
  
-   **Отключение ограничения внешнего ключа для репликации с использованием следующих средств:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Требуется разрешение ALTER на таблицу.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-disable-a-foreign-key-constraint-for-replication"></a>Отключение ограничения внешнего ключа для репликации  
  
1.  В **обозревателе объектов**раскройте таблицу, содержащую ограничение внешнего ключа, которое необходимо изменить, а затем разверните папку **Ключи** .  
  
2.  Правой кнопкой мыши щелкните ограничение, а затем выберите команду **Изменить**.  
  
3.  В диалоговом окне **Связи по внешнему ключу** выберите значение **Нет** для параметра **Включить использование для репликации**.  
  
4.  Щелкните **Закрыть**.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-disable-a-foreign-key-constraint-for-replication"></a>Отключение ограничения внешнего ключа для репликации  
  
1.  Для выполнения этой задачи в [!INCLUDE[tsql](../../includes/tsql-md.md)]удалите ограничение внешнего ключа. Затем добавьте новое ограничение внешнего ключа и укажите параметр NOT FOR REPLICATION.  
  
 Дополнительные сведения см. в разделе [ALTER TABLE (Transact-SQL)](/sql/t-sql/statements/alter-table-transact-sql).  
  
###  <a name="TsqlExample"></a>  
