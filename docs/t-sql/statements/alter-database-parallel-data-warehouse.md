---
title: ALTER DATABASE (Parallel Data Warehouse) | Документы Майкрософт
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
ms.assetid: 5751656b-7aae-4152-a314-4c631bea4fc4
caps.latest.revision: 10
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 0dd532ce7001c52d9fef2f3fd030fd6cf53e8a77
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="alter-database-parallel-data-warehouse"></a>ALTER DATABASE (Parallel Data Warehouse)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Изменяет параметры максимального размера базы данных для реплицированных таблиц, распределенных таблиц и журнала транзакций в [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]. С помощью этой инструкции можно управлять выделением дискового пространства для базы данных по мере изменения ее размера.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL (Transact-SQL)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Parallel Data Warehouse  
ALTER DATABASE database_name    
    SET ( <set_database_options>   | <db_encryption_option> )  
[;]  
  
<set_database_options> ::=   
{  
    AUTOGROW = { ON | OFF }  
    | REPLICATED_SIZE = size [GB]  
    | DISTRIBUTED_SIZE = size [GB]  
    | LOG_SIZE = size [GB]  
}  
  
<db_encryption_option> ::=  
    ENCRYPTION { ON | OFF }  
```  
  
## <a name="arguments"></a>Аргументы  
 *database_name*  
 Имя изменяемой базы данных. Чтобы получить список баз данных на устройстве, используйте представление [sys.databases (Transact-SQL)](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md).  
  
 AUTOGROW = { ON | OFF }  
 Изменяет значение параметра AUTOGROW. Если параметр AUTOGROW имеет значение ON, [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] автоматически увеличивает пространство, выделенное для реплицированных таблиц, распределенных таблиц и журнала транзакций, в соответствии с растущими требованиями к хранилищу. Если параметр AUTOGROW имеет значение OFF, [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] возвращает ошибку в случае, если размер пространства, занимаемого реплицированными таблицами, распределенными таблицами или журналом транзакций, превышает заданное максимальное значение.  
  
 REPLICATED_SIZE = *размер* [ГБ]  
 Задает для вычислительного узла новый максимальный размер для хранения всех реплицированных таблиц изменяемой базы данных в гигабайтах. Если вы планируете пространство для хранения данных на устройстве, значение REPLICATED_SIZE необходимо умножить на количество вычислительных узлов на устройстве.  
  
 DISTRIBUTED_SIZE = *размер* [ГБ]  
 Задает для базы данных новый максимальный размер для хранения всех распределенных таблиц изменяемой базы данных в гигабайтах. Этот размер распределяется по всем вычислительным узлам на устройстве.  
  
 LOG_SIZE = *размер* [ГБ]  
 Задает для базы данных новый максимальный размер для хранения всех журналов транзакций изменяемой базы данных в гигабайтах. Этот размер распределяется по всем вычислительным узлам на устройстве.  
  
 ENCRYPTION { ON | OFF }  
 Включает шифрование базы данных (ON) или отключает его (OFF). Шифрование можно настроить для [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] только в том случае, если [sp_pdw_database_encryption](http://msdn.microsoft.com/5011bb7b-1793-4b2b-bd9c-d4a8c8626b6e) имеет значение **1**. Перед настройкой прозрачного шифрования данных необходимо создать ключ шифрования базы данных. Дополнительные сведения о шифровании баз данных см. в статье [Прозрачное шифрование данных (TDE)](../../relational-databases/security/encryption/transparent-data-encryption.md).  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение ALTER для базы данных.  
  
## <a name="general-remarks"></a>Общие замечания  
 Значения параметров REPLICATED_SIZE, DISTRIBUTED_SIZE и LOG_SIZE могут быть больше, равны или меньше текущих значений для базы данных.  
  
## <a name="limitations-and-restrictions"></a>Ограничения  
 Операции увеличения и уменьшения размера являются приблизительными. Полученные фактические размеры могут отличаться от значений параметров.  
  
 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] выполняет инструкцию ALTER DATABASE не как атомарную операцию. Если выполнение инструкции прерывается, уже внесенные изменения сохраняются.  
  
## <a name="locking-behavior"></a>Режим блокировки  
 Принимает совмещаемую блокировку для объекта DATABASE. Изменить базу данных, в которой другой пользователь в настоящее время производит операции чтения или записи, невозможно. Это относится и к сеансам, в рамках которых была выполнена инструкция [USE](http://msdn.microsoft.com/158ec56b-b822-410f-a7c4-1a196d4f0e15) для базы данных.  
  
## <a name="performance"></a>Производительность  
 Для сжатия базы данных может требоваться много времени и системных ресурсов в зависимости от фактического размера данных в ней и степени фрагментации на диске. Например, сжатие базы данных может длиться несколько часов.  
  
## <a name="determining-encryption-progress"></a>Определение хода выполнения шифрования  
 Чтобы определить ход выполнения прозрачного шифрования данных в базе данных в процентах, используйте следующий запрос:  
  
```  
WITH  
database_dek AS (  
    SELECT ISNULL(db_map.database_id, dek.database_id) AS database_id,  
        dek.encryption_state, dek.percent_complete,  
        dek.key_algorithm, dek.key_length, dek.encryptor_thumbprint,  
        type  
    FROM sys.dm_pdw_nodes_database_encryption_keys AS dek  
    INNER JOIN sys.pdw_nodes_pdw_physical_databases AS node_db_map  
        ON dek.database_id = node_db_map.database_id   
        AND dek.pdw_node_id = node_db_map.pdw_node_id  
    LEFT JOIN sys.pdw_database_mappings AS db_map  
        ON node_db_map .physical_name = db_map.physical_name  
    INNER JOIN sys.dm_pdw_nodes nodes  
        ON nodes.pdw_node_id = dek.pdw_node_id  
    WHERE dek.encryptor_thumbprint <> 0x  
),  
dek_percent_complete AS (  
    SELECT database_dek.database_id, AVG(database_dek.percent_complete) AS percent_complete  
    FROM database_dek  
    WHERE type = 'COMPUTE'  
    GROUP BY database_dek.database_id  
)  
SELECT DB_NAME( database_dek.database_id ) AS name,  
    database_dek.database_id,  
    ISNULL(  
       (SELECT TOP 1 dek_encryption_state.encryption_state  
        FROM database_dek AS dek_encryption_state  
        WHERE dek_encryption_state.database_id = database_dek.database_id  
        ORDER BY (CASE encryption_state  
            WHEN 3 THEN -1  
            ELSE encryption_state  
            END) DESC), 0)  
        AS encryption_state,  
