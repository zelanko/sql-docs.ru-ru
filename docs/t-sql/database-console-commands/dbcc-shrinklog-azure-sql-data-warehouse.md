---
title: DBCC SHRINKLOG (Parallel Data Warehouse) | Документы Майкрософт
ms.custom: ''
ms.date: 03/16/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
author: pmasl
ms.author: umajay
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: d2cf30f4f01a30d8171e58cce3052e45fefa6179
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67930318"
---
# <a name="dbcc-shrinklog-parallel-data-warehouse"></a>DBCC SHRINKLOG (Parallel Data Warehouse)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

Уменьшает размер журнала транзакций *на устройстве* для текущей базы данных [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]. Для сжатия журнала транзакций данные дефрагментируются. Со временем журнал транзакций базы данных может становиться фрагментированным и неэффективным. Используйте инструкцию DBCC SHRINKLOG, чтобы снизить уровень фрагментации и уменьшить размер журнала.
  
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
  
## <a name="examples"></a>Примеры 
### <a name="a-shrink-the-transaction-log-to-the-original-size-specified-by-create-database"></a>A. Сжатие журнала транзакций до исходного размера, заданного инструкцией CREATE DATABASE  
Предположим, что при создании базы данных Addresses для ее журнала транзакций был задан размер 100 МБ. То есть в инструкции CREATE DATABASE для базы данных Addresses содержался параметр LOG_SIZE = 100 MB. Теперь допустим, что журнал увеличился до 150 МБ и его необходимо снова сжать до 100 МБ.
  
Каждая из приведенных ниже инструкций попытается сжать журнал транзакций для базы данных Addresses до размера по умолчанию, равного 100 МБ. Если сжатие журнала до 100 МБ приведет к потере данных, инструкция DBCC SHRINKLOG сожмет журнал до минимального размера более 100 МБ, который возможен без потери данных.
  
```sql
USE Addresses;  
DBCC SHRINKLOG ( SIZE = 100 MB );  
DBCC SHRINKLOG ( SIZE = DEFAULT );  
DBCC SHRINKLOG;  
```  
  
  
