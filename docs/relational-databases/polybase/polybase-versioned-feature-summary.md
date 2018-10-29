---
title: Возможности и ограничения PolyBase | Документация Майкрософт
ms.custom: ''
ms.date: 09/24/2018
ms.prod: sql
ms.technology: polybase
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 6591994d-6109-4285-9c5b-ecb355f8a111
author: rothja
ms.author: jroth
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 8f7520a4e9bdc346113e4777bd6899f5ccc0e01c
ms.sourcegitcommit: ef78cc196329a10fc5c731556afceaac5fd4cb13
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2018
ms.locfileid: "49460319"
---
# <a name="polybase-features-and-limitations"></a>Возможности и ограничения PolyBase

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

## <a name="known-limitations"></a>Известные ограничения

PolyBase имеет следующие ограничения.

- Максимальный размер строки, включая полную длину столбцов переменной длины, не может превышать 32 МБ в SQL Server или 1 МБ в хранилище данных Azure SQL.

- PolyBase не поддерживает типы данных Hive 0.12+ (например, Char(), VarChar()).

- При экспорте данных в формате файлов ORC из SQL Server или хранилища данных SQL Azure столбцы с большим объемом текста могут ограничиваться всего 50 столбцами из-за ошибок нехватки памяти в Java. Чтобы обойти эту проблему, экспортируйте подмножество столбцов.

- Не удается прочесть или записать данные, зашифрованные в местах хранения в Hadoop. Сюда входят зашифрованные зоны HDFS или прозрачное шифрование.

- PolyBase не может подключиться к экземпляру Hortonworks, если включена поддержка KNOX.

- Если вы используете таблицы Hive с параметром transactional, равным true, PolyBase не имеет доступа к данным в каталоге таблицы Hive.

<!--SQL Server 2016-->
::: moniker range="= sql-server-2016 || =sqlallproducts-allversions"

- [PolyBase не устанавливается при добавлении узла в отказоустойчивый кластер SQL Server 2016](https://support.microsoft.com/en-us/help/3173087/fix-polybase-feature-doesn-t-install-when-you-add-a-node-to-a-sql-server-2016-failover-cluster)

::: moniker-end

- Встроенная проверка подлинности не поддерживается. Сейчас поддерживаются только имя пользователя и пароль.  

- Шифрование включено по умолчанию.

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о PolyBase см. в [этом руководстве](polybase-guide.md).
