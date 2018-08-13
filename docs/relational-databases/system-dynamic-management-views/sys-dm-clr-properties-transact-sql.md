---
title: sys.dm_clr_properties (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_clr_properties
- sys.dm_clr_properties_TSQL
- dm_clr_properties_TSQL
- dm_clr_properties
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_clr_properties dynamic management view
ms.assetid: 220d062f-d117-46e7-a448-06fe48db8163
caps.latest.revision: 26
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 46eb510f9f943d2f63bd3eb1ea3ee4c2bf5f1a52
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/06/2018
ms.locfileid: "39548754"
---
# <a name="sysdmclrproperties-transact-sql"></a>sys.dm_clr_properties (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-pdw-md.md)]

  Возвращает строку для каждого свойства, связанного с интеграцией со средой CLR программы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], включая версию и состояние внутрипроцессной среды CLR. Внутрипроцессная среда CLR инициализируется запуском [CREATE ASSEMBLY](../../t-sql/statements/create-assembly-transact-sql.md), [ALTER ASSEMBLY](../../t-sql/statements/alter-assembly-transact-sql.md), или [инструкция DROP ASSEMBLY](../../t-sql/statements/drop-assembly-transact-sql.md) инструкций, или путем выполнения любой подпрограммы, типа или триггера среды CLR. **Sys.dm_clr_properties** представления не указывает, был ли выполнение определяемого пользователем кода среды CLR на сервере. Выполнение пользовательского кода CLR включается с помощью [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) хранимой процедуры с [включена среда clr](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md) параметр присвоено значение 1.  
  
 **Sys.dm_clr_properties** представление содержит **имя** и **значение** столбцов. Каждая строка в этом представлении содержит подробные сведения о свойстве внутрипроцессной среды CLR. Это представление используется для сбора информации о внутрипроцессной среде CLR, например о каталоге установки, версии и текущем состоянии этой среды. Оно помогает определить, вызвана ли неработоспособность кода интеграции со средой CLR проблемами установки CLR на серверном компьютере.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**name**|**nvarchar(128)**|Имя свойства.|  
|**Значение**|**nvarchar(128)**|Значение свойства.|  
  
## <a name="properties"></a>Свойства  
 **Directory** свойство указывает каталог, в который была установлена .NET Framework на сервере. На серверном компьютере может быть несколько установок платформы .NET Framework, и значение этого свойства определяет установку, которую использует [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 **Версии** указывает версию .NET Framework и внутрипроцессной среды CLR на сервере.  
  
 **Sys.dm_clr_properties** динамическое административное представление может возвращать шесть различных значений **состояние** свойство, которое отражает состояние [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] внутрипроцессной среды CLR. Подробные сведения.  
  
-   Mscoree is not loaded;  
  
-   Mscoree is loaded;  
  
-   Locked CLR version with mscoree;  
  
-   CLR is initialized;  
  
-   CLR initialization permanently failed;  
  
-   CLR is stopped.  
  
 **Mscoree не загружается** и **загружается Mscoree** состояния отображают процесс инициализации размещенной среды CLR при запуске сервера и скорее всего не распознается.  
  
 **Версия среды CLR, заблокирована с mscoree** состояние может возникнуть где внутрипроцессная среда CLR не используется и, таким образом, он имеет еще не был инициализирован. Внутрипроцессная среда CLR инициализируется первой инструкции DDL (такие как [CREATE ASSEMBLY &#40;Transact-SQL&#41;](../../t-sql/statements/create-assembly-transact-sql.md)) или выполнении управляемого объекта базы данных.  
  
 **Среда CLR инициализируется** состояние означает, что внутрипроцессная среда CLR успешно инициализирована. Обратите внимание, что оно не является признаком включения выполнения пользовательского кода CLR. При первой выполнение пользовательского кода CLR включено и затем отключить с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)] [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) хранимой процедуры значение состояния по-прежнему будут **среда CLR инициализируется**.  
  
 **Без возможности восстановления не удалось инициализировать CLR** состояние означает, что внутрипроцессной среды CLR не удалось инициализировать. Возможной причиной является нехватка памяти, также это может быть результатом сбоя при подтверждении соединения между [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и средой CLR. В этом случае будет вызвано сообщение об ошибке 6512 или 6513.  
  
 **CLR остановлена состояние** можно увидеть, только когда [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] завершает работу.  
  
## <a name="remarks"></a>Примечания  
 Свойства и значения этого представления может измениться в будущих версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] вследствие улучшений функциональных возможностей интеграции со средой CLR.  
  
## <a name="permissions"></a>Разрешения  
  
На [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], требуется `VIEW SERVER STATE` разрешение.   
На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], требуется `VIEW DATABASE STATE` разрешение в базе данных.   

## <a name="examples"></a>Примеры  
 В следующем примере происходит получение данных о внутрипроцессной среде CLR:  
  
```  
SELECT name, value   
FROM sys.dm_clr_properties;  
```  
  
## <a name="see-also"></a>См. также  
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Динамические административные представления, связанные с среда CLR &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/common-language-runtime-related-dynamic-management-views-transact-sql.md)  
  
  
