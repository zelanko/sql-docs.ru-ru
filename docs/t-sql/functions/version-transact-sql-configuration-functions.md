---
title: "@@VERSION (Transact-SQL) | Документы Майкрософт"
ms.custom: 
ms.date: 09/18/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
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
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 9f2a03af933d739760944f72aaea935e8bb3e682
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="x40x40version---transact-sql-configuration-functions"></a>&#x40;&#x40;Version — функции настройки Transact SQL
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает сведения о системе и построении текущей установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
@@VERSION  
```  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **nvarchar**  
  
## <a name="remarks"></a>Remarks  
 Результаты функции @@VERSION представлены как одна строка типа nvarchar. Для получения значений отдельных свойств можно использовать функцию [SERVERPROPERTY (Transact-SQL)](../../t-sql/functions/serverproperty-transact-sql.md).  
  
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
  
### <a name="a-return-the-current-version-of-includessnoversionincludesssnoversion-mdmd"></a>А. Получение текущей версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 Следующий код возвращает сведения о версии текущего экземпляра SQL Server.  
  
```  
SELECT @@VERSION AS 'SQL Server Version';  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="b-return-the-current-version-of-includessdwincludesssdw-mdmd"></a>Б. Получение текущей версии [!INCLUDE[ssDW](../../includes/ssdw-md.md)]  
  
```  
SELECT @@VERSION AS 'SQL Server PDW Version';  
```  
  
## <a name="see-also"></a>См. также:  
 [SERVERPROPERTY (Transact-SQL)](../../t-sql/functions/serverproperty-transact-sql.md)  
  
  

