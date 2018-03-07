---
title: "ALTER DATABASE (Parallel Data Warehouse) | Документы Microsoft"
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
ms.assetid: 5751656b-7aae-4152-a314-4c631bea4fc4
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7db44d9c9f02618e4d95a9d3eb9dfc581438dea5
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="alter-database-parallel-data-warehouse"></a>Инструкции ALTER DATABASE (параллельное хранилище данных)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Изменяет параметры максимальный размер для реплицированных таблиц, распределенных таблиц и журнала транзакций в [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]. Эта инструкция предназначена для управления выделение места на диске для базы данных, как его при увеличении или уменьшении размера.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "значок ссылки на раздел") [синтаксические обозначения Transact-SQL &#40; Transact-SQL &#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
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
 Имя изменяемой базы данных. Чтобы отобразить список баз данных на устройстве, используйте [sys.databases &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md).  
  
 АВТОМАТИЧЕСКОЕ УВЕЛИЧЕНИЕ = {ON | {OFF}  
 Обновляет параметр автоматического УВЕЛИЧЕНИЯ. Если автоматическое УВЕЛИЧЕНИЕ имеет значение ON, [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] автоматически увеличивается место, выделяемое для реплицированных таблиц, распределенных таблиц и журнала транзакций при необходимости для роста в требования к хранилищу. Если автоматическое УВЕЛИЧЕНИЕ имеет значение OFF, [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] возвращает ошибку, если в реплицированных таблицах, распределенные таблицы или превышает максимальный размер журнала транзакций.  
  
 REPLICATED_SIZE = *размер* [ГБ]  
 Задает новый максимальный гигабайт в вычислительном узле для хранения всех реплицированных таблиц в базе данных изменения. При планировании дискового пространства устройства необходимо умножить REPLICATED_SIZE количество вычислительных узлов в устройстве.  
  
 DISTRIBUTED_SIZE = *размер* [ГБ]  
 Задает новый максимальный гигабайт в базу данных для хранения всех распределенных таблиц в базе данных изменения. Размер распределяется по всем вычислительных узлов в устройстве.  
  
 LOG_SIZE = *size* [GB]  
 Задает новый максимальный гигабайт в базу данных для хранения всех журналов транзакций в базе данных изменения. Размер распределяется по всем вычислительных узлов в устройстве.  
  
 ШИФРОВАНИЕ {ON | {OFF}  
 Включает шифрование базы данных (ON) или отключает его (OFF). Шифрование можно задавать только для [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] при [sp_pdw_database_encryption](http://msdn.microsoft.com/5011bb7b-1793-4b2b-bd9c-d4a8c8626b6e) ему было присвоено **1**. Ключ шифрования базы данных должны создаваться, прежде чем можно будет настроить прозрачное шифрование данных. Дополнительные сведения о шифровании баз данных см. в разделе [прозрачное шифрование данных &#40; Прозрачное шифрование данных &#41; ](../../relational-databases/security/encryption/transparent-data-encryption.md).  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение ALTER на базу данных.  
  
## <a name="general-remarks"></a>Общие замечания  
 Значения REPLICATED_SIZE, DISTRIBUTED_SIZE и LOG_SIZE может быть больше, равно или меньше, чем текущие значения для базы данных.  
  
## <a name="limitations-and-restrictions"></a>Ограничения  
 Увеличение и операции сжатия являются приблизительными. Полученный фактическими размерами могут отличаться от параметров размера.  
  
 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]не выполняет инструкцию ALTER DATABASE в виде атомарной операции. Если инструкция прервана во время выполнения, изменения, произошедшие уже останется.  
  
## <a name="locking-behavior"></a>Режим блокировки  
 Принимает совмещаемую блокировку для объекта базы данных. Невозможно изменить базу данных, уже используется другим пользователем для чтения или записи. Сюда входят сеансы, которые выданы [используйте](http://msdn.microsoft.com/158ec56b-b822-410f-a7c4-1a196d4f0e15) инструкцию в базе данных.  
  
## <a name="performance"></a>Производительность  
 Сжатие базы данных может занять много времени и ресурсов системы, в зависимости от размера фактических данных в базе данных и степени фрагментации диска. Например сжатие базы данных может занять несколько часов или более.  
  
## <a name="determining-encryption-progress"></a>Определение хода выполнения шифрования  
 Чтобы определить ход работы базы данных прозрачного шифрования данных в процентах, используйте следующий запрос:  
  
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
  
 Подробный пример, демонстрирующий все этапы реализации прозрачного шифрования данных, в разделе [прозрачное шифрование данных &#40; Прозрачное шифрование данных &#41; ](../../relational-databases/security/encryption/transparent-data-encryption.md).  
  
## <a name="examples-includesspdwincludessspdw-mdmd"></a>Примеры:[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="a-altering-the-autogrow-setting"></a>A. Изменение параметров АВТОРАСШИРЕНИЯ  
 Установите АВТОУВЕЛИЧЕНИЕ в значение ON для базы данных `CustomerSales`.  
  
```  
ALTER DATABASE CustomerSales  
    SET ( AUTOGROW = ON );  
```  
  
### <a name="b-altering-the-maximum-storage-for-replicated-tables"></a>Б. Изменение максимальный объем хранилища для реплицированных таблиц  
 В следующем примере задается ограничение хранилища реплицируемой таблицы до 1 ГБ для базы данных `CustomerSales`. Это ограничение хранилища вычислительных узлов.  
  
```  
ALTER DATABASE CustomerSales  
    SET ( REPLICATED_SIZE = 1 GB );  
```  
  
### <a name="c-altering-the-maximum-storage-for-distributed-tables"></a>В. Изменение максимальный объем хранилища для распределенных таблиц  
 В следующем примере задается таблица распространения предельный размер хранилища для 1000 ГБ (один терабайт) для базы данных `CustomerSales`. Это ограничение объединенный хранилища через устройства для всех вычислительных узлов не ограничение хранилища вычислительных узлов.  
  
```  
ALTER DATABASE CustomerSales  
    SET ( DISTRIBUTED_SIZE = 1000 GB );  
```  
  
### <a name="d-altering-the-maximum-storage-for-the-transaction-log"></a>Г. Изменение максимальный объем хранилища для журнала транзакций  
 В следующем примере обновляется база данных `CustomerSales` максимум [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] размер журнала транзакций до 10 ГБ для устройства.  
  
```  
ALTER DATABASE CustomerSales  
    SET ( LOG_SIZE = 10 GB );  
```  
  
## <a name="see-also"></a>См. также  
 [Создание базы данных &#40; Параллельное хранилище данных &#41;](../../t-sql/statements/create-database-parallel-data-warehouse.md)   
 [DROP DATABASE (Transact-SQL)](../../t-sql/statements/drop-database-transact-sql.md)  
  
  
