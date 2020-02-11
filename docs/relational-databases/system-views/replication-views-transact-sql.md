---
title: Представления репликации (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- distribution databases [SQL Server replication], system views
- metadata [SQL Server], views
- views [SQL Server], replication
- replication views [SQL Server]
- publications [SQL Server replication], system views
- articles [SQL Server replication], system views
- replication metadata [SQL Server]
- subscriptions [SQL Server replication], system views
- system views [SQL Server], replication
ms.assetid: 93e5056d-0d93-4a48-ba33-72762eb995d8
author: stevestein
ms.author: sstein
ms.openlocfilehash: 51cc9434805fbd14204d74edae1594ae01c06bb2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68129570"
---
# <a name="replication-views-transact-sql"></a>Представления репликации (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Эти представления содержат сведения, используемые репликацией в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Представления обеспечивают более простой доступ к данным в [системных таблицах репликации](../../relational-databases/system-tables/replication-tables-transact-sql.md). Представления создаются в пользовательской базе данных, когда эта база данных используется в качестве базы данных публикации или подписки. Все объекты репликации удаляются из пользовательской базы данных, когда эта база данных удаляется из топологии репликации. Предпочтительным методом доступа к метаданным репликации является использование [хранимых процедур репликации](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md).  
  
> [!IMPORTANT]  
>  Системные представления не должны подвергаться непосредственному изменению каким-либо пользователем.  
  
## <a name="replication-views"></a>Представления репликации  
 Ниже представлен список системных представлений, используемых репликацией, с группированием элементов по базе данных.  
  
### <a name="replication-views-in-the-msdb-database"></a>Представления репликации в базе данных msdb  
  
|||  
|-|-|  
|[MSdatatype_mappings &#40;Transact-SQL&#41;](../../relational-databases/system-views/msdatatype-mappings-transact-sql.md)|[sysdatatypemappings &#40;Transact-SQL&#41;](../../relational-databases/system-views/sysdatatypemappings-transact-sql.md)|  
  
### <a name="replication-views-in-the-distribution-database"></a>Представления репликации в базе данных распространителя  
  
|||  
|-|-|  
|[IHextendedArticleView &#40;Transact-SQL&#41;](../../relational-databases/system-views/ihextendedarticleview-transact-sql.md)|[sysarticles &#40;системного представления&#41; &#40;&#41;Transact-SQL](../../relational-databases/system-views/sysarticles-system-view-transact-sql.md)|  
|[Ихекстендедсубскриптионвиев &#40;Transact-SQL&#41;](../../relational-databases/system-views/ihextendedsubscriptionview-transact-sql.md)|[сисекстендедартиклесвиев &#40;Transact-SQL&#41;](../../relational-databases/system-views/sysextendedarticlesview-transact-sql.md)|  
|[Ихсисколумнс &#40;Transact-SQL&#41;](../../relational-databases/system-views/ihsyscolumns-transact-sql.md)|[syspublications &#40;системного представления&#41; &#40;&#41;Transact-SQL](../../relational-databases/system-views/syspublications-system-view-transact-sql.md)|  
|[MSdistribution_status &#40;Transact-SQL&#41;](../../relational-databases/system-views/msdistribution-status-transact-sql.md)|[syssubscriptions &#40;системного представления&#41; &#40;&#41;Transact-SQL](../../relational-databases/system-views/syssubscriptions-system-view-transact-sql.md)|  
|[Системное представление sysarticlecolumns &#40;системного представления&#41; &#40;&#41;Transact-SQL](../../relational-databases/system-views/sysarticlecolumns-system-view-transact-sql.md)||  
  
### <a name="replication-views-in-the-publication-database"></a>Представления репликации в базе данных публикации  
  
|||  
|-|-|  
|[сисмержеекстендедартиклесвиев &#40;Transact-SQL&#41;](../../relational-databases/system-views/sysmergeextendedarticlesview-transact-sql.md)|[сисмержепартитионинфовиев &#40;Transact-SQL&#41;](../../relational-databases/system-views/sysmergepartitioninfoview-transact-sql.md)|  
|[systranschemas &#40;Transact-SQL&#41;](../../relational-databases/system-views/systranschemas-transact-sql.md)||  
  
### <a name="replication-views-in-the-subscription-database"></a>Представления репликации в базе данных подписки  
  
|||  
|-|-|  
|[сисмержеекстендедартиклесвиев &#40;Transact-SQL&#41;](../../relational-databases/system-views/sysmergeextendedarticlesview-transact-sql.md)|[сисмержепартитионинфовиев &#40;Transact-SQL&#41;](../../relational-databases/system-views/sysmergepartitioninfoview-transact-sql.md)|  
|[systranschemas &#40;Transact-SQL&#41;](../../relational-databases/system-views/systranschemas-transact-sql.md)||  
  
## <a name="see-also"></a>См. также:  
 [Таблицы репликации &#40;&#41;Transact-SQL](../../relational-databases/system-tables/replication-tables-transact-sql.md)  
  
  
