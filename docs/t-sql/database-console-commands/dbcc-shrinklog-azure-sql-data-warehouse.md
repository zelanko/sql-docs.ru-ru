---
title: "DBCC: параметр (хранилище данных Azure SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/17/2017
ms.prod: sql-non-specified
ms.prod_service: sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|database-console-commands
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
caps.latest.revision: "11"
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: d06917a784e507ab5568e28b4d34273f5fe71063
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="dbcc-shrinklog-azure-sql-data-warehouse"></a>DBCC: параметр (хранилище данных Azure SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

Уменьшает размер журнала транзакций *через устройство* для текущего [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] или [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] базы данных. Данные состояния для сжатия журнала транзакций. Со временем журнал транзакций базы данных может стать фрагментированным и неэффективным. Используйте DBCC: параметр для уменьшения фрагментации и уменьшения размера журнала.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "значок ссылки на раздел") [синтаксические обозначения Transact-SQL &#40; Transact-SQL &#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
DBCC SHRINKLOG   
    [ ( SIZE = { target_size [ MB | GB | TB ]  } | DEFAULT ) ]   
    [ WITH NO_INFOMSGS ]   
[;]  
```  
  
## <a name="arguments"></a>Аргументы  
РАЗМЕР = { *target_size* [МБ | **ГБ** | ТБ]} | **По умолчанию**.  
*target_size* является желаемый размер журнала транзакций по всем узлам вычислений, после завершения команды DBCC: параметр. Он является целым числом больше 0.  
Размер журнала измеряется в мегабайтах (МБ), гигабайт (ГБ) или терабайт (ТБ). Это общий размер журнала транзакций на всех узлах вычислений.  
По умолчанию: параметр DBCC сократить размер журнала, хранящиеся в метаданных для базы данных журнал транзакций. Размер журнала в метаданных определяется параметром LOG_SIZE в [CREATE DATABASE &#40; Хранилище данных Azure SQL &#41; ](../../t-sql/statements/create-database-azure-sql-data-warehouse.md) или [ALTER базы данных &#40; Хранилище данных Azure SQL &#41; ](../../t-sql/statements/alter-database-azure-sql-data-warehouse.md). DBCC: параметр уменьшает размер журнала транзакций по умолчанию размер при `SIZE=DEFAULT` указано, или когда `SIZE` предложение опущено.
  
WITH NO_INFOMSGS  
Информационные сообщения не отображаются в результатах: параметр инструкции DBCC.  
  
## <a name="permissions"></a>Разрешения  
Необходимо разрешение ALTER SERVER STATE.
  
## <a name="general-remarks"></a>Общие замечания  
DBCC: параметр не изменяет размер журнала, хранящиеся в метаданных для базы данных. Метаданные по-прежнему содержать параметр LOG_SIZE, который был указан в инструкции CREATE DATABASE или ALTER DATABASE.
  
## <a name="examples-includesssdwincludessssdw-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
### <a name="a-shrink-the-transaction-log-to-the-original-size-specified-by-create-database"></a>A. Сжатие журнала транзакций до исходного размера, определяемого CREATE DATABASE.  
Предположим, что при создании адреса базы данных журнал транзакций для базы данных адреса было задано значение 100 МБ. То есть инструкции CREATE DATABASE для адреса имели LOG_SIZE = 100 МБ. Предположим, журнала достиг 150 МБ, и вы хотите уменьшить его обратно в 100 МБ.
  
Каждая из следующих инструкций будут пытаться сжатии журнала транзакций для базы данных адресов размер по умолчанию 100 МБ. Если сжатие журнала до 100 МБ приведет к потере данных, инструкция DBCC: параметр сжатия журнала до наименьшего возможного размера, больше 100 МБ, без потери данных.
  
```sql
USE Addresses;  
DBCC SHRINKLOG ( SIZE = 100 MB );  
DBCC SHRINKLOG ( SIZE = DEFAULT );  
DBCC SHRINKLOG;  
```  
  
  
