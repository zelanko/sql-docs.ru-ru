---
title: "Сводка функций PolyBase по версиям | Microsoft Docs"
ms.custom: ""
ms.date: "04/13/2016"
ms.prod: "sql-non-specified"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6591994d-6109-4285-9c5b-ecb355f8a111
caps.latest.revision: 10
author: "barbkess"
ms.author: "barbkess"
manager: "jhubbard"
caps.handback.revision: 8
---
# Сводка функций PolyBase по версиям
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw_md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  Сводка функций PolyBase, доступных для продуктов и служб SQL Server.  
  
## Сводка функций по выпускам  
 В приведенной ниже таблице перечислены основные функции PolyBase и продукты, в которых они доступны.  
  
### [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]  
 Эти функции относятся к [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] в локальной среде или в виртуальной машине Azure.  Технология PolyBase недоступна в SQL Server 2014 и более ранних версий.  
  
|||  
|-|-|  
|**Компонент**|**Доступность**|  
|Запрос данных Hadoop с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)]|да|  
|Запрос хранилища BLOB-объектов Azure с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)]|да|  
|Импорт данных из Hadoop|да|  
|Импорт данных из хранилища BLOB-объектов Azure|да|  
|Экспорт данных в Hadoop|да|  
|Экспорт данных в хранилище BLOB-объектов Azure|да|  
|Выполнение запросов PolyBase из средств бизнес-аналитики Майкрософт|да|  
|Отправка результатов вычислений запросов в Hadoop|да|  
  
### [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]  
 Эти функции относятся к [!INCLUDE[ssSDW](../../includes/sssdw-md.md)].  
  
|||  
|-|-|  
|**Компонент**|**Доступность**|  
|Запрос данных Hadoop с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)]|нет|  
|Запрос хранилища BLOB-объектов Azure с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)]|да|  
|Импорт данных из Hadoop|нет|  
|Импорт данных из хранилища BLOB-объектов Azure|да|  
|Экспорт данных в Hadoop|нет|  
|Экспорт данных в хранилище BLOB-объектов Azure|да|  
|Выполнение запросов PolyBase из средств бизнес-аналитики Майкрософт|да|  
|Отправка результатов вычислений запросов в Hadoop|нет|  
  
### [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 Эти функции относятся к [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].  
  
|||  
|-|-|  
|**Компонент**|**Доступность**|  
|Запрос данных Hadoop с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)]|да|  
|Запрос хранилища BLOB-объектов Azure с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)]|да|  
|Импорт данных из Hadoop|да|  
|Импорт данных из хранилища BLOB-объектов Azure|да|  
|Экспорт данных в Hadoop|да|  
|Экспорт данных в хранилище BLOB-объектов Azure|да|  
|Выполнение запросов PolyBase из средств бизнес-аналитики Майкрософт|да|  
|Отправка результатов вычислений запросов в Hadoop|да|  
  
## См. также:  
 [Руководство по PolyBase](../../relational-databases/polybase/polybase-guide.md)  
  
  