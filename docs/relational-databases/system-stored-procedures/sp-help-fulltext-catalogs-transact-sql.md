---
title: sp_help_fulltext_catalogs (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_help_fulltext_catalogs_TSQL
- sp_help_fulltext_catalogs
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_fulltext_catalogs
ms.assetid: 1b94f280-e095-423f-88bc-988c9349d44c
caps.latest.revision: 36
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 5490c7e8d8658ddc8048e63d082d48ea92249c08
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
ms.locfileid: "33243397"
---
# <a name="sphelpfulltextcatalogs-transact-sql"></a>sp_help_fulltext_catalogs (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает идентификатор, имя, корневой каталог, состояние и число таблиц с полнотекстовым индексом для заданного полнотекстового каталога.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Используйте [sys.fulltext_catalogs](../../relational-databases/system-catalog-views/sys-fulltext-catalogs-transact-sql.md) представления каталога.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_help_fulltext_catalogs [ @fulltext_catalog_name = ] 'fulltext_catalog_name'  
```  
  
## <a name="arguments"></a>Аргументы  
 [ **@fulltext_catalog_name=**] **'***fulltext_catalog_name***'**  
 Имя полнотекстового каталога. *fulltext_catalog_name* — **sysname**. Если этот аргумент не указывается или имеет значение NULL, возвращаются сведения обо всех полнотекстовых каталогах, связанных с текущей базой данных.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 В данной таблице показан результирующий набор, упорядоченный по столбцу **ftcatid**.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**fulltext_catalog_id**|**smallint**|Идентификатор полнотекстового каталога.|  
|**ИМЯ**|**sysname**|Имя полнотекстового каталога.|  
|**PATH**|**nvarchar(260)**|Начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], это предложение не оказывает влияние на работу системы.|  
|**СОСТОЯНИЕ**|**int**|Состояние заполнения полнотекстового индекса каталога:<br /><br /> 0 = бездействие<br /><br /> 1 = идет полное заполнение<br /><br /> 2 = пауза<br /><br /> 3 = ограниченный режим<br /><br /> 4 = восстановление<br /><br /> 5 = выключение<br /><br /> 6 = идет добавочное заполнение<br /><br /> 7 = построение индекса<br /><br /> 8 = диск заполнен. Пауза<br /><br /> 9 = отслеживание изменений.<br /><br /> NULL = У пользователя нет разрешения VIEW на полнотекстовый каталог, в базе данных не включены полнотекстовые возможности или полнотекстовый компонент не установлен.|  
|**NUMBER_FULLTEXT_TABLES**|**int**|Число полнотекстовых индексированных таблиц, связанных с каталогом.|  
  
## <a name="permissions"></a>Разрешения  
 По умолчанию разрешения на выполнение предоставлены членам роли **public** .  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращаются сведения о полнотекстовом каталоге `Cat_Desc`.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_help_fulltext_catalogs 'Cat_Desc' ;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [FULLTEXTCATALOGPROPERTY & #40; Transact-SQL & #41;](../../t-sql/functions/fulltextcatalogproperty-transact-sql.md)   
 [sp_fulltext_catalog &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-fulltext-catalog-transact-sql.md)   
 [sp_help_fulltext_catalogs_cursor &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-fulltext-catalogs-cursor-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
