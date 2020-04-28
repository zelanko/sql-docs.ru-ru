---
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
ms.openlocfilehash: 8a0505b8316254090fe5f2310fa68011d8289679
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68129552"
---
# <a name="sysarticlecolumns-system-view-transact-sql"></a>Системное представление sysarticlecolumns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

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
  
  
