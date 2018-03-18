---
title: "DBCC SHRINKLOG (хранилище данных SQL Azure) | Документы Майкрософт"
ms.custom: 
ms.date: 07/17/2017
ms.prod: sql-non-specified
ms.prod_service: sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|database-console-commands
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: d06917a784e507ab5568e28b4d34273f5fe71063
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="dbcc-shrinklog-azure-sql-data-warehouse"></a>DBCC SHRINKLOG (хранилище данных SQL Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

Уменьшает размер журнала транзакций *на устройстве* для текущей базы данных [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] или [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]. Для сжатия журнала транзакций данные дефрагментируются. Со временем журнал транзакций базы данных может становиться фрагментированным и неэффективным. Используйте инструкцию DBCC SHRINKLOG, чтобы снизить уровень фрагментации и уменьшить размер журнала.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL (Transact-SQL)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
DBCC SHRINKLOG   
    [ ( SIZE = { target_size [ MB | GB | TB ]  } | DEFAULT ) ]   
    [ WITH NO_INFOMSGS ]   
[;]  
```  
  
## <a name="arguments"></a>Аргументы  
SIZE = { *target_size* [ MB | **GB** | TB ]  } | **DEFAULT**.  
*target_size* — это желательный размер журнала транзакций во всех вычислительных узлах после выполнения инструкции DBCC SHRINKLOG. Значение должно быть целым числом больше 0.  
Размер журнала измеряется в мегабайтах (МБ), гигабайтах (ГБ) или терабайтах (ТБ). Это совокупный размер журнала транзакций во всех вычислительных узлах.  
По умолчанию инструкция DBCC SHRINKLOG уменьшает журнал транзакций до размера, хранящегося в метаданных базы данных. Размер журнала в метаданных определяется параметром LOG_SIZE инструкции [CREATE DATABASE (хранилище данных SQL Azure)](../../t-sql/statements/create-database-azure-sql-data-warehouse.md) или [ALTER DATABASE (хранилище данных SQL Azure)](../../t-sql/statements/alter-database-azure-sql-data-warehouse.md). Инструкция DBCC SHRINKLOG уменьшает журнал транзакций до размера по умолчанию, если указан аргумент `SIZE=DEFAULT` или если отсутствует предложение `SIZE`.
  
WITH NO_INFOMSGS  
Информационные сообщения не выводятся в результатах DBCC SHRINKLOG.  
  
## <a name="permissions"></a>Разрешения  
Требует разрешения ALTER SERVER STATE.
  
## <a name="general-remarks"></a>Общие замечания  
Инструкция DBCC SHRINKLOG не изменяет размер журнала, хранящийся в метаданных базы данных. В метаданных сохраняется значение параметра LOG_SIZE, которое было указано в инструкции CREATE DATABASE или ALTER DATABASE.
  
## <a name="examples-includesssdwincludessssdw-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] и [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
### <a name="a-shrink-the-transaction-log-to-the-original-size-specified-by-create-database"></a>A. Сжатие журнала транзакций до исходного размера, заданного инструкцией CREATE DATABASE  
Предположим, что при создании базы данных Addresses для ее журнала транзакций был задан размер 100 МБ. То есть в инструкции CREATE DATABASE для базы данных Addresses содержался параметр LOG_SIZE = 100 MB. Теперь допустим, что журнал увеличился до 150 МБ и его необходимо снова сжать до 100 МБ.
  
Каждая из приведенных ниже инструкций попытается сжать журнал транзакций для базы данных Addresses до размера по умолчанию, равного 100 МБ. Если сжатие журнала до 100 МБ приведет к потере данных, инструкция DBCC SHRINKLOG сожмет журнал до минимального размера более 100 МБ, который возможен без потери данных.
  
```sql
USE Addresses;  
DBCC SHRINKLOG ( SIZE = 100 MB );  
DBCC SHRINKLOG ( SIZE = DEFAULT );  
DBCC SHRINKLOG;  
```  
  
  
