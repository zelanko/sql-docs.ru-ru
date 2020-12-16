---
description: DBCC SHRINKLOG (Parallel Data Warehouse)
title: DBCC SHRINKLOG (Parallel Data Warehouse)
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
monikerRange: '>= aps-pdw-2016'
ms.openlocfilehash: 58bda1e035c25ae373fef14bfb574a6f2c139835
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97480425"
---
# <a name="dbcc-shrinklog-parallel-data-warehouse"></a>DBCC SHRINKLOG (Parallel Data Warehouse)

[!INCLUDE [pdw](../../includes/applies-to-version/pdw.md)]

Уменьшает размер журнала транзакций *на устройстве* для текущей базы данных [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]. Для сжатия журнала транзакций данные дефрагментируются. Со временем журнал транзакций базы данных может становиться фрагментированным и неэффективным. Используйте инструкцию DBCC SHRINKLOG, чтобы снизить уровень фрагментации и уменьшить размер журнала.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL &#40;Transact-SQL&#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```syntaxsql
DBCC SHRINKLOG   
    [ ( SIZE = { target_size [ MB | GB | TB ]  } | DEFAULT ) ]   
    [ WITH NO_INFOMSGS ]   
[;]  
```  

## <a name="arguments"></a>Аргументы

SIZE = { *target_size* [ MB \| **GB** \| TB ]  } \| **DEFAULT**.  
*target_size* — это желательный размер журнала транзакций во всех вычислительных узлах после выполнения инструкции DBCC SHRINKLOG. Значение должно быть целым числом больше 0.  
Размер журнала измеряется в мегабайтах (МБ), гигабайтах (ГБ) или терабайтах (ТБ). Это совокупный размер журнала транзакций во всех вычислительных узлах.  
По умолчанию инструкция DBCC SHRINKLOG уменьшает журнал транзакций до размера, хранящегося в метаданных базы данных. Размер журнала в метаданных определяется параметром LOG_SIZE инструкции [CREATE DATABASE &#40;Azure Synapse Analytics&#41;](../statements/create-database-transact-sql.md) или [ALTER DATABASE &#40;Azure Synapse Analytics&#41;](../statements/alter-database-transact-sql.md). Инструкция DBCC SHRINKLOG уменьшает журнал транзакций до размера по умолчанию, если указан аргумент `SIZE=DEFAULT` или если отсутствует предложение `SIZE`.
  
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