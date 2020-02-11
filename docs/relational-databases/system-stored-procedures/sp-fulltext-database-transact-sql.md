---
title: sp_fulltext_database (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_fulltext_database_TSQL
- sp_fulltext_database
dev_langs:
- TSQL
helpviewer_keywords:
- sp_fulltext_database
ms.assetid: eeb1e151-eb00-484c-8fd1-5641e621ffc6
author: MikeRayMSFT
ms.author: mikeray
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 0c27f2efcfc15cc1ff9d53f735c08fad922f9466
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68124277"
---
# <a name="sp_fulltext_database-transact-sql"></a>sp_fulltext_database (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Не влияет на полнотекстовые каталоги в [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] и более поздних версиях и поддерживается только для обеспечения обратной совместимости. **sp_fulltext_database** не отключает средство полнотекстового поиска для данной базы данных. В [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] полнотекстовое индексирование всегда включено для всех баз данных, созданных пользователем.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]Вместо [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] этого используйте.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_fulltext_database [@action=] 'action'  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @action = ] 'action'`Действие, которое необходимо выполнить. **Action** имеет тип **varchar (20)** и может принимать одно из следующих значений.  
  
|Значение|Description|  
|-----------|-----------------|  
|**параметр**|Поддерживается только для обеспечения обратной совместимости. Не действует на полнотекстовые каталоги в [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] и более поздних версиях.|  
|**включен**|Поддерживается только для обеспечения обратной совместимости. Не действует на полнотекстовые каталоги в [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] и более поздних версиях.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успех) или 1 (сбой).  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Remarks  
 В [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] и более поздних версиях полнотекстовое индексирование отключить нельзя. Отключение полнотекстового индексирования не приводит к удалению строк из **таблицы sysfulltextcatalogs** и не указывает на то, что таблицы с поддержкой полнотекстового индексирования больше не отмечаются для полнотекстовой индексации. Все определения полнотекстовых метаданных продолжают храниться в системных таблицах.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** и **db_owner** предопределенной роли базы данных могут выполнять **sp_fulltext_database**.  
  
## <a name="see-also"></a>См. также:  
 [DATABASEPROPERTYEX &#40;Transact-SQL&#41;](../../t-sql/functions/databasepropertyex-transact-sql.md)   
 [FULLTEXTSERVICEPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/fulltextserviceproperty-transact-sql.md)   
 [Системные хранимые процедуры &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
