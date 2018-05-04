---
title: sys.dm_clr_loaded_assemblies (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_clr_loaded_assemblies
- sys.dm_clr_loaded_assemblies_TSQL
- dm_clr_loaded_assemblies_TSQL
- sys.dm_clr_loaded_assemblies
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_clr_loaded_assemblies dynamic management view
ms.assetid: 8523d8db-d8a0-4b1f-ae19-6705d633e0a6
caps.latest.revision: 22
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: da771a7d64383bf9328d04353c071fbe9f8a1fc6
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sysdmclrloadedassemblies-transact-sql"></a>sys.dm_clr_loaded_assemblies (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает по строке для каждой из управляемых пользовательских сборок, загруженных в адресное пространство сервера. Используйте это представление для исследования и устранение неполадок с интеграцией со средой CLR управляемых объектов базы данных, которые выполняются в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Сборки — это файлы динамических библиотек с управляемым кодом, которые используются для определения и развертывания управляемых объектов базы данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Каждый раз, когда пользователь запускает один из управляемых объектов базы данных, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и среда CLR загружают сборку (а также другие сборки, на которые она ссылается), в которой определен этот управляемый объект базы данных. Сборка остается загруженной в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для увеличения производительности, чтобы впоследствии управляемые объекты базы данных, содержащиеся в сборке, можно было бы вызывать без повторной загрузки сборки. Сборка не выгружается до тех пор, пока у [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не возникнет необходимость в освобождении памяти. Дополнительные сведения о сборках и интеграции со средой CLR см. в разделе [среде размещения CLR](../../relational-databases/clr-integration/clr-integration-architecture-clr-hosted-environment.md). Дополнительные сведения об управляемых объектов базы данных см. в разделе [построение объектов базы данных с помощью среды CLR &#40;CLR&#41; интеграции](../../relational-databases/clr-integration/database-objects/building-database-objects-with-common-language-runtime-clr-integration.md).  

  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**assembly_id**|**int**|Идентификатор загруженной сборки. **Assembly_id** можно использовать для поиска дополнительной информации о сборке в [sys.assemblies &#40;Transact-SQL&#41; ](../../relational-databases/system-catalog-views/sys-assemblies-transact-sql.md) представления каталога. Обратите внимание, что [!INCLUDE[tsql](../../includes/tsql-md.md)] [sys.assemblies](../../relational-databases/system-catalog-views/sys-assemblies-transact-sql.md) каталога содержит сборки только текущей базы данных. **Sqs.dm_clr_loaded_assemblies** представление показывает все сборки, загруженные на сервере.|  
|**appdomain_address**|**int**|Адрес домена приложения (**AppDomain**) в который загружена сборка. Все сборки, принадлежащие одному пользователю всегда загружаются в одном **AppDomain**. **Appdomain_address** можно использовать для поиска дополнительной информации о **AppDomain** в [sys.dm_clr_appdomains](../../relational-databases/system-dynamic-management-views/sys-dm-clr-appdomains-transact-sql.md) представления.|  
|**load_time**|**datetime**|Время, когда сборка была загружена. Обратите внимание, что сборка остается загруженной до [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в условиях нехватки памяти и выгружает **AppDomain**. Вы можете отслеживать **load_time** чтобы узнать, как часто [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставляется в условиях нехватки памяти и выгружает **AppDomain**.|  
  
## <a name="permissions"></a>Разрешения  
 необходимо разрешение VIEW SERVER STATE на сервере.  
  
## <a name="remarks"></a>Замечания  
 **Dm_clr_loaded_assemblies.appdomain_address** представление имеет отношение "многие к одному" с **dm_clr_appdomains.appdomain_address**. **Dm_clr_loaded_assemblies.assembly_id** представление имеет отношение "один ко многим" с **sys.assemblies.assembly_id**.  
  
## <a name="examples"></a>Примеры  
 Следующий пример показывает, как можно просматривать сведения обо всех сборках, которые в данный момент загружены в текущей базе данных.  
  
```  
 SELECT a.name, a.assembly_id, a.permission_set_desc, a.is_visible, a.create_date, l.load_time   
FROM sys.dm_clr_loaded_assemblies AS l   
INNER JOIN sys.assemblies AS a  
ON l.assembly_id = a.assembly_id;  
```  
  
 В следующем примере показано, как просмотреть подробные сведения о **AppDomain** в котором загружена данная сборка.  
  
```  
SELECT appdomain_id, creation_time, db_id, user_id, state  
FROM sys.dm_clr_appdomains AS a  
WHERE appdomain_address =   
(SELECT appdomain_address   
 FROM sys.dm_clr_loaded_assemblies  
 WHERE assembly_id = 555);  
```  
  
## <a name="see-also"></a>См. также  
 [Динамические административные представления, связанные с общеязыковой &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/common-language-runtime-related-dynamic-management-views-transact-sql.md)  
  
  
