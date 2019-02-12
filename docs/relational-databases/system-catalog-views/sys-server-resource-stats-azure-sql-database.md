---
title: sys.server_resource_stats (база данных SQL Azure) | Документация Майкрософт
ms.custom: ''
ms.date: 06/28/2018
ms.service: sql-database
ms.reviewer: carlrab, edmaca
ms.topic: language-reference
f1_keywords:
- resource_stats
- sys.resource_stats
- sys.resource_stats_TSQL
- resource_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.resource_stats
- resource_stats
ms.assetid: ''
author: jovanpop-msft
ms.author: jovanpop
manager: craigg
ms.openlocfilehash: b8a5aaa7d0aecd992905e0eaf53ef362f24b1485
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/11/2019
ms.locfileid: "56009656"
---
# <a name="sysserverresourcestats-azure-sql-database"></a>sys.server_resource_stats (база данных SQL Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

Возвращает данные об использовании, операции ввода-ВЫВОДА и хранения ЦП за Azure управляемый экземпляр SQL. Эти данные собираются и объединяются с пятиминутными интервалами. Имеется одна строка для отчетов через каждые 15 секунд. Данные, возвращенные включает использование ЦП, размер хранилища, операций ввода-вывода и управляемого экземпляра SKU. Данные предыстории хранятся приблизительно в течение 14 суток.

**Sys.server_resource_stats** представление имеет разные определения в зависимости от версии управляемого экземпляра Azure SQL, с которой связан базы данных. Рассмотрим эти различия и все изменения, которые требуются приложению при обновлении до новой версии сервера.
 
  
 В следующей таблице описываются столбцы, доступные на сервере v12.  
  
|Столбцы|Тип данных|Описание|  
|----------------------------|---------------|-----------------|  
|start_time|**datetime2**|Время в формате UTC, с которой начинается 15 секундного интервала отчетности|  
|end_time|**datetime**|Время в формате UTC, указывающее окончание 15 секундного интервала отчетности|
|resource_type|nvarchar(128)|Тип ресурса, для которого предоставляются метрики|
|имя_ресурса|nvarchar(128)|Имя ресурса.|
|sku|nvarchar(128)|Уровень служб управляемого экземпляра экземпляра. Допустимы следующие значения: <br><ul><li>Общее назначение</li></ul><ul><li>Критические задачи для бизнеса</li></ul>|
|hardware_generation|nvarchar(128)|Идентификатор поколения оборудования: Gen 4 или 5-го поколений|
|virtual_core_count|ssNoversion|Представляет количество виртуальных ядер на один экземпляр (8, 16 или 24 в общедоступной предварительной версии)|
|avg_cpu_percent|Decimal(5,2)|Среднее использование вычислительных ресурсов в процентах от предела для уровня управляемый экземпляр службы, используемой экземпляром. Он вычисляется как сумма времени ЦП все пулы ресурсов для всех баз данных в экземпляре а деленное доступного времени ЦП для этого уровня в заданном интервале.|
|reserved_storage_mb|BIGINT|Зарезервированные хранилища на экземпляр (объем хранилища пространства этого клиента, приобретенных в управляемом экземпляре)|
|storage_space_used_mb|Decimal(18,2)|Хранилище, используемое файлами все управляемый экземпляр базы данных (включая пользовательских и системных баз данных)|
|io_request|BIGINT|Общее число физических операций ввода-вывода в течение интервала|
|io_bytes_read|BIGINT|Число байтов физической памяти, считанных в течение интервала|
|io_bytes_written|BIGINT|Число байтов физической памяти, записанных в течение интервала|

 
> [!TIP]  
>  Дополнительные сведения об этих ограничениях и уровней обслуживания см. в разделах [уровни служб управляемого экземпляра](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance#managed-instance-service-tier).  
    
## <a name="permissions"></a>Разрешения  
 Это представление доступно для всех ролей пользователей с разрешениями на подключение к **master** базы данных.  
  
## <a name="remarks"></a>Примечания  
 Данные, возвращаемые **sys.server_resource_stats** выражаются как общее число используемых в байтах или мегабайтах (указано в именах столбцов), отличный от avg_cpu, выраженное в процентах от максимально разрешенных ограничений для службы уровня или уровня производительности, которые выполняются.  
 
## <a name="examples"></a>Примеры  
 В следующем примере возвращаются все базы данных с усреднением по меньшей мере для 80 % использования вычислительной мощности за последнюю неделю.  
  
```sql  
DECLARE @s datetime;  
DECLARE @e datetime;  
SET @s= DateAdd(d,-7,GetUTCDate());  
SET @e= GETUTCDATE();  
SELECT resource_name, AVG(avg_cpu_percent) AS Average_Compute_Utilization   
FROM sys.server_resource_stats   
WHERE start_time BETWEEN @s AND @e  
GROUP BY resource_name  
HAVING AVG(avg_cpu_percent) >= 80  
```  
    
## <a name="see-also"></a>См. также  
 [Управляемый экземпляр уровней служб](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance#managed-instance-service-tier)
