---
title: sys.resource_usage (база данных SQL Azure) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.service: sql-database
ms.reviewer: ''
ms.topic: language-reference
f1_keywords:
- sys.resource_usage_TSQL
- resource_usage
- sys.resource_usage
- resource_usage_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- resource_usage
- sys.resource_usage
ms.assetid: b90147a3-fd8e-408e-961d-5c7000e068ad
author: julieMSFT
ms.author: jrasnick
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 3be4ff07923759af53b929852d4dbaa4088a77f2
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67904421"
---
# <a name="sysresourceusage-azure-sql-database"></a>sys.resource_usage (база данных SQL Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

    
> [!IMPORTANT]
>  Этот компонент доступен в состоянии предварительной версии. Не полагайтесь на конкретную реализацию этого компонента, так как он может быть изменен или удален в следующей версии.  
> 
>  В предварительной версии группа эксплуатации [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] может отключать и включать сбор данных для данного динамического административного представления:  
> 
>  -   Если сбор данных включен, представление DMV возвращает текущие данные в том виде, в каком они были собраны.  
> -   Если сбор данных включен, представление DMV возвращает данные предыстории, которые могут устареть.  
  
 Предоставляет почасовые сводные данные по использованию ресурсов для пользовательских баз данных на текущем сервере. Исторические данные будут храниться в течение 90 дней.  
  
 Для каждой пользовательской базы данных существует одна строка для каждого часа в непрерывном формате. Даже если база данных не использовалась в течение этого часа, для него существует соответствующая строка, а значение usage_in_seconds для этой базы данных будет равно 0. Сведения об использовании хранилища и номере SKU добавляются для часа соответствующим образом.  
  
|Столбцы|Тип данных|Описание|  
|-------------|---------------|-----------------|  
|time|**datetime**|Время (UTC) в почасовых приращениях.|  
|database_name|**nvarchar**|Имя пользовательской базы данных.|  
|sku|**nvarchar**|Имя SKU. Допустимы следующие значения:<br /><br /> Интернет<br /><br /> Business Edition<br /><br /> Basic<br /><br /> Standard<br /><br /> Premium|  
|usage_in_seconds|**int**|Время ЦП, использованное в течение часа.<br /><br /> Примечание. Этот столбец является устаревшим для версии 11 и не относится к версии 12. **Значение всегда имеет значение 0.**|  
|storage_in_megabytes|**decimal**|Максимальный объем хранилища в течение часа, включающий данные базы данных, индексы, хранимые процедуры и метаданные.|  
  
## <a name="permissions"></a>Разрешения  
 Это представление доступно для всех ролей пользователей с разрешениями на подключение к виртуальной **master** базы данных.  
  
  
