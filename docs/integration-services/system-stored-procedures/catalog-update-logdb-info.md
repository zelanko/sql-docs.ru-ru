---
title: "Catalog.update_logdb_info (база данных SSISDB) | Документы Microsoft"
ms.custom: 
ms.date: 07/18/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
caps.latest.revision: 1
author: haoqian
ms.author: haoqian
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: a898be08859230ab873fd8e358b892789aaed043
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="catalogupdatelogdbinfo-ssisdb-database"></a>Catalog.update_logdb_info (база данных SSISDB)
[!INCLUDE[tsql-appliesto-ssvnxt-xxxx-xxxx-xxx.md](../../includes/tsql-appliesto-ssvnxt-xxxx-xxxx-xxx.md)]

Обновление [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] сведения шкалы Out ведения журнала.

## <a name="syntax"></a>Синтаксис

```tsql
update_logdb_info [@server_name = ] server_name, [@connection_string = ] connection_string
```

## <a name="arguments"></a>Аргументы
[ @server_name =] *имя_сервера*  
 Sql Server, используемые для ведения журнала масштабное развертывание. *Имя_сервера* — **nvarchar**.  

 [ @connection_string =] *строка_соединения*  
 Строка подключения, используемые для ведения журнала масштабное развертывание. *Строка_соединения* — **nvarchar**.

 ## <a name="return-code-value"></a>Значения кодов возврата  
 0 (успешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет  

## <a name="permissions"></a>Разрешения  
 Эта хранимая процедура требует применения одного из следующих разрешений:  
   
-   Членство в **ssis_admin** роли базы данных  
  
-   Членство в **sysadmin** роли сервера  
 
