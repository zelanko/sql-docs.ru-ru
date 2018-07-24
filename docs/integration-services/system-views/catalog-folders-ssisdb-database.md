---
title: catalog.folders (база данных SSISDB) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: language-reference
ms.assetid: 21a37c16-60aa-4b3f-8bca-ac90ad1697ac
caps.latest.revision: 14
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: f8f2456972b3be34cc6f50df55108f8f553d7f0a
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38020967"
---
# <a name="catalogfolders-ssisdb-database"></a>catalog.folders (база данных SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Отображает папки в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|идентификатор|**bigint**|Уникальный идентификатор папки.|  
|name|**sysname(nvarchar(128)**|Имя папки, уникальное в пределах каталога служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].|  
|description|**nvarchar(1024)**|Описание папки.|  
|created_by_sid|**varbinary(85)**|Уникальный идентификатор безопасности пользователя, создавшего папку.|  
|created_by_name|**nvarchar(128)**|Имя пользователя, создавшего папку.|  
|created_time|**datetimeoffset(7)**|Дата и время создания папки.|  
  
## <a name="remarks"></a>Remarks  
 В этом представлении отображается строка для каждой папки в каталоге.  
  
## <a name="permissions"></a>Разрешения  
 Это представление требует применения одного из следующих разрешений:  
  
-   разрешение READ на папку  
  
-   Членство в роли базы данных **ssis_admin**  
  
-   Членство в роли сервера **sysadmin**  
  
> [!NOTE]  
>  Наличие разрешения на выполнение операции на сервере подразумевает наличие разрешения на просмотр сведений об этой операции. Действует защита на уровне строки. Отображаются только строки, на которые у вас имеется разрешение.  
  
  
