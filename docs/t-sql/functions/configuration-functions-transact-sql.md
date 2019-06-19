---
title: Функции настройки (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- functions [SQL Server], configuration
- configuration options [SQL Server], functions
- current configuration information
- configuration functions [SQL Server]
ms.assetid: 066f15e7-3406-437e-93c4-3f247c529169
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 687aca13afdca66915e7636b02df209f3e5b5b85
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65943846"
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
  
  
