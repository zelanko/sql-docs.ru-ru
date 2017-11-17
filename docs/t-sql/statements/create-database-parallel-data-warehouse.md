---
title: "Создание базы данных (Parallel Data Warehouse) | Документы Microsoft"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 40cacde4-ac72-45f7-9564-d76e2b4a741a
caps.latest.revision: 13
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 52a55d6c275388e03e3f7be09d265a3b918f583f
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="create-database-parallel-data-warehouse"></a>Создание базы данных (параллельное хранилище данных)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Создает новую базу данных на [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] устройства. Эта инструкция предназначена для создания все файлы, связанные с базой данных устройства и задать максимальный размер и параметры автоматическое увеличение таблицы базы данных и журнала транзакций.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "значок ссылки на раздел") [синтаксические обозначения Transact-SQL &#40; Transact-SQL &#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
CREATE DATABASE database_name   
WITH (   
    [ AUTOGROW = ON | OFF , ]   
    REPLICATED_SIZE = replicated_size [ GB ] ,  
    DISTRIBUTED_SIZE = distributed_size [ GB ] ,  
    LOG_SIZE = log_size [ GB ] )  
[;]  
```  
  
## <a name="arguments"></a>Аргументы  
 *database_name*  
 Имя новой базы данных. Дополнительные сведения о имена разрешенных баз данных см. в разделе «Правила именования объектов» и «Зарезервированные имена базы данных» в [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
 АВТОМАТИЧЕСКОЕ УВЕЛИЧЕНИЕ = ON | **OFF**  
 Указывает, является ли *replicated_size*, *distributed_size*, и *log_size* параметры для этой базы данных автоматически будет увеличиваться по мере необходимости за пределами их указанного размеры. Значение по умолчанию — **OFF**.  
  
 Если автоматическое РАСШИРЕНИЕ включено *replicated_size*, *distributed_size*, и *log_size* будет увеличиваться как с каждой вставки данных обязательно (а не в блоки заданного начального размера) обновление или другое действие, требует меньше места, чем уже выделен.  
  
 Если АВТОУВЕЛИЧЕНИЕ отключено, размеры не будет увеличиваться автоматически. [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]Возвращает ошибку при попытке действие, требующее *replicated_size*, *distributed_size*, или *log_size* увеличение их указанное значение.  
  
 Автоматическое УВЕЛИЧЕНИЕ является ON для всех размеров или OFF для всех размеров. Например, не невозможно присвоить значение ON АВТОУВЕЛИЧЕНИЕ для *log_size*, но не задано его для *replicated_size*.  
  
 *replicated_size* [ГБ]  
 Положительное число. Задает размер (в гигабайтах целого или десятичного) для свободное место, выделенное для реплицированных таблиц и соответствующие данные *на каждом вычислительном узле*. Для максимального и минимального *replicated_size* требования, см. в «Минимальное и максимальное значения» в [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
 Если автоматическое РАСШИРЕНИЕ включено, реплицированные таблицы будет разрешено превысит это ограничение.  
  
 Если автоматическое РАСШИРЕНИЕ установлено в OFF, возвращается ошибка при попытке создания новой реплицируемой таблицы, вставка данных в существующей репликации таблицы или обновляет существующую реплицированная таблица таким образом, чтобы увеличит размер за пределы *replicated_size*.  
  
 *distributed_size* [ГБ]  
 Положительное число. Размер в гигабайтах целого или десятичного, для свободное место, выделенное для распределенных таблицы (и соответствующие данные) *через устройство*. Для максимального и минимального *distributed_size* требования, см. в «Минимальное и максимальное значения» в [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
 Если включено автоматическое УВЕЛИЧЕНИЕ, распределенных таблиц будет разрешено превысит это ограничение.  
  
 Если АВТОУВЕЛИЧЕНИЕ отключено, если пользователь пытается создать новую таблицу распределенной, вставки данных в существующей распределенной таблицы или обновление существующей распределенной таблицы таким образом, чтобы увеличит размер за пределами будет возвращена ошибка *distributed_size* .  
  
 *log_size* [ГБ]  
 Положительное число. Размер (в гигабайтах целого или десятичного) для журнала транзакций *через устройство*.  
  
 Для максимального и минимального *log_size* требования, см. в «Минимальное и максимальное значения» в [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
 Если АВТОУВЕЛИЧЕНИЕ имеет значение ON, файл журнала разрешается превысит это ограничение. Используйте [: параметр DBCC (хранилище данных SQL Azure)](../../t-sql/database-console-commands/dbcc-shrinklog-azure-sql-data-warehouse.md) инструкцию, чтобы уменьшить размер файлов журнала до их исходного размера.  
  
 Если АВТОУВЕЛИЧЕНИЕ отключено, будет возвращена ошибка пользователю для любое действие, которое будет увеличить размер журнала в отдельных вычислительном узле за *log_size*.  
  
## <a name="permissions"></a>Permissions  
 Требуется **CREATE ANY DATABASE** разрешение в базе данных master или членство в группе **sysadmin** предопределенной роли сервера.  
  
 В следующем примере предоставляется разрешение на создание базы данных для пользователя Fay базы данных.  
  
```  
USE master;  
GO  
GRANT CREATE ANY DATABASE TO [Fay];  
GO  
```  
  
## <a name="general-remarks"></a>Общие замечания  
 Создаются базы данных с уровнем совместимости базы данных 120, который является совместимости уровня для [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]. Это гарантирует, что база данных будет использовать все [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] функциональность, использующую PDW.  
  
## <a name="limitations-and-restrictions"></a>Ограничения  
 Инструкция CREATE DATABASE не допускается в явной транзакции. Дополнительные сведения см. в разделе [инструкции](../../t-sql/statements/statements.md).  
  
 Сведения о минимальные и максимальные ограничения для базы данных, в разделе «Минимальное и максимальное значения» в [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
 Во время создания базы данных, должны быть недостаточно свободного места *на каждом вычислительном узле* для распределения всего следующие размеры:  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]размер базы данных с таблицами из *replicated_table_size*.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]базы данных с таблицами, размер (*distributed_table_size* / число вычислительных узлов).  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Регистрирует размер (*log_size* / число вычислительных узлов).  
  
## <a name="locking"></a>Блокировка  
 Принимает совмещаемую блокировку для объекта базы данных.  
  
## <a name="metadata"></a>Метаданные  
 После этого операция завершилась успешно, запись для этой базы данных будет отображаться в [sys.databases &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) и [sys.objects &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)метаданные представления.  
  
## <a name="examples-includesspdwincludessspdw-mdmd"></a>Примеры:[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="a-basic-database-creation-examples"></a>A. Примеры создания баз данных Basic  
 В следующем примере создается база данных `mytest` с выделением 100 ГБ на вычислительном узле для реплицированных таблиц, 500 ГБ на устройство для распределенных таблиц и 100 ГБ на устройство для журнала транзакций. В этом примере АВТОУВЕЛИЧЕНИЕ отключено по умолчанию.  
  
```  
CREATE DATABASE mytest  
   WITH   
   (REPLICATED_SIZE = 100 GB,  
   DISTRIBUTED_SIZE = 500 GB,  
   LOG_SIZE = 100 GB );  
```  
  
 В следующем примере создается база данных `mytest` с теми же параметрами, как описано выше, за исключением АВТОУВЕЛИЧЕНИЕ включен. Это позволяет рост за пределами параметров указанного размера базы данных.  
  
```  
CREATE DATABASE mytest  
   WITH   
   (AUTOGROW = ON,  
   REPLICATED_SIZE = 100 GB,  
   DISTRIBUTED_SIZE = 500 GB,  
   LOG_SIZE = 100 GB);  
```  
  
### <a name="b-creating-a-database-with-partial-gigabyte-sizes"></a>Б. Создание базы данных с размерами частичного ГБ  
 В следующем примере создается база данных `mytest`с АВТОУВЕЛИЧЕНИЕ off, выделение хранилища 1,5 ГБ на вычислительном узле для реплицированных таблиц, 5,25 ГБ на устройство для распределенных таблиц и 10 ГБ на устройство для журнала транзакций.  
  
```  
CREATE DATABASE mytest  
   WITH   
   (REPLICATED_SIZE = 1.5 GB,  
   DISTRIBUTED_SIZE = 5.25 GB,  
   LOG_SIZE = 10 GB);  
```  
  
## <a name="see-also"></a>См. также:  
 [ALTER DATABASE &#40; Параллельное хранилище данных &#41;](../../t-sql/statements/alter-database-parallel-data-warehouse.md)   
 [DROP DATABASE (Transact-SQL)](../../t-sql/statements/drop-database-transact-sql.md)  
  
  

