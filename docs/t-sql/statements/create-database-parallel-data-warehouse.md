---
title: CREATE DATABASE (Parallel Data Warehouse) | Документы Майкрософт
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: pdw
ms.service: ''
ms.component: t-sql|statements
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 40cacde4-ac72-45f7-9564-d76e2b4a741a
caps.latest.revision: 13
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 41ed767a4acd2dbe4b202e94ed054da46810e14a
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="create-database-parallel-data-warehouse"></a>CREATE DATABASE (Parallel Data Warehouse)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Создает новую базу данных на устройстве [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]. Используйте эту инструкцию, чтобы создать все файлы, связанные с базой данных устройства, и задать максимальный размер и параметры автоматического увеличения для таблицы базы данных и журнала транзакций.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL (Transact-SQL)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
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
 Имя новой базы данных. Дополнительные сведения о допустимых именах баз данных см. в разделе "Правила именования объектов" и "Зарезервированные имена базы данных" в статье [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
 AUTOGROW = ON | **OFF**  
 Указывает, будут ли параметры *replicated_size*, *distributed_size* и *log_size* для этой базы данных автоматически увеличиваться по мере необходимости. Значение по умолчанию — **OFF**.  
  
 Если для параметра AUTOGROW установлено значение ON, параметры *replicated_size*, *distributed_size* и *log_size* будут увеличиваться по мере необходимости (не в блоках начального заданного размера) в результате вставки или обновления данных или другого действия, которое требует больше места, чем уже выделено.  
  
 Если для параметра AUTOGROW установлено значение OFF, размеры не будут увеличиваться автоматически. [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] вернет ошибку при попытке выполнения действия, которое требует увеличения значений *replicated_size*, *distributed_size* или *log_size*.  
  
 Параметр AUTOGROW принимает значение ON или OFF для всех размеров. Например, невозможно включить AUTOGROW для *log_size* и отключить для *replicated_size*.  
  
 *replicated_size* [ GB ]  
 Положительное число. Задает размер (в виде целого или десятичного числа гигабайт) всего пространства, выделенного для реплицированных таблиц и соответствующих данных *на каждом вычислительном узле*. Требования к минимальному и максимальному значению *replicated_size* см. в разделе "Минимальные и максимальные значения" в [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
 Если для параметра AUTOGROW установлено значение ON, реплицированные таблицы могут увеличиваться.  
  
 Если для параметра AUTOGROW установлено значение OFF, при попытке пользователя создать новую реплицированную таблицу, вставить данные в существующую реплицированную таблицу или обновить существующую реплицированную таблицу с увеличением значения *replicated_size* будет возвращена ошибка.  
  
 *distributed_size* [ GB ]  
 Положительное число. Размер (в виде целого или десятичного числа гигабайт) всего пространства, выделенного для распределенных таблиц и соответствующих данных *на устройстве*. Требования к минимальному и максимальному значению *distributed_size* см. в разделе "Минимальные и максимальные значения" в статье [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
 Если для параметра AUTOGROW установлено значение ON, распределенные таблицы могут увеличиваться.  
  
 Если для параметра AUTOGROW установлено значение OFF, при попытке пользователя создать новую распределенную таблицу, вставить данные в существующую распределенную таблицу или обновить существующую распределенную таблицу с увеличением значения *distributed_size* будет возвращена ошибка.  
  
 *log_size* [ GB ]  
 Положительное число. Размер (в виде целого или десятичного числа гигабайт) для журнала транзакций *на устройстве*.  
  
 Требования к минимальному и максимальному значению *log_size* см. в разделе "Минимальные и максимальные значения" в статье [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
 Если для параметра AUTOGROW установлено значение ON, файл журнала может увеличиваться в размерах. Используйте инструкцию [DBCC SHRINKLOG (хранилище данных SQL Azure)](../../t-sql/database-console-commands/dbcc-shrinklog-azure-sql-data-warehouse.md), чтобы уменьшить размер файлов журнала до исходного значения.  
  
 Если для параметра AUTOGROW установлено значение OFF, в случае любого действия, которое увеличит размер журнала на отдельном вычислительном узле с превышением значения *log_size*, будет возвращена ошибка.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение **CREATE ANY DATABASE** в базе данных master или членство в предопределенной роли сервера **sysadmin**.  
  
 В следующем примере предоставляется разрешение на создание базы данных для пользователя Fay базы данных.  
  
```  
USE master;  
GO  
GRANT CREATE ANY DATABASE TO [Fay];  
GO  
```  
  
## <a name="general-remarks"></a>Общие замечания  
 Базы данных создаются с уровнем совместимости базы данных 120, который является уровнем совместимости для [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]. Это гарантирует, что база данных сможет использовать все функции [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], которые использует PDW.  
  
## <a name="limitations-and-restrictions"></a>Ограничения  
 Инструкция CREATE DATABASE не разрешена в явных транзакциях. Дополнительные сведения см. в разделе [Инструкции](../../t-sql/statements/statements.md).  
  
 Сведения о минимальных и максимальных ограничениях для базы данных см. в разделе "Минимальные и максимальные значения" в статье [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)].  
  
 Во время создания базы данных должно быть достаточно свободного места *на каждом вычислительном узле* для распределения общей суммы следующих размеров:  
  
-   База данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с таблицами со значением размера *replicated_table_size*.  
  
-   База данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с таблицами со значением размера (*distributed_table_size* / количество вычислительных узлов).  
  
-   Журналы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] со значением размера (*log_size* / количество вычислительных узлов).  
  
## <a name="locking"></a>Блокировка  
 Принимает совмещаемую блокировку для объекта DATABASE.  
  
## <a name="metadata"></a>Метаданные  
 После успешного завершения этой операции запись для этой базы данных будет отображаться в представлениях метаданных [sys.databases (Transact-SQL)](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) и [sys.objects (Transact-SQL)](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md).  
  
## <a name="examples-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="a-basic-database-creation-examples"></a>A. Примеры создания базовых баз данных  
 В следующем примере создается база данных `mytest` с выделением 100 ГБ на вычислительный узел для реплицированных таблиц, 500 ГБ на устройство для распределенных таблиц и 100 ГБ на устройство для журнала транзакций. В этом примере параметр AUTOGROW отключен по умолчанию.  
  
```  
CREATE DATABASE mytest  
   WITH   
   (REPLICATED_SIZE = 100 GB,  
   DISTRIBUTED_SIZE = 500 GB,  
   LOG_SIZE = 100 GB );  
```  
  
 В следующем примере создается база данных `mytest` с указанными выше параметрами, но AUTOGROW включен. Это позволяет базе данных увеличиваться и превышать указанные значения размера.  
  
```  
CREATE DATABASE mytest  
   WITH   
   (AUTOGROW = ON,  
   REPLICATED_SIZE = 100 GB,  
   DISTRIBUTED_SIZE = 500 GB,  
   LOG_SIZE = 100 GB);  
```  
  
### <a name="b-creating-a-database-with-partial-gigabyte-sizes"></a>Б. Создание базы данных с десятичным числом гигабайт  
 В следующем примере создается база данных `mytest` с отключенным параметром AUTOGROW, с выделением 1,5 ГБ на вычислительный узел для реплицированных таблиц, 5,25 ГБ на устройство для распределенных таблиц и 10 ГБ на устройство для журнала транзакций.  
  
```  
CREATE DATABASE mytest  
   WITH   
   (REPLICATED_SIZE = 1.5 GB,  
   DISTRIBUTED_SIZE = 5.25 GB,  
   LOG_SIZE = 10 GB);  
```  
  
## <a name="see-also"></a>См. также:  
 [ALTER DATABASE (Parallel Data Warehouse)](../../t-sql/statements/alter-database-parallel-data-warehouse.md)   
 [DROP DATABASE (Transact-SQL)](../../t-sql/statements/drop-database-transact-sql.md)  
  
  
