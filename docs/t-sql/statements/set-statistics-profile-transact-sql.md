---
title: SET STATISTICS PROFILE (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: t-sql|statements
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- PROFILE
- SET_STATISTICS_PROFILE_TSQL
- PROFILE_TSQL
- SET STATISTICS PROFILE
dev_langs:
- TSQL
helpviewer_keywords:
- profiles [SQL Server], displaying
- statements [SQL Server], profile information
- SET STATISTICS PROFILE statement
- STATISTICS PROFILE option
- statistical information [SQL Server], profiles
ms.assetid: c635e262-35fa-421a-aa6f-a1c30f351647
caps.latest.revision: 34
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 6494f792c1dcfbb92bfe48d3063df533d0ff1510
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="set-statistics-profile-transact-sql"></a>SET STATISTICS PROFILE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Выводит сведения о профиле для инструкции. Параметр STATISTICS PROFILE предназначен для нерегламентированных запросов, представлений и хранимых процедур.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SET STATISTICS PROFILE { ON | OFF }  
```  
  
## <a name="remarks"></a>Remarks  
 Если параметру STATISTICS PROFILE присвоено значение ON, каждый исполняемый запрос возвращает обычный результирующий набор, за которым следует дополнительный результирующий набор, отображающий профиль выполнения запроса.  
  
 Дополнительный результирующий набор содержит столбцы SHOWPLAN_ALL для запроса, а также следующие дополнительные столбцы.  
  
|Имя столбца|Description|  
|-----------------|-----------------|  
|**Строки**|Фактическое количество строк, созданных каждым оператором.|  
|**Executes**|Количество выполнений каждого оператора.|  
  
## <a name="permissions"></a>Разрешения  
 Для запуска инструкции SET STATISTICS PROFILE и просмотра данных пользователи должны иметь следующие разрешения:  
  
-   соответствующие разрешения на выполнение инструкций языка [!INCLUDE[tsql](../../includes/tsql-md.md)];  
  
-   разрешение SHOWPLAN на все базы данных, содержащие объекты, на которые ссылаются инструкции языка [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 Для инструкций языка [!INCLUDE[tsql](../../includes/tsql-md.md)], которые не выводят результирующие наборы STATISTICS PROFILE, требуются только соответствующие разрешения на выполнение инструкций языка [!INCLUDE[tsql](../../includes/tsql-md.md)]. Для инструкций языка [!INCLUDE[tsql](../../includes/tsql-md.md)], которые выводят результирующие наборы STATISTICS PROFILE, должны успешно выполняться проверки как разрешения для выполнения инструкций языка [!INCLUDE[tsql](../../includes/tsql-md.md)], так и разрешения SHOWPLAN. Иначе выполнение инструкции языка [!INCLUDE[tsql](../../includes/tsql-md.md)] прекращается и сведения Showplan не формируются.  
  
## <a name="see-also"></a>См. также:  
 [Инструкции SET (Transact-SQL)](../../t-sql/statements/set-statements-transact-sql.md)   
 [SET SHOWPLAN_ALL (Transact-SQL)](../../t-sql/statements/set-showplan-all-transact-sql.md)   
 [SET STATISTICS TIME (Transact-SQL)](../../t-sql/statements/set-statistics-time-transact-sql.md)   
 [SET STATISTICS IO (Transact-SQL)](../../t-sql/statements/set-statistics-io-transact-sql.md)  
  
  
