---
title: ALTER DATABASE (хранилище данных SQL Azure) | Документы Майкрософт
ms.custom: ''
ms.date: 02/15/2018
ms.prod: ''
ms.prod_service: sql-data-warehouse
ms.reviewer: ''
ms.service: sql-data-warehouse
ms.component: t-sql|statements
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: da712a46-5f8a-4888-9d33-773e828ba845
caps.latest.revision: 20
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: 2e89ba1dde52c1b5cb919ff34181d7ca723b6c61
ms.sourcegitcommit: d2573a8dec2d4102ce8882ee232cdba080d39628
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/07/2018
---
# <a name="alter-database-azure-sql-data-warehouse"></a>ALTER DATABASE (хранилище данных SQL Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

Изменяет имя, максимальный размер или цель обслуживания для базы данных.  
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
ALTER DATABASE database_name  

  MODIFY NAME = new_database_name  
| MODIFY ( <edition_option> [, ... n] )  
  
<edition_option> ::=   
      MAXSIZE = { 
            250 | 500 | 750 | 1024 | 5120 | 10240 | 20480 
          | 30720 | 40960 | 51200 | 61440 | 71680 | 81920 
          | 92160 | 102400 | 153600 | 204800 | 245760 
      } GB  
      | SERVICE_OBJECTIVE = { 
            'DW100' | 'DW200' | 'DW300' | 'DW400' | 'DW500' 
          | 'DW600' | 'DW1000' | 'DW1200' | 'DW1500' | 'DW2000' 
          | 'DW3000' | 'DW6000' | 'DW1000c' | 'DW1500c' | 'DW2000c' 
          | 'DW2500c' | 'DW3000c' | 'DW5000c' | 'DW6000c' | 'DW7500c' 
          | 'DW10000c' | 'DW15000c' | 'DW30000c'
      }  
```  
  
## <a name="arguments"></a>Аргументы  
*database_name*  
Задает имя изменяемой базы данных.  

MODIFY NAME = *новое_имя_базы_данных*  
Присваивает базе данных имя, указанное в аргументе *новое_имя_базы_данных*.  
  
MAXSIZE  
Значение по умолчанию — 245 760 ГБ (240 ТБ).  

**Область применения:** уровень производительности "Оптимизация под гибкость"

Максимально допустимый размер базы данных. Размер базы данных не может превышать MAXSIZE. 

**Область применения:** уровень производительности "Оптимизация под вычисление"

Максимально допустимый размер данных rowstore в базе данных. Размер данных, хранящихся в таблицах rowstore, разностном хранилище индекса columnstore или некластеризованном индексе на базе кластеризованного индекса columnstore, не может превышать MAXSIZE.  Данные, сжатые в формат columnstore, не имеют ограничений на размер и не ограничивается значением MAXSIZE. 
  
SERVICE_OBJECTIVE  
Определяет уровень производительности. Дополнительные сведения о целевых уровнях служб для [!INCLUDE[ssSDW_md](../../includes/sssdw-md.md)] см. на странице [Уровни производительности](https://azure.microsoft.com/documentation/articles/performance-tiers/).  
  
## <a name="permissions"></a>Разрешения  
Требуются следующие разрешения:  
  
-   имя входа субъекта серверного уровня, созданное процессом подготовки, или  
  
-   член роли базы данных `dbmanager`.  
  
Владелец базы данных не может изменять базу данных, если он не является членом роли `dbmanager`.  
  
## <a name="general-remarks"></a>Общие замечания  
Текущая база данных должна отличаться от изменяемой, поэтому **инструкцию ALTER следует выполнять при подключении к базе данных master**.  
  
Для хранилища данных SQL задано значение COMPATIBILITY_LEVEL 130, изменить которое невозможно. Дополнительные сведения: [Улучшение производительности запросов с уровнем совместимости 130 в базе данных SQL Azure](https://azure.microsoft.com/documentation/articles/sql-database-compatibility-level-query-performance-130/).
  
Чтобы уменьшить размер базы данных, используйте предложение [DBCC SHRINKDATABASE](../../t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql.md).  
  
## <a name="limitations-and-restrictions"></a>Ограничения  
Для выполнения инструкции ALTER DATABASE база данных должна находиться в сети и не может быть в приостановленном состоянии.  
  
Инструкция ALTER DATABASE должна выполняться в режиме автофиксации, который является режимом управления транзакциями по умолчанию. Он задается в параметрах подключения.  
  
Инструкция ALTER DATABASE не может входить в определенную пользователем транзакцию.

Изменить параметры сортировки базы данных невозможно.  
  
## <a name="examples"></a>Примеры  
Перед выполнением этих примеров убедитесь в том, что изменяемая база данных не является текущей базой данных. Текущая база данных должна отличаться от изменяемой, поэтому **инструкцию ALTER следует выполнять при подключении к базе данных master**.  

### <a name="a-change-the-name-of-the-database"></a>A. Изменение имени базы данных  

```  
ALTER DATABASE AdventureWorks2012  
MODIFY NAME = Northwind;  
```  
  
### <a name="b-change-max-size-for-the-database"></a>Б. Изменение максимального размера базы данных  
  
```  
ALTER DATABASE dw1 MODIFY ( MAXSIZE=10240 GB );  
```  
  
### <a name="c-change-the-performance-level"></a>В. Изменение уровня производительности  
  
```  
ALTER DATABASE dw1 MODIFY ( SERVICE_OBJECTIVE= 'DW1200' );  
```  
  
### <a name="d-change-the-max-size-and-the-performance-level"></a>Г. Изменение максимального размера и уровня производительности  
  
```  
ALTER DATABASE dw1 MODIFY ( MAXSIZE=10240 GB, SERVICE_OBJECTIVE= 'DW1200' );  
```  
  
## <a name="see-also"></a>См. также:  
[CREATE DATABASE (хранилище данных SQL Azure)](../../t-sql/statements/create-database-azure-sql-data-warehouse.md)
[Список разделов справки по хранилищу данных SQL](https://azure.microsoft.com/en-us/documentation/articles/sql-data-warehouse-overview-reference/)  
  
