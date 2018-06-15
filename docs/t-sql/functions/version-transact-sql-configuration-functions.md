---
title: '@@VERSION (Transact-SQL) | Документы Майкрософт'
ms.custom: ''
ms.date: 03/20/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
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
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 1d44d9755cca86af446449c14c90117be1e45043
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "33060991"
---
# <a name="x40x40version---transact-sql-configuration-functions"></a>&#x40;&#x40;Version — функции настройки Transact SQL
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает сведения о системе и построении текущей установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
@@VERSION  
```  
  
## <a name="return-types"></a>Типы возвращаемых данных  
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
  
-   Выпуск — "Microsoft SQL Azure"  
  
-   Уровень продукта — "(RTM)"  
  
-   Версия продукта  
  
-   Дата сборки  
  
-   Заявление об авторских правах  

> [!NOTE]  
> Нам известно о проблеме, когда @@VERSION сообщает о неправильной версии продукта для базы данных SQL Azure. Версия ядра базы данных SQL Server, выполняющаяся в базе данных SQL Azure, всегда выше локальной версии SQL Server и содержит последние исправления безопасности. Это означает, что уровень исправления всегда совпадает с локальной версией SQL Server или выше ее, и что последние функции, доступные в SQL Server, также доступны в базе данных SQL Azure.
>
> Чтобы определить выпуск ядра базы данных программным способом, используйте SELECT SERVERPROPERTY('EngineEdition'). Этот запрос вернет "5" для автономных баз данных и "8" для управляемых экземпляров в базе данных SQL Azure. 
>
> После решения этой проблемы документация будет обновлена.

  
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
  
  

