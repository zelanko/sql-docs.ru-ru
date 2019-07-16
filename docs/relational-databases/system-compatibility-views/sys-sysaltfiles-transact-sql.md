---
title: sys.sysaltfiles (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.sysaltfiles_TSQL
- sys.sysaltfiles
- sysaltfiles_TSQL
- sysaltfiles
dev_langs:
- TSQL
helpviewer_keywords:
- sysaltfiles system table
- sys.sysaltfiles compatibility view
ms.assetid: 698dec23-5336-4108-87a5-f8e407f8da09
author: rothja
ms.author: jroth
ms.openlocfilehash: 891e88761cac47be83fb69debbbc5e4cb6c401c0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68006975"
---
# <a name="syssysaltfiles-transact-sql"></a>sys.sysaltfiles (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  В особых случаях содержит строки, соответствующие файлам в базе данных.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**fileid**|**smallint**|Идентификационный номер файла. Уникален для каждой базы данных.|  
|**groupid**|**smallint**|Идентификационный номер файловой группы.|  
|**size**|**int**|Размер файла, в страницах по 8 килобайт (КБ).|  
|**параметр MaxSize**|**int**|Максимальный размер файла, в страницах по 8 КБ.<br /><br /> 0 = не возрастает.<br /><br /> -1 = размер файла может увеличиваться до полного заполнения диска.<br /><br /> 268435456 = файл журнала может увеличиваться до 2 ТБ.<br /><br /> Примечание. Базы данных, которые обновляются с размером файла журнала возвращают -1 для максимального размера файла журнала.|  
|**рост**|**int**|Предельный размер базы данных.<br /><br /> 0 = не возрастает. В зависимости от значения состояния может представлять собой либо процент от размера файла, либо число страниц: Если **состояние** равно 0x100000, **рост** процент от размера файла; в противном случае, это число страниц.|  
|**status**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**perf**|**int**|Зарезервировано.|  
|**dbid**|**smallint**|Идентификационный номер базы данных, которой принадлежит данный файл.|  
|**name**|**sysname**|Логическое имя файла.|  
|**Имя файла**|**nvarchar(260)**|Имя физического устройства. Включает полный путь к файлу.|  
  
## <a name="see-also"></a>См. также  
 [Сопоставление системных таблиц с системными представлениями &#40;Transact-SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Представления совместимости (Transact-SQL)](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
