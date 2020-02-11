---
title: sys. таблицу sysprotects (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysprotects
- sys.sysprotects_TSQL
- sys.sysprotects
- sysprotects_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sysprotects compatibility view
- sysprotects system table
ms.assetid: 49c9658d-fb51-4c77-94a0-fba699b0102d
author: rothja
ms.author: jroth
ms.openlocfilehash: ca403b5ad56386252d789ddede007a7293e59a40
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68079243"
---
# <a name="syssysprotects-transact-sql"></a>sys.sysprotects (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит сведения о разрешениях, примененных к учетным записям безопасности в базе данных при помощи инструкций GRANT и DENY.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**удостоверения**|**int**|Идентификатор объекта, к которому применены данные разрешения.|  
|**uid**|**smallint**|Идентификатор пользователя или группы, к которым применены данные разрешения. Вызывает переполнение или возвращает значение NULL, если количество пользователей и ролей превышает 32 767.|  
|**поддержки**|**tinyint**|Может иметь одно из следующих разрешений:<br /><br /> 26 = REFERENCES<br /><br /> 178 = CREATE FUNCTION<br /><br /> 193 = SELECT<br /><br /> 195 = INSERT<br /><br /> 196 = УДАЛЕНИЕ<br /><br /> 197 = ОБНОВЛЕНИЕ<br /><br /> 198 = CREATE TABLE<br /><br /> 203 = CREATE DATABASE<br /><br /> 207 = CREATE VIEW<br /><br /> 222 = CREATE PROCEDURE<br /><br /> 224 = EXECUTE<br /><br /> 228 = BACKUP DATABASE<br /><br /> 233 = CREATE DEFAULT<br /><br /> 235 = BACKUP LOG<br /><br /> 236 = CREATE RULE|  
|**protecttype**|**tinyint**|Может иметь следующие значения:<br /><br /> 204 = GRANT_W_GRANT<br /><br /> 205 = GRANT<br /><br /> 206 = DENY|  
|**столбце**|**varbinary (8000)**|Битовая карта столбцов, к которым применены эти разрешения SELECT или UPDATE.<br /><br /> Бит 0 = все столбцы.<br /><br /> Бит 1 = разрешения применяются к этому столбцу.<br /><br /> NULL = нет данных.|  
|**GRANTOR**|**smallint**|Идентификатор пользователя, который выдал разрешения GRANT или DENY. Вызывает переполнение или возвращает значение NULL, если количество пользователей и ролей превышает 32 767.|  
  
## <a name="see-also"></a>См. также:  
 [Сопоставление системных таблиц с системными представлениями &#40;&#41;Transact-SQL](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Представления совместимости &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
