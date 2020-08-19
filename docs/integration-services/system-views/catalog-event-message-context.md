---
description: catalog.event_message_context
title: catalog.event_message_context | Документы Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 273a54f8-b107-4f36-9461-2b475644760d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e8728d1ddbc8ae7643d0ee660266357d42125c89
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88495333"
---
# <a name="catalogevent_message_context"></a>catalog.event_message_context 

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Отображает сведения об условиях, которые связаны с сообщениями о событиях выполнения, для выполнений на сервере [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|Context_id|BIGINT|Уникальный идентификатор контекста ошибки.|  
|Event_message_id|BIGINT|Уникальный идентификатор сообщения, к которому относится контекст.|  
|Context_depth|INT|При увеличении глубины контекст оказывается дальше от ошибки. При возникновении ошибки глубина контекста начинается с 1. Значение 0 указывает состояние пакета да начала выполнения.|  
|Package_path|Nvarchar(max)|Путь к пакету для источника контекста.|  
|Context_type|smallint|Тип объекта, который является источником для контекста. Список типов контекста см. в разделе **Примечания**.|  
|Context_source_name|Nvarchar(4000)|Имя объекта, который является источником для контекста.|  
|Context_source_id|Nvarchar(38)|Уникальный идентификатор объекта, который является источником для контекста.|  
|Property_name|Nvarchar(4000)|Имя свойства, связанного с источником контекста.|  
|Property_value|Sql_variant|Значение свойства, связанного с источником контекста.|  
  
## <a name="remarks"></a>Комментарии  
 В следующей таблице перечислены типы контекстов.  
  
|Значение типа контекста|Имя типа|Описание|  
|-|-|-|  
|10|Задача|Состояние задачи при возникновении ошибки.|  
|20|Pipeline|Ошибка компонента конвейера: компонент источника, назначения или преобразования.|  
|30|Sequence|Состояние последовательности.|  
|40|Цикл For|Состояние цикла For.|  
|50|Цикл Foreach|Состояние цикла Foreach|  
|60|Пакет|Состояние пакета при возникновении ошибки.|  
|70|Переменная|Значение переменной|  
|80|Диспетчер соединений|Свойства диспетчера соединений.|  
  
## <a name="permissions"></a>Разрешения  
 Это представление требует применения одного из следующих разрешений:  
  
-   Разрешение READ по отношению к операции  
  
-   Членство в роли базы данных **ssis_admin**.  
  
-   Членство в роли сервера **sysadmin**.  
  
  
