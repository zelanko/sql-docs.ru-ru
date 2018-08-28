---
title: Сводка по функциям разных версий PolyBase | Документация Майкрософт
ms.custom: ''
ms.date: 08/29/2017
ms.prod: sql
ms.technology: polybase
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 6591994d-6109-4285-9c5b-ecb355f8a111
author: rothja
ms.author: jroth
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: bc95156f93b6b87d317348f56e1b06f57439ada2
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43102112"
---
# <a name="polybase-versioned-feature-summary"></a>Сводка функций PolyBase по версиям
[!INCLUDE[appliesto-ss2016-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-all-md.md)]
Сводка функций PolyBase, доступных для продуктов и служб SQL Server.  
  
## <a name="feature-summary-for-product-releases"></a>Сводка функций по выпускам  
 В приведенной ниже таблице перечислены основные функции PolyBase и продукты, в которых они доступны.  
  
||||||
|-|-|-|-|-|   
|**Компонент**|**SQL Server 2016**|**База данных SQL Azure**|**Хранилище данных SQL Azure**|**Параллельное хранилище данных**| 
|Запрос данных Hadoop с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)]|да|нет|нет|да|
|Импорт данных из Hadoop|да|нет|нет|да|
|Экспорт данных в Hadoop  |да|нет|нет| да|
|Запрос, импорт из HDInsights, экспорт в HDInsights |нет|нет|нет|нет
|Отправка результатов вычислений запросов в Hadoop|да|нет|нет|да|  
|Импорт данных из хранилища BLOB-объектов Azure|да|нет|да|да| 
|Экспорт данных в хранилище BLOB-объектов Azure|да|нет|да|да|  
|Импорт данных из хранилища Azure Data Lake Store|нет|нет|да|нет|    
|Экспорт данных из хранилища Azure Data Lake Store|нет|нет|да|нет|
|Выполнение запросов PolyBase из средств бизнес-аналитики Майкрософт|да|нет|да|да|   


## <a name="pushdown-computation-supported-t-sql-operators"></a>Передача операторов T-SQL, поддерживаемых вычислением
В SQL Server и APS передачу в кластер Hadoop поддерживают лишь некоторые операторы. В следующей таблице перечислены все поддерживаемые операторы и приводится ряд неподдерживаемых операторов. 

||||
|-|-|-| 
|**Тип оператора**|**Отправка в Hadoop**|**Отправка в хранилище BLOB-объектов**|
|Проекции столбца|да|нет|
|Предикаты|да|нет|
|Статистические вычисления|частично|нет|
|Соединения между внешними таблицами|нет|нет|
|Соединения между внешними и локальными таблицами|нет|нет|
|Сортировки|нет|нет|

Частичная статистическая обработка означает, что окончательная статистическая обработка должна выполняться после достижения данными SQL Server, но часть статистической обработки происходит в Hadoop. Это общий метод вычисления статистических схем в системах с массивно-параллельной обработкой данных.  
## <a name="see-also"></a>См. также:  
 [Руководство по PolyBase](../../relational-databases/polybase/polybase-guide.md)  
  
  
