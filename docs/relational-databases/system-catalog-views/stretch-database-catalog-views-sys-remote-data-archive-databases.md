---
title: sys. remote_data_archive_databases (Transact-SQL) | Документация Майкрософт
description: Узнайте, как sys. remote_data_archive_databases содержит по одной строке для каждой удаленной базы данных, в которой хранятся данные из локальной базы данных с поддержкой Stretch.
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.technology: stored-procedures
ms.topic: language-reference
f1_keywords:
- sys.remote_data_archive_databases
- sys.remote_data_archive_databases_TSQL
- remote_data_archive_databases
- remote_data_archive_databases_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.remote_data_archive_databases catalog view
ms.assetid: 25bffb0c-9821-40b4-88cf-75f854891a09
author: pmasl
ms.author: pelopes
ms.reviewer: mikeray
ms.openlocfilehash: e192a70c1d8f46b7ad89844a3b38019ab6364cc1
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/28/2020
ms.locfileid: "87248153"
---
# <a name="stretch-database-catalog-views---sysremote_data_archive_databases"></a>Stretch Database представлений каталога — sys. remote_data_archive_databases
[!INCLUDE [sqlserver2016](../../includes/applies-to-version/sqlserver2016.md)]

  Содержит по одной строке для каждой удаленной базы данных, в которой хранятся данные из локальной базы данных с поддержкой Stretch.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**remote_database_id**|**int**|Автоматически созданный локальный идентификатор удаленной базы данных.|  
|**remote_database_name**|**sysname**|Имя удаленной базы данных.|  
|**data_source_id**|**int**|Источник данных, используемый для подключения к удаленному серверу|  
  
## <a name="see-also"></a>См. также:  
 [База данных Stretch](../../sql-server/stretch-database/stretch-database.md)  
  
  
