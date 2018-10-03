---
title: catalog.execution_data_statistics | Документы Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 6f51407e-0e4e-4b44-af33-db14c9d40ded
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: f413b5d7d5cb3480adfa8ee37b8fd4af520d6a61
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47721353"
---
# <a name="catalogexecutiondatastatistics"></a>catalog.execution_data_statistics
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Это представление отображает строку каждый раз, когда компонент потока данных передает данные в компонент, находящийся ниже в иерархии, для выполнения данного пакета. Данные в этом представлении могут быть использованы для расчета пропускной способности данных для компонента.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|data_stats_id|**bigint**|Уникальный идентификатор данных.|  
|execution_id|**bigint**|Уникальный идентификатор для экземпляра исполнения.|  
|package_name|**nvarchar(260)**|Имя первого пакета, запущенного во время выполнения.|  
|task_name|**nvarchar(4000)**|Имя задачи потока данных.|  
|dataflow_path_id_string|**nvarchar(4000)**|Строка идентификации пути потока данных.|  
|dataflow_path_name|**nvarchar(4000)**|Имя пути потока данных.|  
|source_component_name|**nvarchar(4000)**|Имя компонента потока данных, который отправил данные.|  
|destination_component_name|**nvarchar(4000)**|Имя компонента потока данных, который получил данные.|  
|rows_sent|**bigint**|Число строк, отправленных из компонента источника.|  
|created_time|**datatimeoffset(7)**|Время, когда были получены значения.|  
|execution_path|**nvarchar(max)**|Путь выполнения компонента.|  
  
## <a name="remarks"></a>Remarks  
  
-   Если существует несколько выходов из компонента, добавляется строка для каждого выхода.  
  
-   По умолчанию, когда начинается выполнение, сведения о количестве переданных строк не регистрируются.  
  
-   Для просмотра этих данных для указанного выполнения пакета установите уровень ведения журнала **Подробно**. Дополнительные сведения см. в разделе [Включение ведения журналов при выполнении пакета на сервере служб SSIS](../../integration-services/performance/integration-services-ssis-logging.md#server_logging).  
  
## <a name="permissions"></a>Разрешения  
 Это представление требует применения одного из следующих разрешений:  
  
-   Разрешение READ на экземпляр выполнения  
  
-   Членство в роли базы данных **ssis_admin**  
  
-   Членство в роли сервера **sysadmin**  
  
> [!NOTE]  
>  Наличие разрешения на выполнение операции на сервере подразумевает наличие разрешения на просмотр сведений об этой операции. Действует защита на уровне строки. Отображаются только строки, на которые у вас имеется разрешение.  
  
  
