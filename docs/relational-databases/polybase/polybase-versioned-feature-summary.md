---
title: Возможности и ограничения PolyBase | Документация Майкрософт
ms.date: 09/24/2018
ms.prod: sql
ms.technology: polybase
ms.topic: conceptual
ms.assetid: 6591994d-6109-4285-9c5b-ecb355f8a111
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: aboke
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 9a619f67d951ba7407aa0987b2ca9fb65373de95
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68061968"
---
# <a name="polybase-features-and-limitations"></a>Возможности и ограничения PolyBase

[!INCLUDE[appliesto-ss2016-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-all-md.md)]

В этой статье приведена сводка функций PolyBase, доступных для продуктов и служб SQL Server.  
  
## <a name="feature-summary-for-product-releases"></a>Сводка функций по выпускам продукта

В следующей таблице перечислены основные функции PolyBase и продукты, в которых они доступны.  
  
||||||
|-|-|-|-|-|   
|**Компонент**|**SQL Server 2016**|**База данных SQL Azure**|**Хранилище данных SQL Azure**|**Параллельное хранилище данных**| 
|Запрос данных Hadoop с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)]|Да|нет|нет|Да|
|Импорт данных из Hadoop|Да|нет|нет|Да|
|Экспорт данных в Hadoop  |Да|нет|нет| Да|
|Запрос, импорт и экспорт данных в Azure HDInsight |нет|нет|нет|нет
|Отправка результатов вычислений запросов в Hadoop|Да|нет|нет|Да|  
|Импорт данных из хранилища BLOB-объектов Azure|Да|нет|Да|Да| 
|Экспорт данных в хранилище BLOB-объектов Azure|Да|нет|Да|Да|  
|Импорт данных из хранилища Azure Data Lake Store|нет|нет|Да|нет|    
|Экспорт данных из хранилища Azure Data Lake Store|нет|нет|Да|нет|
|Выполнение запросов PolyBase из средств бизнес-аналитики Майкрософт|Да|нет|Да|Да|   

## <a name="pushdown-computation-supported-by-t-sql-operators"></a>Поддержка передачи вычислений в операторах T-SQL

В SQL Server и APS лишь некоторые операторы T-SQL поддерживают передачу в кластер Hadoop. В следующей таблице приведены все поддерживаемые операторы и ряд неподдерживаемых. 

||||
|-|-|-| 
|**Тип оператора**|**Отправка в Hadoop**|**Отправка в хранилище BLOB-объектов**|
|Проекции столбцов|Да|нет|
|Предикаты|Да|нет|
|Статистические вычисления|Частичный|нет|
|Соединения между внешними таблицами|нет|нет|
|Соединения между внешними и локальными таблицами|нет|нет|
|Сортировки|нет|нет|

Частичное статистическое вычисление означает, что итоговое вычисление должно выполняться после получения данных в SQL Server. Однако часть статистического вычисления происходит в Hadoop. Это стандартный метод вычисления статистических выражений в системах обработки данных с массовым параллелизмом.  

## <a name="known-limitations"></a>Известные ограничения

PolyBase имеет следующие ограничения.

- Чтобы использовать PolyBase, необходимо иметь роль системного администратора или разрешения на управление сервером базы данных.

- Максимальный размер строки, включая полную длину столбцов переменной длины, не может превышать 32 КБ в SQL Server или 1 МБ в хранилище данных SQL Azure.

- При экспорте данных в файл формата ORC из SQL Server или Хранилища данных SQL число столбцов с большим количеством текста может быть ограничено. Их число может даже не превышать 50, что связано с сообщениями об ошибках нехватки памяти Java. Чтобы обойти эту проблему, экспортируйте подмножество столбцов.

- PolyBase не может подключиться к экземпляру Hortonworks, если включена поддержка Knox.

- Если вы используете таблицы Hive с параметром transactional = true, то PolyBase не может обратиться к данным в каталоге таблицы Hive.

<!--SQL Server 2016-->
::: moniker range="= sql-server-2016 || =sqlallproducts-allversions"

- [PolyBase не устанавливается при добавлении узла в отказоустойчивый кластер SQL Server 2016](https://support.microsoft.com/help/3173087/fix-polybase-feature-doesn-t-install-when-you-add-a-node-to-a-sql-server-2016-failover-cluster).

::: moniker-end

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о PolyBase см. в [этом руководстве](polybase-guide.md).
