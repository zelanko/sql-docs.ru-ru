---
title: Отключение ограничений внешнего ключа для репликации | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: table-view-index, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: table-view-index
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- constraints [SQL Server], foreign keys
- foreign keys [SQL Server], disabling constraints
- disabling constraints
ms.assetid: 4211f2fd-d16a-4081-995c-43f1f0827f0b
caps.latest.revision: 20
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 342e975b72e338157794566966e8676a65217bad
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43074310"
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
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-disable-a-foreign-key-constraint-for-replication"></a>Отключение ограничения внешнего ключа для репликации  
  
1.  Для выполнения этой задачи в [!INCLUDE[tsql](../../includes/tsql-md.md)]удалите ограничение внешнего ключа. Затем добавьте новое ограничение внешнего ключа и укажите параметр NOT FOR REPLICATION.  
  
 Дополнительные сведения см. в разделе [ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md).  
  
###  <a name="TsqlExample"></a>  
