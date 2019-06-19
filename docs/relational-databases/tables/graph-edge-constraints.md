---
title: Ограничения ребер графа | Документация Майкрософт
ms.custom: ''
ms.date: 04/23/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- edge constraints [SQL Server]
- CONNECTION constraints
- edge constraints [Azure SQL Database]
- graph edge constraints
- SQL Graph
ms.assetid: ''
author: shkale-msft
ms.author: shkale
manager: craigg
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 86544dee5262a1d04c1ff1d8e59f8ddac5e9b5ce
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "64774655"
---
# <a name="edge-constraints"></a>Ограничения границ
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx.md](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

  Ограничения ребер могут использоваться для обеспечения целостности данных и применения определенной семантики в таблицах ребер в базе данных графа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. 
  
Эта статья состоит из следующих разделов:  
  
[Ограничения ребер](../../relational-databases/tables/graph-edge-constraints.md#Connection)  

[Ограничения ребер](../../relational-databases/tables/graph-edge-constraints.md#Connection)  
  
[Связанные задачи](../../relational-databases/tables/graph-edge-constraints.md#Tasks)  
  
##  <a name="Connection"></a> Ограничения ребер
 В первом выпуске функций графа в таблицах ребер не предусмотрено ничего для конечных точек ребра. То есть ребро в базе данных графа может соединить любой узел с другим, независимо от типа. 

 В этом выпуске появились ограничения ребер, позволяющие пользователям добавлять ограничения к таблицам ребер, тем самым принудительно применяя определенную семантику и сохраняя целостность данных. При добавлении нового ребра к таблицам ребер с помощью ограничений ребер [!INCLUDE[ssDE](../../includes/ssde-md.md)] обеспечивает существование узлов, которые ребро пытается соединить, в надлежащей таблице узлов. Также гарантируется, что узел не может быть удален, если на него еще ссылается ребро. 

 ### <a name="edge-constraint-clauses"></a>Предложения ограничения ребер
 Каждое ограничение ребер состоит из одного или нескольких предложений ограничения ребер. Предложение ограничения ребер — это пара начального и конечного узлов, которые может соединить данное ребро. 

 Предположим, что в графе есть узлы `Product` и `Customer`, для соединения которых используется ребро `Bought`. Предложение ограничения ребер указывает пару начального и конечного узлов и направление ребра. В этом случае предложение ограничения ребер будет соединять `Customer` с `Product`. То есть вставка ребра `Bought`, идущего от `Customer` к `Product`, будет разрешена. Попытки вставить ребро, которое соединяет `Product` с `Customer`, завершатся ошибкой. 
  
- Предложение ограничения ребра содержит таблицы пар начального и конечного узлов, к которым применяется ограничение ребра. 
  
- Пользователи могут указывать несколько предложений ограничения ребра на одно ограничение, которые будут применяться путем логического сложения.

- Если в одной таблице ребер созданы несколько ограничений, ребра будут разрешены, только если они соответствуют нескольким ограничениям.
  
### <a name="indexes-on-edge-constraints"></a>Индексы для ограничений ребер
 Создание ограничения ребра автоматически не создает соответствующий индекс для столбцов `$from_id` и `$to_id` в таблице ребер. Рекомендуется создать индексы для пары `$from_id` и `$to_id` вручную, если имеются запросы на поиск точек или рабочая нагрузка OLTP. 

##  <a name="Tasks"></a> Связанные задачи  
 В следующей таблице перечислены общие задачи, связанные с ограничениями ребер.  
  
|Задача|Статья|  
|----------|-----------|  
|Описывает, как создать ограничения ребер.|[Создание ограничений ребер](../../relational-databases/tables/create-edge-constraints.md)|  
|Описывает, как удалить ограничение ребра.|[Удаление ограничений ребер](../../relational-databases/tables/delete-edge-constraint.md)|  
|Описывает, как изменить ограничение ребра.|[Изменение ограничения ребер](../../relational-databases/tables/modify-edge-constraint.md)|  
|Описывает, как просмотреть свойства ограничения ребер.|[Просмотр свойств ограничений ребер](../../relational-databases/tables/view-edge-constraint-properties.md)|  
