---
title: dbo. sysdac_instances (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dbo.sysdac_instances_TSQL
- sysdac_instances
- sysdac_instances_TSQL
- dbo.sysdac_instances
dev_langs:
- TSQL
helpviewer_keywords:
- dbo.sysdac_instances
- sysdac_instances
ms.assetid: 28285f3d-3889-439f-8b24-3bdef08e46b4
author: stevestein
ms.author: sstein
ms.openlocfilehash: b1530e58597947a7e19f4ca264808fbfefd164ef
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68033111"
---
# <a name="data-tier-application-views---dbosysdac_instances"></a>Представления приложения уровня данных — dbo. sysdac_instances
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Отображает по одной строке для каждого экземпляра приложения уровня данных (DAC), развернутого на экземпляре [!INCLUDE[ssDE](../../includes/ssde-md.md)]. sysdac_instances принадлежит схеме dbo в базе данных msdb. В следующей таблице описаны столбцы в представлении sysdac_instances.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|instance_id|**UNIQUEIDENTIFIER**|Идентификатор экземпляра DAC.|  
|имя_экземпляра|**имеет sysname**|Имя экземпляра приложения уровня данных, указанное при развертывании DAC.|  
|type_name|**имеет sysname**|Имя DAC, указанное при создании пакета DAC.|  
|type_version|**nvarchar (64)**|Версия DAC, указанная при создании пакета DAC.|  
|description|**nvarchar (4000)**|Описание DAC, записанное при создании пакета DAC.|  
|type_stream|**varbinary(max)**|Битовый поток, который содержит закодированное представление логических объектов, таких как таблицы и представления, содержащихся в DAC.|  
|date_created|**datetime**|Дата и время создания экземпляра DAC.|  
|created_by|**имеет sysname**|Имя входа, создавшее экземпляр DAC.|  
|database_name|**имеет sysname**|Имя базы данных, созданной для экземпляра DAC.|  
  
## <a name="remarks"></a>Remarks  
 DAC включает тип DAC, который представляет собой определение логических объектов уровня данных, используемых приложением, таких как таблицы и представления. Пакет DAC представляет собой файл, используемый для развертывания DAC. Пакет DAC содержит представление всех логических объектов, содержащихся в типе DAC. Пакет DAC может использоваться для развертывания одной или нескольких копий или экземпляров DAC на экземпляре компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Каждый экземпляр DAC, развернутый одним и тем же пакетом DAC, имеет одинаковый с другими экземплярами тип, но ему присваиваются уникальные имя и идентификатор экземпляра.  
  
## <a name="permissions"></a>Разрешения  
 Требует членства в предопределенной роли сервера sysadmin для просмотра всех столбцов. Члены роли public могут просматривать столбцы instance_name, description и type_version.  
  
## <a name="see-also"></a>См. также:  
 [Приложения уровня данных](../../relational-databases/data-tier-applications/data-tier-applications.md)   
 [Представления приложений уровня данных &#40;Transact-SQL&#41;](https://msdn.microsoft.com/library/0de01328-d7a6-4677-b7a0-dcd3098c23d4)  
  
  
