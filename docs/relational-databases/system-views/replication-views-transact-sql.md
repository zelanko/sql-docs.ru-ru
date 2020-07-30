---
title: Представления репликации (Transact-SQL) | Документация Майкрософт
description: Представления репликации содержат сведения, используемые репликацией в SQL Server. Они обеспечивают более удобный доступ к данным в системных таблицах репликации.
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
ms.openlocfilehash: ab4088aa563befcb32eaaf8fe129716b789f516b
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/28/2020
ms.locfileid: "87243615"
---
# <a name="replication-views-transact-sql"></a>Представления репликации (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Эти представления содержат сведения, используемые репликацией в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Представления обеспечивают более простой доступ к данным в [системных таблицах репликации](../../relational-databases/system-tables/replication-tables-transact-sql.md). Представления создаются в пользовательской базе данных, когда эта база данных используется в качестве базы данных публикации или подписки. Все объекты репликации удаляются из пользовательской базы данных, когда эта база данных удаляется из топологии репликации. Предпочтительным методом доступа к метаданным репликации является использование [хранимых процедур репликации](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md).  
  
> [!IMPORTANT]  
>  Системные представления не должны подвергаться непосредственному изменению каким-либо пользователем.  
  
## <a name="replication-views"></a>Представления репликации  
 Ниже представлен список системных представлений, используемых репликацией, с группированием элементов по базе данных.  
  
### <a name="replication-views-in-the-msdb-database"></a>Представления репликации в базе данных msdb  

:::row:::
    :::column:::
        [MSdatatype_mappings &#40;Transact-SQL&#41;](../../relational-databases/system-views/msdatatype-mappings-transact-sql.md)
    :::column-end:::
    :::column:::
        [sysdatatypemappings &#40;Transact-SQL&#41;](../../relational-databases/system-views/sysdatatypemappings-transact-sql.md)
    :::column-end:::
:::row-end:::

### <a name="replication-views-in-the-distribution-database"></a>Представления репликации в базе данных распространителя  

:::row:::
    :::column:::
        [IHextendedArticleView &#40;Transact-SQL&#41;](../../relational-databases/system-views/ihextendedarticleview-transact-sql.md)

        [Ихекстендедсубскриптионвиев &#40;Transact-SQL&#41;](../../relational-databases/system-views/ihextendedsubscriptionview-transact-sql.md)

        [Ихсисколумнс &#40;Transact-SQL&#41;](../../relational-databases/system-views/ihsyscolumns-transact-sql.md)

        [MSdistribution_status &#40;Transact-SQL&#41;](../../relational-databases/system-views/msdistribution-status-transact-sql.md)

        [Системное представление sysarticlecolumns &#40;системного представления&#41; &#40;&#41;Transact-SQL](../../relational-databases/system-views/sysarticlecolumns-system-view-transact-sql.md)
    :::column-end:::
    :::column:::
        [sysarticles &#40;системного представления&#41; &#40;&#41;Transact-SQL](../../relational-databases/system-views/sysarticles-system-view-transact-sql.md)

        [сисекстендедартиклесвиев &#40;Transact-SQL&#41;](../../relational-databases/system-views/sysextendedarticlesview-transact-sql.md)

        [Системное представление syspublications (Transact-SQL)](../../relational-databases/system-views/syspublications-system-view-transact-sql.md)

        [Системное представление syssubscriptions (Transact-SQL)](../../relational-databases/system-views/syssubscriptions-system-view-transact-sql.md)
    :::column-end:::
:::row-end:::

### <a name="replication-views-in-the-publication-database"></a>Представления репликации в базе данных публикации  

:::row:::
    :::column:::
        [сисмержеекстендедартиклесвиев &#40;Transact-SQL&#41;](../../relational-databases/system-views/sysmergeextendedarticlesview-transact-sql.md)

        [systranschemas &#40;Transact-SQL&#41;](../../relational-databases/system-views/systranschemas-transact-sql.md)
    :::column-end:::
    :::column:::
        [сисмержепартитионинфовиев &#40;Transact-SQL&#41;](../../relational-databases/system-views/sysmergepartitioninfoview-transact-sql.md)
    :::column-end:::
:::row-end:::

### <a name="replication-views-in-the-subscription-database"></a>Представления репликации в базе данных подписки  

:::row:::
    :::column:::
        [сисмержеекстендедартиклесвиев &#40;Transact-SQL&#41;](../../relational-databases/system-views/sysmergeextendedarticlesview-transact-sql.md)

        [сисмержепартитионинфовиев &#40;Transact-SQL&#41;](../../relational-databases/system-views/sysmergepartitioninfoview-transact-sql.md)
    :::column-end:::
    :::column:::
        [systranschemas &#40;Transact-SQL&#41;](../../relational-databases/system-views/systranschemas-transact-sql.md)
    :::column-end:::
:::row-end:::
  
## <a name="see-also"></a>См. также:  
 [Таблицы репликации (Transact-SQL)](../../relational-databases/system-tables/replication-tables-transact-sql.md)  
  
  
