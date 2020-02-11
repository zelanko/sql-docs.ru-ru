---
title: sys. backup_devices (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- backup_devices_TSQL
- backup_devices
- sys.backup_devices
- sys.backup_devices_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- backup devices [SQL Server], viewing information
- sys.backup_devices catalog view
ms.assetid: 457edaa4-aca1-4bd3-bf8d-734490b80fcd
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b70d87a6f1a72662c1ca466a532d3050b4fe58ab
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67942582"
---
# <a name="sysbackup_devices-transact-sql"></a>sys.backup_devices (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит по одной строке для каждого устройства резервного копирования, **** зарегистрированного с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]sp_addumpdevice или созданного в.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**name**|**имеет sysname**|Имя устройства резервного копирования. Уникально в пределах набора.|  
|**type**|**tinyint**|Тип устройства резервного копирования:<br /><br /> 2 = диск;<br /><br /> 3 = дискета (устаревший);<br /><br /> 5 = лента;<br /><br /> 6 = канальное устройство (устаревший);<br /><br /> 7 = виртуальное устройство (для дополнительного использования сторонними поставщиками резервных копий).<br /><br /> Обычно используются только диск (2) и лента (5).|  
|**type_desc**|**nvarchar (60)**|Описание типа устройства резервного копирования:<br /><br /> DISK;<br /><br /> DISKETTE (устаревшее);<br /><br /> TAPE;<br /><br /> PIPE (устаревшее);<br /><br /> VIRTUAL_DEVICE (для дополнительного использования сторонними поставщиками резервных копий).<br /><br /> Обычно используются только DISK и TAPE.|  
|**physical_name**|**nvarchar(260)**|Физическое имя файла или пути в устройстве резервного копирования.|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]Дополнительные сведения см. в разделе [Настройка видимости метаданных](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также:  
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [&#41;BACKUP &#40;Transact-SQL](../../t-sql/statements/backup-transact-sql.md)   
 [Устройства резервного копирования &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-devices-sql-server.md)   
 [sp_addumpdevice &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql.md)   
 [Представления каталога баз данных и файлов &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/databases-and-files-catalog-views-transact-sql.md)   
 [Часто задаваемые вопросы о запросах к системному каталогу сервера SQL Server](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
