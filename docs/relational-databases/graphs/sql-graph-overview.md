---
title: Обработка с помощью SQL Server и базы данных SQL Azure Graph | Документы Microsoft
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
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2018
ms.locfileid: "34707052"
---
# <a name="graph-processing-with-sql-server-and-azure-sql-database"></a>Обработка с помощью SQL Server и базы данных SQL Azure Graph
[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предоставляет возможности диаграммы базы данных для моделирования связей многие ко многим. Граф связей интегрированы в [!INCLUDE[tsql-md](../../includes/tsql-md.md)] и получать преимущества использования [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] как основная база данных системы управления.


## <a name="what-is-a-graph-database"></a>Что такое диаграммы базы данных  
Диаграммы базы данных — это совокупность узлов (или вершин) и границ (или связи). Узел представляет сущность (например, человек или организация) и граница представляет связь между двумя узлами, которые он подключается (например для другого подобного места или друзей). Узлы и ребра, может иметь свойства, связанные с ними. Ниже приведены некоторые функции, чтобы уникальным диаграммы базы данных.  
-   Границы или связи — это сущности первого класса в диаграмме базы данных и могут иметь атрибуты или свойства, связанные с ними. 
-   Одним краем гибкое можно подключить несколько узлов в диаграмме базы данных.
-   Легко можно выразить регулярные выражения и запросы навигации мульти-прыжка.
-   Легко можно выразить транзитивное замыкание и полиморфного запросов.

## <a name="when-to-use-a-graph-database"></a>Когда следует использовать диаграммы базы данных

Нет ничего, что можно добиться диаграммы базы данных, которой нельзя сделать с помощью реляционной базы данных. Тем не менее диаграммы базы данных можно упростить express определенного типа запросов. Кроме того с определенной оптимизации определенных запросов может работать быстрее. Решение, чтобы выбрать необходимый сценарий может основываться на следующих факторов:  
-   Ваше приложение имеет иерархических данных. Тип данных HierarchyID можно использовать для реализации иерархии, но оно имеет некоторые ограничения. Например он не позволяет хранить несколько родительских элементов для узла.
-   Приложение содержит сложные связи многие ко многим; по мере развития приложения добавляются новые связи.
-   В этом случае необходимо выполнить анализ взаимосвязанных данных и связи.

## <a name="graph-features-introduced-in-includesssqlv14includessssqlv14-mdmd"></a>График функциям [!INCLUDE[sssqlv14](../../includes/sssqlv14-md.md)] 
Начинаем Добавление расширения graph в SQL Server упрощает хранение и выполнение запросов данных диаграммы. В первом выпуске добавлены следующие возможности. 


### <a name="create-graph-objects"></a>Создание графа объектов
[!INCLUDE[tsql-md](../../includes/tsql-md.md)] расширения позволит пользователям создавать узел или края таблицы. Узлы и ребра, может иметь свойства, связанные с ними. Начиная с узлы и ребра, хранятся в виде таблиц, все операции, которые поддерживаются на реляционных таблицах поддерживаются для узла или края таблицы. Например:  

```   
CREATE TABLE Person (ID INTEGER PRIMARY KEY, Name VARCHAR(100), Age INT) AS NODE;
CREATE TABLE friends (StartDate date) AS EDGE;
```   

![лицо, друзей, таблицы](../../relational-databases/graphs/media/person-friends-tables.png "узел Person и друзья ребро таблиц")  
Узлы и ребра, хранятся в виде таблицы  

### <a name="query-language-extensions"></a>Расширения языка запросов  
Новый `MATCH` предложение вводится для поддержки сопоставления шаблонов и перемещение мульти-прыжка по graph. `MATCH` Функция использует стиль синтаксиса рисунка ASCII сопоставление по шаблону. Например:  

```   
-- Find friends of John
SELECT Person2.Name 
FROM Person Person1, Friends, Person Person2
WHERE MATCH(Person1-(Friends)->Person2)
AND Person1.Name = 'John';
```   
 
### <a name="fully-integrated-in-includessnoversionincludesssnoversion-mdmd-engine"></a>Полностью интегрированная в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ядра 
Расширения Graph полностью интегрированы в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ядра. Мы используем же подсистемы хранилища, метаданных, обработчик запросов, т. д. для хранения и запроса данных диаграммы. Это позволяет пользователям запрашивать их graph и реляционных данных в одном запросе. Пользователи также могут выиграть от объединения возможностей диаграммы с другими [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] технологии, такие как служб R columnstore высокого уровня ДОСТУПНОСТИ, и т. д. База данных SQL graph также поддерживает все безопасности и соответствия требованиям функции, доступные с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
 
### <a name="tooling-and-ecosystem"></a>Инструментарий и сообщество  
Пользователи могут использовать существующие средства и экосистему, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предлагает. Такие средства, как резервное копирование и восстановление, Импорт и экспорт BCP работать без дополнительной настройки. Другие инструменты или службы, такие как службы SSIS, SSRS или PowerBI будет работать с таблицами graph так, как они работают с реляционными таблицами.
 
 ## <a name="next-steps"></a>Следующие шаги  
Чтение [диаграммы базы данных SQL — архитектура](./sql-graph-architecture.md)
   

