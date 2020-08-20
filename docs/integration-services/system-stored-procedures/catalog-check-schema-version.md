---
description: catalog.check_schema_version
title: catalog.check_schema_version | Документы Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: e0d5e9f5-59c6-4118-87b5-4aa5c37a7df6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b8f1d04f2a41c247a3de8a66f5b07ee74f5036b5
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88457010"
---
# <a name="catalogcheck_schema_version"></a>catalog.check_schema_version 

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Определяет, совместимы ли схема каталога SSISDB и двоичные файлы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] (сборка ISServerExec и SQLCLR).  
  
 ISServerExec.exc заносит в журнал сообщение об ошибке, если схема и двоичные файлы несовместимы.  
  
 Версия схемы SSISDB увеличивается, если происходит изменение схемы во время применения исправлений и во время обновлений. Поэтому рекомендуется запускать эту хранимую процедуру после восстановления резервной копии SSISDB, чтобы убедиться, что схема и двоичные файлы совместимы.  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
catalog.check_schema_version [ @use32bitruntime = ] use32bitruntime  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @use32bitruntime= ] *use32bitruntime*  
 Если параметр имеет значение **1**, то вызывается 32-разрядная версия программы dtexec. Параметр *use32bitruntime* имеет тип **int**.  
  
## <a name="result-set"></a>Результирующий набор  
 None  
  
## <a name="permissions"></a>Разрешения  
 Эта хранимая процедура требует наличия одного из следующих разрешений:  
  
-   Членство в роли базы данных **ssis_admin**.  
  
  
