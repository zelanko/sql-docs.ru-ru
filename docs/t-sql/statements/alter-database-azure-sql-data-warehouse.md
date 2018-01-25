---
title: "ALTER DATABASE (хранилище данных Azure SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: 
ms.prod_service: sql-data-warehouse
ms.reviewer: 
ms.service: sql-data-warehouse
ms.component: t-sql|statements
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
ms.assetid: da712a46-5f8a-4888-9d33-773e828ba845
caps.latest.revision: "20"
author: barbkess
ms.author: barbkess
manager: craigg
ms.openlocfilehash: 71737beb817cfeebed195c90d056768aef678a3e
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="alter-database-azure-sql-data-warehouse"></a>Инструкции ALTER DATABASE (хранилище данных Azure SQL)
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
Имя изменяемой базы данных.  

Параметр MODIFY NAME = *новое_имя_базы_данных*  
Переименование базы данных с именем, указанным в качестве *новое_имя_базы_данных*.  
  
MAXSIZE  
Значение по умолчанию — базе 10240 ГБ (10 ТБ).  

**Применяется к:** оптимизирован для эластичности уровня производительности

Максимально допустимый размер для базы данных. Базы данных не превысит значение MAXSIZE. 

**Применяется к:** , обеспечивающее уровень производительности вычислений

Максимально допустимый размер базы данных rowstore. Данные, хранящиеся в таблицы rowstore deltastore индекс columnstore и некластеризованный индекс в кластеризованный индекс columnstore не может увеличиваться за пределами MAXSIZE.  Данные, сжатые в формате columnstore не имеет ограничение на размер и не ограничивается MAXSIZE. 
  
SERVICE_OBJECTIVE  
Определяет уровень производительности. Дополнительные сведения о цели обслуживания для [!INCLUDE[ssSDW_md](../../includes/sssdw-md.md)], в разделе [уровни производительности](https://azure.microsoft.com/documentation/articles/performance-tiers/).  
  
## <a name="permissions"></a>Разрешения  
Требуются следующие разрешения.  
  
-   Имя входа субъекта серверного уровня (один, созданное процессом подготовки) или  
  
-   Член `dbmanager` роли базы данных.  
  
Владелец базы данных не может изменять базу данных, если владелец не является членом `dbmanager` роли.  
  
## <a name="general-remarks"></a>Общие замечания  
Текущей базы данных должен быть другой базы данных от того, вы изменение, поэтому **ALTER должна запускаться при подключении к базе данных master**.  
  
Хранилище данных SQL имеет значение COMPATIBILITY_LEVEL 130 и не может быть изменено. Дополнительные сведения см. в разделе [повысить производительность запросов с 130 уровень совместимости базы данных SQL Azure](https://azure.microsoft.com/documentation/articles/sql-database-compatibility-level-query-performance-130/).
  
Чтобы уменьшить размер базы данных, используйте [DBCC SHRINKDATABASE](../../t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql.md).  
  
## <a name="limitations-and-restrictions"></a>Ограничения  
Для выполнения инструкции ALTER DATABASE, база данных должна быть в сети и не может быть приостановлена.  
  
Инструкция ALTER DATABASE должна выполняться в режиме автоматической фиксации, который является режим управления транзакциями по умолчанию. Этот параметр задается в параметрах соединения.  
  
Инструкция ALTER DATABASE не может быть частью пользовательской транзакции.

Невозможно изменить параметры сортировки базы данных.  
  
## <a name="examples"></a>Примеры  
Перед выполнением этих примеров, убедитесь, что выбранная база данных изменение не является текущей базы данных. Текущей базы данных должен быть другой базы данных от того, вы изменение, поэтому **ALTER должна запускаться при подключении к базе данных master**.  

### <a name="a-change-the-name-of-the-database"></a>A. Измените имя базы данных  

```  
ALTER DATABASE AdventureWorks2012  
MODIFY NAME = Northwind;  
```  
  
### <a name="b-change-max-size-for-the-database"></a>Б. Изменение максимального размера для базы данных  
  
```  
ALTER DATABASE dw1 MODIFY ( MAXSIZE=10240 GB );  
```  
  
### <a name="c-change-the-performance-level"></a>В. Изменение уровня производительности  
  
```  
ALTER DATABASE dw1 MODIFY ( SERVICE_OBJECTIVE= 'DW1200' );  
```  
  
### <a name="d-change-the-max-size-and-the-performance-level"></a>Г. Изменение максимального размера и уровень производительности  
  
```  
ALTER DATABASE dw1 MODIFY ( MAXSIZE=10240 GB, SERVICE_OBJECTIVE= 'DW1200' );  
```  
  
## <a name="see-also"></a>См. также  
[Создание базы данных (хранилище данных SQL Azure)](../../t-sql/statements/create-database-azure-sql-data-warehouse.md)
[хранилище данных SQL список разделов справки](https://azure.microsoft.com/en-us/documentation/articles/sql-data-warehouse-overview-reference/)  
  
