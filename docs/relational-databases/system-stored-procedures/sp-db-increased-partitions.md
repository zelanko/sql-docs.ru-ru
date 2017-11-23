---
title: "sp_db_increased_partitions | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_db_increased_partitions_TSQL
- sp_db_increased_partitions
dev_langs: TSQL
helpviewer_keywords: sp_db_increased_partitions
ms.assetid: a8c043ec-b504-4929-ac0e-8babaa99d989
caps.latest.revision: "9"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5266ce8c25465b6fd398111e7fd7e2d6634f5f34
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="spdbincreasedpartitions"></a>sp_db_increased_partitions
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Включает или отключает поддержку до 15 000 секций для указанной базы данных.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
||  
|-|  
|**Применяется к**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] SP2 через [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] SP1 и более поздних версий). Дополнительные сведения см. в разделе [поддержка 15 000 секций в SQL Server 2008 SP2 и SQL Server 2008 R2 SP1](http://go.microsoft.com/fwlink/p/?LinkId=299658),|  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_dp_increased_partitions   
[ @dbname ] = 'database_name'   
[ , [ @increased_partitions = ] 'increased_partitions' ] [;]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @dbname=] '*имя_базы_данных*"  
 Имя базы данных. *DBName* — **sysname** со значением по умолчанию NULL. Если *dbname* не указан, используется текущая база данных.  
  
 [ @increased_partitions=] '*increased_partitions*"  
 Включает или выключает поддержку 15 000 секций для указанной базы данных. *increased_partitions* — **varchar(6)** значение по умолчанию NULL. Для включения поддержки используются значения ON или TRUE, а для выключения — OFF или FALSE. Если *increased_partitions* не указан, процедура возвращает 1, чтобы указать, предназначенного для указанной базы данных, или 0 для указания поддержки отключена.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="permissions"></a>Permissions  
 Необходимо разрешение ALTER DATABASE для указанной базы данных.  
  
  
