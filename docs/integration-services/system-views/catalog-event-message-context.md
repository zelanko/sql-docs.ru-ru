---
title: "Catalog.event_message_context | Документы Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 273a54f8-b107-4f36-9461-2b475644760d
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: b7aeb07c52f7ed00aa5a6a29cdd054258cb62d65
ms.contentlocale: ru-ru
ms.lasthandoff: 09/26/2017

---
# <a name="catalogeventmessagecontext"></a>catalog.event_message_context
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Отображает сведения об условиях, которые связаны с сообщениями о событиях выполнения, для выполнений на сервере [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|Context_id|bigint|Уникальный идентификатор контекста ошибки.|  
|Event_message_id|bigint|Уникальный идентификатор сообщения, к которому относится контекст.|  
|Context_depth|int|При увеличении глубины контекст оказывается дальше от ошибки. При возникновении ошибки глубина контекста начинается с 1. Значение 0 указывает состояние пакета да начала выполнения.|  
|Package_path|Nvarchar(max)|Путь к пакету для источника контекста.|  
|Context_type|smallint|Тип объекта, который является источником для контекста. В разделе **примечания** раздел список типов контекста.|  
|Context_source_name|Nvarchar(4000)|Имя объекта, который является источником для контекста.|  
|Context_source_id|Nvarchar(38)|Уникальный идентификатор объекта, который является источником для контекста.|  
|Property_name|Nvarchar(4000)|Имя свойства, связанного с источником контекста.|  
|Property_value|Sql_variant|Значение свойства, связанного с источником контекста.|  
  
## <a name="remarks"></a>Замечания  
 В следующей таблице перечислены типы контекстов.  
  
||||  
|-|-|-|  
|Значение типа контекста|Имя типа|Description|  
|10|Задача|Состояние задачи при возникновении ошибки.|  
|20|Pipeline|Ошибка в компоненте конвейера: компонент источника, назначения или преобразования.|  
|30|Последовательность|Состояние последовательности.|  
|40|Цикл For|Состояние цикла For.|  
|50|Цикл Foreach|Состояние цикла Foreach|  
|60|Пакет|Состояние пакета при возникновении ошибки.|  
|70|Переменная|Значение переменной|  
|80|Диспетчер соединений|Свойства диспетчера соединений.|  
  
## <a name="permissions"></a>Permissions  
 Это представление требует применения одного из следующих разрешений:  
  
-   Разрешение READ по отношению к операции  
  
-   Членство в **ssis_admin** роли базы данных.  
  
-   Членство в **sysadmin** роли сервера.  
  
  

