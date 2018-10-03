---
title: sp_helpdevice (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helpdevice
- sp_helpdevice_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpdevice
ms.assetid: 1a5eafa7-384e-4691-ba05-978eb73bbefb
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3ec03794e60027ea578988dbe38855d8ad14cb09
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47596802"
---
# <a name="sphelpdevice-transact-sql"></a>sp_helpdevice (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает сведения об устройствах резервного копирования Microsoft® SQL Server™.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Мы рекомендуем использовать [sys.backup_devices](../../relational-databases/system-catalog-views/sys-backup-devices-transact-sql.md) вместо этого представление каталога  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_helpdevice [ [ @devname = ] 'name' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@devname =** ] **"***имя***"**  
 Имя устройства резервного копирования, для которого выводятся сведения. Значение *имя* всегда **sysname**.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**device_name**|**sysname**|Имя логического устройства.|  
|**physical_name**|**nvarchar(260)**|Физическое имя файла.|  
|**Описание**|**nvarchar(255)**|Описание устройства.|  
|**status**|**int**|Число, которое соответствует состоянию описания в **описание** столбца.|  
|**cntrltype**|**smallint**|Тип контроллера устройства.<br /><br /> 2 = дисковое устройство.<br /><br /> 5 = ленточное устройство.|  
|**size**|**int**|Размер устройства в 2-килобайтовых страницах.|  
  
## <a name="remarks"></a>Примечания  
 Если *имя* указано, **sp_helpdevice** отображает сведения об указанном устройстве хранения. Если *имя* не указан, **sp_helpdevice** отображаются сведения обо всех устройствах хранения в **sys.backup_devices** представления каталога.  
  
 Устройств хранения добавляются в систему с помощью **sp_addumpdevice**.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо быть членом роли **public**.  
  
## <a name="examples"></a>Примеры  
 В приведенном ниже примере возвращаются сведения обо всех устройствах хранения в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```  
EXEC sp_helpdevice;  
```  
  
## <a name="see-also"></a>См. также  
 [sp_addumpdevice (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql.md)   
 [sp_dropdevice (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-dropdevice-transact-sql.md)   
 [Хранимым процедурам ядра СУБД &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
