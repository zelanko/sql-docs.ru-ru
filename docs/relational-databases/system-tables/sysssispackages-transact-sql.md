---
description: sysssispackages (Transact-SQL)
title: sysssispackages (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysdtspackages90_TSQL
- sysdtspackages90
dev_langs:
- TSQL
helpviewer_keywords:
- sysssispackages system table
ms.assetid: 66155dcd-dcdb-4e33-a242-1625828ad8d2
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: d1a1bda3bfea233f7a586a8147f268fbdb1e6ade
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88419038"
---
# <a name="sysssispackages-transact-sql"></a>sysssispackages (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Содержит по одной строке для каждого пакета, сохраненного в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Эта таблица хранится в базе данных **msdb** .  
  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Уникальный идентификатор пакета.|  
|**id**|**uniqueidentifier**|Идентификатор GUID пакета.|  
|**description**|**nvarchar**|Необязательное описание пакета.|  
|**креатедате**|**datetime**|Дата создания пакета.|  
|**FolderId**|**uniqueidentifier**|Идентификатор GUID логической папки, в которой среда [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] содержит данный пакет.|  
|**ownersid**|**varbinary**|Уникальный идентификатор защиты пользователя, создавшего пакет.|  
|**packagedata**|**image**|Пакет.|  
|**packageformat**|**int**|Формат, в котором пакет сохранен:<br /><br /> Значение 2 указывает, что пакет сохранен в [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] формате.<br /><br /> Значение 3 указывает, что пакет сохранен в формате [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] или более поздней версии.|  
|**packagetype**|**int**|Клиент, создавший пакет. Возможны следующие значения:<br /><br /> 0 (значение по умолчанию);<br /><br /> 1 ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Мастер импорта и экспорта)<br /><br /> 3 ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] репликация)<br /><br /> 5 ( [!INCLUDE[ssIS](../../includes/ssis-md.md)] конструктор)<br /><br /> 6 (конструктор или мастер планов обслуживания базы данных).<br /><br /> <br /><br /> Обратите внимание, что значения в этом столбце соответствуют <xref:Microsoft.SqlServer.Dts.Runtime.DTSPackageType> перечислению.|  
|**vermajor**|**int**|Последняя основная версия пакета.|  
|**verminor**|**int**|Последняя вспомогательная версия пакета.|  
|**verbuild**|**int**|Последняя сборка пакета.|  
|**vercomments**|**nvarchar**|Примечания о версии пакета.|  
|**verid**|**uniqueidentifier**|Идентификатор GUID версии пакета.|  
|**IsEncrypted**|**bit**|Логическое значение, показывающее, зашифрован ли пакет.|  
|**readrolesid**|**varbinary**|Роль [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], которая может загрузить пакет.|  
|**writerolesid**|**varbinary**|Роль [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], которая может сохранить пакет.|  
  
## <a name="see-also"></a>См. также:  
 [Пакеты служб Integration Services (SSIS)](../../integration-services/integration-services-ssis-packages.md)  
  
  
