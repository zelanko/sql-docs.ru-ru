---
description: catalog.execution_data_taps
title: catalog.execution_data_taps | Документы Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 54226c01-5b8f-4730-8a5f-1da2613f9689
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d73abfb0ee03e645bcc8d69c3415b7c4d737f055
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88495209"
---
# <a name="catalogexecution_data_taps"></a>catalog.execution_data_taps 

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Отображает сведения для каждого отвода данных, определенного в выполнении.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|data_tap_id|**bigint**|Уникальный идентификатор отвода данных.|  
|execution_id|**bigint**|Уникальный идентификатор для экземпляра выполнения.|  
|путь к пакету|**nvarchar(max)**|Путь к пакету для задачи потока данных, в которой выполняется отвод данных.|  
|dataflow_path_id_string|**nvarchar(4000)**|Строка идентификации пути потока данных.|  
|dataflow_task_guid|**uniqueidentifier**|Уникальный идентификатор задачи потока данных.|  
|max_rows|**int**|Число записываемых строк. Если это значение не задано, фиксируются все строки.|  
|filename|**nvarchar(4000)**|Имя файла дампа данных. Дополнительные сведения см. в статье [Generating Dump Files for Package Execution](../../integration-services/troubleshooting/generating-dump-files-for-package-execution.md).|  
  
## <a name="permissions"></a>Разрешения  
 Это представление требует применения одного из следующих разрешений:  
  
-   Разрешение READ на экземпляр выполнения  
  
-   Членство в роли базы данных **ssis_admin**  
  
-   Членство в роли сервера **sysadmin**  
  
> [!NOTE]  
>  Наличие разрешения на выполнение операции на сервере подразумевает наличие разрешения на просмотр сведений об этой операции. Действует защита на уровне строки. Отображаются только строки, на которые у вас имеется разрешение.  
  
## <a name="see-also"></a>См. также:  
 [Создание файлов дампа для выполнения пакетов](../../integration-services/troubleshooting/generating-dump-files-for-package-execution.md)  
  
  
