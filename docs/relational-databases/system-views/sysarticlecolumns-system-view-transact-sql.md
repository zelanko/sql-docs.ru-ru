---
description: Системное представление sysarticlecolumns (Transact-SQL)
title: Системное представление sysarticlecolumns (Системное представление) (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sysarticlecolumns
- sysarticlecolumns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysarticlecolumns view
ms.assetid: a8dd8d13-c827-45c4-87ba-802725301382
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1a6e359aa7f6c0e7efc4090152b152ab1bfb6fbc
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88460296"
---
# <a name="sysarticlecolumns-system-view-transact-sql"></a>Системное представление sysarticlecolumns (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Представление **системное представление sysarticlecolumns** предоставляет дополнительные сведения о столбцах в опубликованных статьях. Это представление хранится в базе данных распространителя.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**artid**|**int**|Определяет статью.|  
|**идентификатора столбца**|**int**|Идентифицирует столбец в статье.|  
|**is_udt**|**int**|Указывает, принадлежит ли столбец к пользовательскому типу данных (UDT). Значение **1** указывает на столбец определяемого пользователем типа.|  
|**is_xml**|**int**|Значение, если столбец является **XML-** столбцом. Значение **1** указывает на **XML-** столбец.|  
|**is_max**|**int**|Имеет значение, если столбец является столбцом типа данных больших значений (**varchar (max)**, **nvarchar (max)** или **varbinary (max)**). Значение **1** указывает на столбец с большим значением.|  
  
## <a name="see-also"></a>См. также:  
 [sp_articlecolumn &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md)   
 [Системное представление sysarticlecolumns &#40;Transact-SQL&#41;](../../relational-databases/system-tables/sysarticlecolumns-transact-sql.md)  
  
  
