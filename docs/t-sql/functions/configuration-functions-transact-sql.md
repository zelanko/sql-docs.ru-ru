---
title: Функции настройки (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- functions [SQL Server], configuration
- configuration options [SQL Server], functions
- current configuration information
- configuration functions [SQL Server]
ms.assetid: 066f15e7-3406-437e-93c4-3f247c529169
caps.latest.revision: 30
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 7333af5d9e0d3a36dfda7d81e6292bfe7a89dc09
ms.sourcegitcommit: 05e18a1e80e61d9ffe28b14fb070728b67b98c7d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/04/2018
ms.locfileid: "37784435"
---
# <a name="configuration-functions-transact-sql"></a>Функции конфигурации (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Эти скалярные функции возвращают сведения о текущих значениях параметров конфигурации:
  
|||  
|-|-|  
|[@@DATEFIRST](../../t-sql/functions/datefirst-transact-sql.md)|[@@OPTIONS](../../t-sql/functions/options-transact-sql.md)|  
|[@@DBTS](../../t-sql/functions/dbts-transact-sql.md)|[@@REMSERVER](../../t-sql/functions/remserver-transact-sql.md)|  
|[@@LANGID](../../t-sql/functions/langid-transact-sql.md)|[@@SERVERNAME](../../t-sql/functions/servername-transact-sql.md)|  
|[@@LANGUAGE](../../t-sql/functions/language-transact-sql.md)|[@@SERVICENAME](../../t-sql/functions/servicename-transact-sql.md)|  
|[@@LOCK_TIMEOUT](../../t-sql/functions/lock-timeout-transact-sql.md)|[@@SPID](../../t-sql/functions/spid-transact-sql.md)|  
|[@@MAX_CONNECTIONS](../../t-sql/functions/max-connections-transact-sql.md)|[@@TEXTSIZE](../../t-sql/functions/textsize-transact-sql.md)|  
|[@@MAX_PRECISION](../../t-sql/functions/max-precision-transact-sql.md)|[@@VERSION](../../t-sql/functions/version-transact-sql-configuration-functions.md)|  
|[@@NESTLEVEL](../../t-sql/functions/nestlevel-transact-sql.md)||  
  
Все функции конфигурации являются недетерминированными. Это означает, что такие функции не всегда возвращают одинаковые значения при каждом вызове, даже при одинаковых наборах входных значений. Дополнительные сведения о детерминированности функций см. в статье [Детерминированные и недетерминированные функции](../../relational-databases/user-defined-functions/deterministic-and-nondeterministic-functions.md).
  
## <a name="see-also"></a>См. также раздел
[Функции (Transact-SQL)](../../t-sql/functions/functions.md)
  
  
