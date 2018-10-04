---
title: sys.dm_clr_loaded_assemblies (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
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
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6c5a65210f7789d49a05785c05df45cda7272040
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47715934"
---
# <a name="sysdmclrloadedassemblies-transact-sql"></a>sys.dm_clr_loaded_assemblies (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает по строке для каждой из управляемых пользовательских сборок, загруженных в адресное пространство сервера. Используйте это представление для понимания и устранения интеграция со средой CLR управляемые объекты базы данных, которые выполняются в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Сборки — это файлы динамических библиотек с управляемым кодом, которые используются для определения и развертывания управляемых объектов базы данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Каждый раз, когда пользователь запускает один из управляемых объектов базы данных, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и среда CLR загружают сборку (а также другие сборки, на которые она ссылается), в которой определен этот управляемый объект базы данных. Сборка остается загруженной в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для увеличения производительности, чтобы впоследствии управляемые объекты базы данных, содержащиеся в сборке, можно было бы вызывать без повторной загрузки сборки. Сборка не выгружается до тех пор, пока у [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не возникнет необходимость в освобождении памяти. Дополнительные сведения о сборках и интеграции со средой CLR см. в разделе [среде размещения CLR](../../relational-databases/clr-integration/clr-integration-architecture-clr-hosted-environment.md). Дополнительные сведения об управляемых объектов базы данных см. в разделе [построение объектов базы данных с помощью среды CLR &#40;CLR&#41; интеграции](../../relational-databases/clr-integration/database-objects/building-database-objects-with-common-language-runtime-clr-integration.md).  

  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**assembly_id**|**int**|Идентификатор загруженной сборки. **Assembly_id** можно использовать для поиска дополнительной информации о сборке в [sys.assemblies &#40;Transact-SQL&#41; ](../../relational-databases/system-catalog-views/sys-assemblies-transact-sql.md) представления каталога. Обратите внимание, что [!INCLUDE[tsql](../../includes/tsql-md.md)] [sys.assemblies](../../relational-databases/system-catalog-views/sys-assemblies-transact-sql.md) каталога сборки показано только текущей базы данных. **Sqs.dm_clr_loaded_assemblies** представление показывает все сборки, загруженные на сервере.|  
|**appdomain_address**|**int**|Адрес домена приложения (**AppDomain**) в который загружена сборка. Все сборки, принадлежащие одному пользователю всегда загружаются в одном **AppDomain**. **Appdomain_address** можно использовать для поиска дополнительной информации о **AppDomain** в [sys.dm_clr_appdomains](../../relational-databases/system-dynamic-management-views/sys-dm-clr-appdomains-transact-sql.md) представления.|  
|**load_time**|**datetime**|Время, когда сборка была загружена. Обратите внимание на то, что сборка остается загруженной до [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] испытывает недостаток памяти и выгружает **AppDomain**. Вы можете отслеживать **load_time** чтобы узнать, как часто [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] освобождении памяти и выгружает **AppDomain**.|  
  
## <a name="permissions"></a>Разрешения  
 необходимо разрешение VIEW SERVER STATE на сервере.  
  
## <a name="remarks"></a>Примечания  
 **Dm_clr_loaded_assemblies.appdomain_address** представление имеет отношение "многие к одному" с **dm_clr_appdomains.appdomain_address**. **Dm_clr_loaded_assemblies.assembly_id** представление имеет отношение "один ко многим" с **sys.assemblies.assembly_id**.  
  
## <a name="examples"></a>Примеры  
 Следующий пример показывает, как можно просматривать сведения обо всех сборках, которые в данный момент загружены в текущей базе данных.  
  
```  
 SELECT a.name, a.assembly_id, a.permission_set_desc, a.is_visible, a.create_date, l.load_time   
FROM sys.dm_clr_loaded_assemblies AS l   
INNER JOIN sys.assemblies AS a  
ON l.assembly_id = a.assembly_id;  
```  
  
 В следующем примере показано, как для просмотра сведений о **AppDomain** в котором загружена данная сборка.  
  
```  
SELECT appdomain_id, creation_time, db_id, user_id, state  
FROM sys.dm_clr_appdomains AS a  
WHERE appdomain_address =   
(SELECT appdomain_address   
 FROM sys.dm_clr_loaded_assemblies  
 WHERE assembly_id = 555);  
```  
  
## <a name="see-also"></a>См. также  
 [Динамические административные представления, связанные с среда CLR &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/common-language-runtime-related-dynamic-management-views-transact-sql.md)  
  
  
