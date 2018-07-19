---
title: Граф, обработка с помощью SQL Server и базы данных SQL Azure | Документация Майкрософт
ms.custom: ''
ms.date: 07/18/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: graphs
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- SQL graph
- SQL graph, overview
ms.assetid: ''
caps.latest.revision: 1
author: shkale-msft
ms.author: shkale
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2017 || = sqlallproducts-allversions
ms.openlocfilehash: 8c2ad7f5b31a97de5d0bfb22074b55bd61bb825b
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38015680"
---
# <a name="graph-processing-with-sql-server-and-azure-sql-database"></a>Граф, обработка с помощью SQL Server и базы данных SQL Azure
[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предоставляет возможности диаграммы базы данных для моделирования связей многие ко многим. Граф связей интегрированы в [!INCLUDE[tsql-md](../../includes/tsql-md.md)] и получать преимущества использования [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] как система управления базовой базы данных.


## <a name="what-is-a-graph-database"></a>Что такое база данных графов  
База данных графов состоит из узлов (или вершины) и краев (или связи). Узел представляет сущность (например, пользователя или организации) и ребро представляет связь между двумя узлами, которые он подключается (для примера, пометки "нравится" или друзей). Узлы и ребра могут иметь свойства, связанные с ними. Ниже приведены некоторые функции, делающие уникальный базы данных графа.  
-   Края или связи являются первого класса сущностей в базу данных графов и могут иметь атрибуты или свойства, связанные с ними. 
-   Одним краем гибко можно подключить несколько узлов в базу данных графов.
-   Легко можно выразить сопоставления по шаблону и запросы многоступенчатую навигацию.
-   Легко можно выразить транзитивное замыкание и полиморфные запросы.

## <a name="when-to-use-a-graph-database"></a>Когда следует использовать базу данных графов

Нет ничего, базы данных графа можно добиться, чего нельзя добиться с помощью реляционной базы данных. Тем не менее базы данных графа можно упростить express определенного типа запросов. Кроме того, с помощью оптимизировать код, некоторые запросы могут эффективнее. Выберите иное решение может основываться на следующие факторы:  
-   Ваше приложение имеет иерархическую структуру данных. Тип данных HierarchyID можно использовать для реализации иерархии, но он имеет некоторые ограничения. Например он не позволяет хранить несколько родительских элементов для узла.
-   Приложение содержит сложные связи многие ко многим; по мере развития приложения добавляются новые связи.
-   В этом случае необходимо выполнить анализ взаимосвязанных данных и связи.

## <a name="graph-features-introduced-in-includesssqlv14includessssqlv14-mdmd"></a>Граф функций, появившихся в [!INCLUDE[sssqlv14](../../includes/sssqlv14-md.md)] 
Мы начинаем добавлять расширения графа для SQL Server, чтобы упростить хранение и выполнение запросов graph. В первом выпуске добавлены следующие возможности. 


### <a name="create-graph-objects"></a>Создание графа объектов
[!INCLUDE[tsql-md](../../includes/tsql-md.md)] расширения позволит пользователям создавать узла или граничной таблицы. Узлы и ребра может иметь свойства, связанные с ними. Так как узлы и ребра хранятся в виде таблиц, все операции, которые поддерживаются в реляционные таблицы поддерживаются для узлов или граничную таблицу. Например:  

```   
CREATE TABLE Person (ID INTEGER PRIMARY KEY, Name VARCHAR(100), Age INT) AS NODE;
CREATE TABLE friends (StartDate date) AS EDGE;
```   

![пользователь друзей tables](../../relational-databases/graphs/media/person-friends-tables.png "узел Person и друзей периметра таблиц")  
Узлы и ребра хранятся в виде таблицы  

### <a name="query-language-extensions"></a>Расширения языка запросов  
Новый `MATCH` предложение вводится для поддержки сопоставления по шаблону и многоступенчатую навигацию через graph. `MATCH` Функция использует синтаксис искусство ASCII для сопоставления шаблонов. Например:  

```   
-- Find friends of John
SELECT Person2.Name 
FROM Person Person1, Friends, Person Person2
WHERE MATCH(Person1-(Friends)->Person2)
AND Person1.Name = 'John';
```   
 
### <a name="fully-integrated-in-includessnoversionincludesssnoversion-mdmd-engine"></a>Полностью интегрированный в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ядра 
Расширения Graph полностью интегрированы в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ядра. Мы используем же подсистемы хранилища, метаданные, обработчик запросов, и т.д. для хранения и запросов к данным графа. Это позволяет пользователям запрашивать их graph и реляционных данных в одном запросе. Пользователи также могут выиграть от объединения возможности диаграммы с другими [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] технологии, такие как службы R columnstore, высокой ДОСТУПНОСТИ, и т.д. База данных SQL graph также поддерживает все безопасности и соответствия требованиям функции, доступные с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
 
### <a name="tooling-and-ecosystem"></a>Инструментарий и экосистема  
Пользователи получают преимущества существующих средств и экосистема, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предлагает. Такие средства, как резервное копирование и восстановление, Импорт и экспорт BCP просто работать без дополнительной настройки. Другие средства или служб, таких как службы SSIS, SSRS или PowerBI будет работать с таблицами графа, именно так, как они работают с реляционными таблицами.
 
 ## <a name="next-steps"></a>Следующие шаги  
Чтение [Graph базы данных SQL — архитектура](./sql-graph-architecture.md)
   

