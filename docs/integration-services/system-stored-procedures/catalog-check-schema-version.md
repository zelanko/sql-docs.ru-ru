---
title: catalog.check_schema_version | Документы Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: e0d5e9f5-59c6-4118-87b5-4aa5c37a7df6
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 23746065ca7096b0405114344d4f6a752bfedda1
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68110459"
---
# <a name="catalogcheckschemaversion"></a>catalog.check_schema_version 

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Определяет, совместимы ли схема каталога SSISDB и двоичные файлы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] (сборка ISServerExec и SQLCLR).  
  
 ISServerExec.exc заносит в журнал сообщение об ошибке, если схема и двоичные файлы несовместимы.  
  
 Версия схемы SSISDB увеличивается, если происходит изменение схемы во время применения исправлений и во время обновлений. Поэтому рекомендуется запускать эту хранимую процедуру после восстановления резервной копии SSISDB, чтобы убедиться, что схема и двоичные файлы совместимы.  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
catalog.check_schema_version [@use32bitruntime = ] use32bitruntime  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @use32bitruntime= ] *use32bitruntime*  
 Если параметр имеет значение **1**, то вызывается 32-разрядная версия программы dtexec. Параметр *use32bitruntime* имеет тип **int**.  
  
## <a name="result-set"></a>Результирующий набор  
 None  
  
## <a name="permissions"></a>Разрешения  
 Эта хранимая процедура требует наличия одного из следующих разрешений:  
  
-   Членство в роли базы данных **ssis_admin**.  
  
  
