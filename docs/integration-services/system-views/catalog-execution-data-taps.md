---
title: "Catalog.execution_data_taps | Документы Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 54226c01-5b8f-4730-8a5f-1da2613f9689
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: bc949b9b6111c65d6faa43a118efd03068630fe0
ms.contentlocale: ru-ru
ms.lasthandoff: 09/26/2017

---
# <a name="catalogexecutiondatataps"></a>catalog.execution_data_taps
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Отображает сведения для каждого отвода данных, определенного в выполнении.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|data_tap_id|**bigint**|Уникальный идентификатор отвода данных.|  
|execution_id|**bigint**|Уникальный идентификатор для экземпляра выполнения.|  
|путь к пакету|**nvarchar(max)**|Путь к пакету для задачи потока данных, в которой выполняется отвод данных.|  
|dataflow_path_id_string|**nvarchar(4000)**|Строка идентификации пути потока данных.|  
|dataflow_task_guid|**uniqueidentifier**|Уникальный идентификатор задачи потока данных.|  
|max_rows|**int**|Число записываемых строк. Если это значение не задано, фиксируются все строки.|  
|filename|**nvarchar(4000)**|Имя файла дампа данных. Дополнительные сведения см. в статье [Generating Dump Files for Package Execution](../../integration-services/troubleshooting/generating-dump-files-for-package-execution.md).|  
  
## <a name="permissions"></a>Permissions  
 Это представление требует применения одного из следующих разрешений:  
  
-   Разрешение READ на экземпляр выполнения  
  
-   Членство в **ssis_admin** роли базы данных  
  
-   Членство в **sysadmin** роли сервера  
  
> [!NOTE]  
>  Наличие разрешения на выполнение операции на сервере подразумевает наличие разрешения на просмотр сведений об этой операции. Действует защита на уровне строки. Отображаются только строки, на которые у вас имеется разрешение.  
  
## <a name="see-also"></a>См. также:  
 [Создание файлов дампа для выполнения пакетов](../../integration-services/troubleshooting/generating-dump-files-for-package-execution.md)  
  
  

