---
title: "@@VERSION (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '@@VERSION'
- '@@VERSION_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- '@@VERSION function'
- current SQL Server installation information
- versions [SQL Server], @@VERSION
- processors [SQL Server], types
ms.assetid: 385ba80e-7c28-41a5-9cdb-5648f3785983
caps.latest.revision: 40
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b8367bb24a37996b2956e3107113812a32086fed
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="version---transact-sql-configuration-functions"></a>Версия - Transact SQL функции конфигурации
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает сведения о системе и построении текущей установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
@@VERSION  
```  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **nvarchar**  
  
## <a name="remarks"></a>Замечания  
 @@VERSION Результаты представляются в виде одной строки nvarchar. Можно использовать [SERVERPROPERTY &#40; Transact-SQL &#41; ](../../t-sql/functions/serverproperty-transact-sql.md) функции для получения значений отдельных свойств.  
  
 Для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращаются следующие сведения.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
-   Архитектура процессора  
  
-   Дата сборки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
-   Заявление об авторских правах  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] edition  
  
-   Версия операционной системы  
  
 Для [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] возвращаются следующие сведения.  
  
-   Выпуск — «База данных SQL Windows Azure»  
  
-   Уровень продукта «(CTP)» или «(RTM)»  
  
-   Версия продукта  
  
-   Дата сборки  
  
-   Заявление об авторских правах  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-return-the-current-version-of-includessnoversionincludesssnoversion-mdmd"></a>Ответ возврата текущей версии[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 Следующий код возвращает сведения о версии текущего экземпляра SQL Server.  
  
```  
SELECT @@VERSION AS 'SQL Server Version';  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="b-return-the-current-version-of-includessdwincludesssdw-mdmd"></a>Б. Возвращает текущую версию[!INCLUDE[ssDW](../../includes/ssdw-md.md)]  
  
```  
SELECT @@VERSION AS 'SQL Server PDW Version';  
```  
  
## <a name="see-also"></a>См. также:  
 [SERVERPROPERTY (Transact-SQL)](../../t-sql/functions/serverproperty-transact-sql.md)  
  
  


