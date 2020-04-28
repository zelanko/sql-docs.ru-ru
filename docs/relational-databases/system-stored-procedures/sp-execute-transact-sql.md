---
title: sp_execute (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_cursor_execute
- sp_cursor_execute_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_execute
ms.assetid: 2009acd3-0d92-435a-a8fb-057e50dc7146
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 1957103cf2c817f0ef77816446be5fb2d352c9d6
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68124464"
---
# <a name="sp_execute-transact-sql"></a>sp_execute (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Выполняет подготовленную [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкцию, используя указанный маркер и необязательное значение параметра. sp_execute вызывается путем указания ID = 12 в пакете потока табличных данных (TDS).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Syntax for SQL Server, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
sp_execute handle OUTPUT  
    [,bound_param  ]  [,...n ]  ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *справиться*  
 Значение *обработчика* , возвращаемое sp_prepare. *Handle* является обязательным параметром, который вызывает входное значение **int** .  
  
 *bound_param*  
 Означает использование дополнительных параметров. *bound_param* является обязательным параметром, который вызывает входные значения любого типа данных для обозначения дополнительных параметров процедуры.  
  
> [!NOTE]  
>  *bound_param* должны соответствовать объявлениям, сделанным значением sp_prepare*params* , и может иметь вид * @name = значение* или *значение*.  
  
## <a name="see-also"></a>См. также:  
 [Системные хранимые процедуры &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [sp_prepare &#40;Transact SQL&#41;](../../relational-databases/system-stored-procedures/sp-prepare-transact-sql.md)  
  
  
