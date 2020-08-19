---
description: catalog.extended_operation_info (база данных SSISDB)
title: catalog.extended_operation_info (база данных SSISDB) | Документы Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: db299b45-557d-4c62-8e14-355cdb051f63
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c4082c0bbf428a96776ae18fece7333f0401a2b6
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88422078"
---
# <a name="catalogextended_operation_info-ssisdb-database"></a>catalog.extended_operation_info (база данных SSISDB)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Отображает расширенные сведения для всех операций в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|info_id|**bigint**|Уникальный идентификатор (ID) расширенных сведений.|  
|operation_id|**bigint**|Уникальный идентификатор (ID) операции, соответствующей расширенным сведениям.|  
|object_name|**nvarchar(260)**|Имя объекта.|  
|object_type|**smallint**|Тип объекта, затронутого операцией. Объект может представлять собой папку (`10`), проект (`20`), пакет (`30`), среду (`40`) или экземпляр выполнения (`50`).|  
|reference_id|**bigint**|Уникальный идентификатор (ID) ссылки, используемой в операции.|  
|status|**int**|Состояние операции. Возможными значениями являются: создана (`1`), запущена (`2`), отменена (`3`), завершена неуспешно (`4`), ожидает (`5`), завершена непредвиденно (`6`), выполнена успешно (`7`), остановлена (`8`) и завершена (`9`).|  
|start_time|**datetimeoffset(7)**|Дата и время начала операции.|  
|end_time|**datetimeoffset(7)**|Дата и время окончания операции.|  
  
## <a name="remarks"></a>Комментарии  
 В одном объекте может быть несколько строк расширенных сведений.  
  
## <a name="permissions"></a>Разрешения  
 Это представление требует применения одного из следующих разрешений:  
  
-   Разрешение READ по отношению к операции  
  
-   Членство в роли базы данных **ssis_admin**  
  
-   Членство в роли сервера **sysadmin**  
  
> [!NOTE]  
>  Наличие разрешения на выполнение операции на сервере подразумевает наличие разрешения на просмотр сведений об этой операции. Действует защита на уровне строки. Отображаются только строки, на которые у вас имеется разрешение.  
  
  
