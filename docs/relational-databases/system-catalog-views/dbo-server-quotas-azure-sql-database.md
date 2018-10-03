---
title: dbo.server_quotas (база данных SQL Azure) | Документация Майкрософт
ms.custom: ''
ms.date: 08/02/2016
ms.prod: ''
ms.reviewer: ''
ms.prod_service: sql-database
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dbo.server_quotas
- dbo.server_quotas_TSQL
- server_quotas
- server_quotas_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- server_quotas
ms.assetid: 34423903-1aaa-4a55-88a6-8228315d84e7
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 02a1d28025fd88694ea4538dc352bc8b7fea51d7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47662618"
---
# <a name="dboserverquotas-azure-sql-database"></a>dbo.server_quotas (база данных SQL Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

    
> **ВАЖНО!** Это относится к  **[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]версии 11 только!**  
>   
>  Этот компонент доступен в состоянии предварительной версии. Не полагайтесь на конкретную реализацию этого компонента, так как он может быть изменен или удален в следующей версии.  
  
 Возвращает типы квот баз данных, доступных на сервере.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|quota_name|**nvarchar**|Тип квоты для сервера. Тип **Premium_database** эквивалентен базам данных с резервированием ресурса.|  
|quota_value|**int**|Количество типов квот, допустимое на сервере.|  
  
## <a name="permissions"></a>Разрешения  
 Это представление доступно для всех ролей пользователей с разрешениями на подключение к виртуальной **master** базы данных.  
  
## <a name="see-also"></a>См. также  
 [Управление базами данных уровня "премиум"](http://go.microsoft.com/fwlink/?LinkID=311927)  
  
  
