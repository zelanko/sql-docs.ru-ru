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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 59b7f4a0cf0c3ba3335a181b35560af8847fca8b
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82824527"
---
# <a name="sp_helpdevice-transact-sql"></a>sp_helpdevice (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает сведения об устройствах резервного копирования Microsoft® SQL Server™.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Вместо этого рекомендуется использовать представление каталога [sys. backup_devices](../../relational-databases/system-catalog-views/sys-backup-devices-transact-sql.md)  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_helpdevice [ [ @devname = ] 'name' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @devname = ] 'name'`Имя устройства резервного копирования, для которого сообщается информация. Значение *Name* всегда имеет тип **sysname**.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**device_name**|**sysname**|Имя логического устройства.|  
|**physical_name**|**nvarchar(260)**|Физическое имя файла.|  
|**nописание**|**nvarchar(255)**|Описание устройства.|  
|**status**|**int**|Число, соответствующее описанию состояния в столбце **Описание** .|  
|**cntrltype**|**smallint**|Тип контроллера устройства.<br /><br /> 2 = дисковое устройство.<br /><br /> 5 = ленточное устройство.|  
|**size**|**int**|Размер устройства в 2-килобайтовых страницах.|  
  
## <a name="remarks"></a>Примечания  
 Если указано *имя* , **sp_helpdevice** отображает сведения об указанном устройстве дампа. Если параметр *Name* не указан, **sp_helpdevice** отображает сведения обо всех устройствах дампа в представлении каталога **sys. backup_devices** .  
  
 Устройства дампа добавляются в систему с помощью **sp_addumpdevice**.  
  
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
 [Ядро СУБД хранимых процедур &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
