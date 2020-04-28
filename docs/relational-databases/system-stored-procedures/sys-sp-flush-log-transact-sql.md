---
title: sys. sp_flush_log (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_flush_log_TSQL
- sys.sp_flush_log
- sys.sp_flush_log_TSQL
- sp_flush_log
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_flush_log
ms.assetid: 75cc9f52-3b1f-4754-b1e7-ce0dd3323bc9
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 61c4cceab6c816d63226216a54d4f647e92e592d
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68066678"
---
# <a name="syssp_flush_log-transact-sql"></a>sys.sp_flush_log (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Выполняет фиксацию на диск журнала транзакций текущей базы данных, таким образом фиксируя все ранее выполненные отложенные долговечные транзакции.  
  
 Если для улучшения производительности используются отложенные долговечные транзакции, но также необходимо гарантированно ограничить объем данных, теряемый при сбое сервера или отработке отказа, то рекомендуется выполнять `sys.sp_flush_log` по регулярному расписанию. Например, если вы хотите убедиться, что данные не потеряны более чем за x секунд, вы выполните `sp_flush_log` каждые x секунд.  
  
 Выполнение хранимой процедуры `sys.sp_flush_log` гарантирует, что все ранее зафиксированные отложенные устойчивые транзакции будут сделаны долговечными. Дополнительные сведения см. в разделе " [Управление устойчивостью транзакций](../../relational-databases/logs/control-transaction-durability.md) ".  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
  
sys.sp_flush_log  
  
```  
  
#### <a name="parameters"></a>Параметры  
 Отсутствует.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 Код возврата 1 означает успешное завершение.  Все другие значения означают неуспешное завершение.  
  
## <a name="result-sets"></a>Результирующие наборы  
 Отсутствует.  
  
## <a name="sample-code"></a>Образец кода  
  
```sql  
.  
EXECUTE sys.sp_flush_log  
  
```  
  
  