dek_percent_complete.percent_complete,  
database_dek.key_algorithm, database_dek.key_length, database_dek.encryptor_thumbprint  
FROM database_dek  
INNER JOIN dek_percent_complete   
    ON dek_percent_complete.database_id = database_dek.database_id  
WHERE type = 'CONTROL';  
```  
  
 Подробный пример, демонстрирующий все этапы реализации прозрачного шифрования данных, см. в статье [Прозрачное шифрование данных (TDE)](../../relational-databases/security/encryption/transparent-data-encryption.md).  
  
## <a name="examples-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="a-altering-the-autogrow-setting"></a>A. Изменение параметра AUTOGROW  
 Присвойте параметру AUTOGROW значение ON для базы данных `CustomerSales`.  
  
```  
ALTER DATABASE CustomerSales  
    SET ( AUTOGROW = ON );  
```  
  
### <a name="b-altering-the-maximum-storage-for-replicated-tables"></a>Б. Изменение максимального пространства для хранения реплицированных таблиц  
 В приведенном ниже примере для базы данных `CustomerSales` задается максимальный размер хранилища для реплицированных таблиц, равный 1 ГБ. Это размер хранилища для вычислительного узла.  
  
```  
ALTER DATABASE CustomerSales  
    SET ( REPLICATED_SIZE = 1 GB );  
```  
  
### <a name="c-altering-the-maximum-storage-for-distributed-tables"></a>В. Изменение максимального пространства для хранения распределенных таблиц  
 В приведенном ниже примере для базы данных `CustomerSales` задается максимальный размер хранилища для распределенных таблиц, равный 1000 ГБ (один терабайт). Это совокупный размер хранилища для всех вычислительных узлов на устройстве, а не для отдельных вычислительных узлов.  
  
```  
ALTER DATABASE CustomerSales  
    SET ( DISTRIBUTED_SIZE = 1000 GB );  
```  
  
### <a name="d-altering-the-maximum-storage-for-the-transaction-log"></a>Г. Изменение максимального пространства для хранения журнала транзакций  
 В приведенном ниже примере для базы данных `CustomerSales` на устройстве задается максимальный размер журнала транзакций [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], равный 10 ГБ.  
  
```  
ALTER DATABASE CustomerSales  
    SET ( LOG_SIZE = 10 GB );  
```  
  
## <a name="see-also"></a>См. также:  
 [CREATE DATABASE (Parallel Data Warehouse)](../../t-sql/statements/create-database-parallel-data-warehouse.md)   
 [DROP DATABASE (Transact-SQL)](../../t-sql/statements/drop-database-transact-sql.md)  
  
  
