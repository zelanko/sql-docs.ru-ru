---
title: "sys.dm_clr_properties (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, pdw
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_clr_properties
- sys.dm_clr_properties_TSQL
- dm_clr_properties_TSQL
- dm_clr_properties
dev_langs: TSQL
helpviewer_keywords: sys.dm_clr_properties dynamic management view
ms.assetid: 220d062f-d117-46e7-a448-06fe48db8163
caps.latest.revision: "26"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: cb5c73dafd26f9ddd4da885b77c8649df13c3d2d
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2017
---
# <a name="sysdmclrproperties-transact-sql"></a>sys.dm_clr_properties (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-pdw-md.md)]

  Возвращает строку для каждого свойства, связанного с интеграцией со средой CLR программы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], включая версию и состояние внутрипроцессной среды CLR. Внутрипроцессная среда CLR инициализируется запуском [CREATE ASSEMBLY](../../t-sql/statements/create-assembly-transact-sql.md), [ALTER ASSEMBLY](../../t-sql/statements/alter-assembly-transact-sql.md), или [DROP ASSEMBLY](../../t-sql/statements/drop-assembly-transact-sql.md) инструкций или путем выполнения любой подпрограммы, типа или триггера среды CLR. **Sys.dm_clr_properties** представления не указывает, включены ли выполнение пользовательского кода CLR на сервере. Выполнение пользовательского кода CLR включается с помощью [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) хранимую процедуру с [включена среда clr](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md) присвоено значение 1.  
  
 **Sys.dm_clr_properties** представление содержит **имя** и **значение** столбцов. Каждая строка в этом представлении содержит подробные сведения о свойстве внутрипроцессной среды CLR. Это представление используется для сбора информации о внутрипроцессной среде CLR, например о каталоге установки, версии и текущем состоянии этой среды. Оно помогает определить, вызвана ли неработоспособность кода интеграции со средой CLR проблемами установки CLR на серверном компьютере.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**name**|**nvarchar(128)**|Имя свойства.|  
|**значение**|**nvarchar(128)**|Значение свойства.|  
  
## <a name="properties"></a>Свойства  
 **Каталога** указывает каталог, который .NET Framework была установлена на сервере. На серверном компьютере может быть несколько установок платформы .NET Framework, и значение этого свойства определяет установку, которую использует [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 **Версии** свойство указывает версию платформы .NET Framework и внутрипроцессной среды CLR на сервере.  
  
 **Sys.dm_clr_properties** динамическое административное представление может возвращать шесть различных значений **состояние** свойство, которое отражает состояние [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] внутрипроцессной среды CLR. Подробные сведения.  
  
-   Mscoree is not loaded;  
  
-   Mscoree is loaded;  
  
-   Locked CLR version with mscoree;  
  
-   CLR is initialized;  
  
-   CLR initialization permanently failed;  
  
-   CLR is stopped.  
  
 **Mscoree не загружено** и **загружается Mscoree** отображают процесс инициализации размещенной среды CLR при запуске сервера состояний и не могут быть показаны.  
  
 **Версию среды CLR, заблокирован с mscoree** состояние может возникать, когда внутрипроцессной среды CLR не используется и, таким образом, он еще не была инициализирована. Внутрипроцессная среда CLR инициализируется при первом запуске инструкции DDL (такие как [CREATE ASSEMBLY &#40; Transact-SQL &#41; ](../../t-sql/statements/create-assembly-transact-sql.md)) или выполнении управляемого объекта базы данных.  
  
 **Среда CLR инициализируется** состояние означает, что внутрипроцессная среда CLR успешно инициализирована. Обратите внимание, что оно не является признаком включения выполнения пользовательского кода CLR. Если первый выполнение пользовательского кода CLR включено и отключить, используя [!INCLUDE[tsql](../../includes/tsql-md.md)] [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) хранимой процедуры значение состояния по-прежнему будет **среда CLR инициализируется**.  
  
 **Без возможности восстановления не удалось инициализировать CLR** состояние означает, что внутрипроцессной среды CLR не удалось инициализировать. Возможной причиной является нехватка памяти, также это может быть результатом сбоя при подтверждении соединения между [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и средой CLR. В этом случае будет вызвано сообщение об ошибке 6512 или 6513.  
  
 **CLR остановлена состояние** можно увидеть, только если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] завершает работу.  
  
## <a name="remarks"></a>Замечания  
 Свойства и значения этого представления может измениться в будущих версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] вследствие улучшений функциональных возможностей интеграции со средой CLR.  
  
## <a name="permissions"></a>Permissions  
 На [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] необходимо разрешение VIEW SERVER STATE на сервере.  
  
 На [!INCLUDE[ssSDS](../../includes/sssds-md.md)] уровней Premium необходимо разрешение VIEW DATABASE STATE в базе данных. На [!INCLUDE[ssSDS](../../includes/sssds-md.md)] уровней Standard и Basic требуется [!INCLUDE[ssSDS](../../includes/sssds-md.md)] учетная запись администратора.  
  
## <a name="examples"></a>Примеры  
 В следующем примере происходит получение данных о внутрипроцессной среде CLR:  
  
```  
SELECT name, value   
FROM sys.dm_clr_properties;  
```  
  
## <a name="see-also"></a>См. также:  
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Общеязыковая среда выполнения, связанные с динамическим административным представлениям &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/common-language-runtime-related-dynamic-management-views-transact-sql.md)  
  
  
