---
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
ms.openlocfilehash: 21487ba46e53997ebb50403cc4eaf1ae54f0a103
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68029639"
---
# <a name="sysssispackages-transact-sql"></a>sysssispackages (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит по одной строке для каждого пакета, сохраненного [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]в. Эта таблица хранится в базе данных **msdb** .  
  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Уникальный идентификатор пакета.|  
|**идентификатор**|**uniqueidentifier**|Идентификатор GUID пакета.|  
|**nописание**|**nvarchar**|Необязательное описание пакета.|  
|**креатедате**|**datetime**|Дата создания пакета.|  
|**FolderId**|**uniqueidentifier**|Идентификатор GUID логической папки, в которой среда [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] содержит данный пакет.|  
|**ownersid**|**varbinary**|Уникальный идентификатор защиты пользователя, создавшего пакет.|  
|**packagedata**|**image**|Пакет.|  
|**packageformat**|**int**|Формат, в котором пакет сохранен:<br /><br /> Значение 2 указывает, что пакет сохранен в [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] формате.<br /><br /> Значение 3 указывает, что пакет сохранен в формате [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]или более поздней версии.|  
|**packagetype**|**int**|Клиент, создавший пакет. Возможны следующие значения:<br /><br /> 0 (значение по умолчанию);<br /><br /> 1 ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] мастер импорта и экспорта)<br /><br /> 3 ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] репликация)<br /><br /> 5 ([!INCLUDE[ssIS](../../includes/ssis-md.md)] конструктор)<br /><br /> 6 (конструктор или мастер планов обслуживания базы данных).<br /><br /> <br /><br /> Обратите внимание, что значения в этом столбце соответствуют <xref:Microsoft.SqlServer.Dts.Runtime.DTSPackageType> перечислению.|  
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
  
  
