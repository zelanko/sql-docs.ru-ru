---
title: Отключение ограничений внешнего ключа для репликации | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: table-view-index, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- constraints [SQL Server], foreign keys
- foreign keys [SQL Server], disabling constraints
- disabling constraints
ms.assetid: 4211f2fd-d16a-4081-995c-43f1f0827f0b
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 05e8ed3093230979e78b8623de9001f630579a8b
ms.sourcegitcommit: cff8dd63959d7a45c5446cadf1f5d15ae08406d8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/05/2019
ms.locfileid: "67580652"
---
# <a name="disable-foreign-key-constraints-for-replication"></a>Отключение ограничений внешнего ключа для репликации
[!INCLUDE[tsql-appliesto-ss2016-all-md](../../includes/tsql-appliesto-ss2016-all-md.md)]

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

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-disable-a-foreign-key-constraint-for-replication"></a>Отключение ограничения внешнего ключа для репликации  
  
1.  Для выполнения этой задачи в [!INCLUDE[tsql](../../includes/tsql-md.md)]удалите ограничение внешнего ключа. Затем добавьте новое ограничение внешнего ключа и укажите параметр NOT FOR REPLICATION.  
  
 Дополнительные сведения см. в разделе [ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md).  
  
###  <a name="TsqlExample"></a>  
