---
title: "Catalog.operation_messages (база данных SSISDB) | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- catalog.operation_messages view [Integration Services]
- operation_messages view [Integration Services]
ms.assetid: 0b3cbe38-ce24-47ca-83ef-6538a5299d1a
caps.latest.revision: 27
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 235e9896cbf075bdc26e3df120b23091b8e82d6d
ms.contentlocale: ru-ru
ms.lasthandoff: 09/26/2017

---
# <a name="catalogoperationmessages-ssisdb-database"></a>catalog.operation_messages (база данных SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Отображает сообщения, которые заносятся в журнал при выполнении операций в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|operation_message_id|**bigint**|Уникальный идентификатор сообщения.|  
|operation_id|**bigint**|Уникальный идентификатор операции.|  
|message_time|**DateTimeOffset(7)**|Время создания сообщения.|  
|message_type|**smallint**|Тип отображаемого сообщения.|  
|message_source_type|**smallint**|Идентификатор типа источника сообщения.|  
|message|**nvarchar(max)**|Текст сообщения.|  
|extended_info_id|**bigint**|Идентификатор дополнительных сведений, которые относятся к сообщению операции найден в [extended_operation_info](../../integration-services/system-views/catalog-extended-operation-info-ssisdb-database.md) представления.|  
  
## <a name="remarks"></a>Замечания  
 В этом представлении отображается по одной строке для каждого из сообщений, которые внесены в журнал во время выполнения операции в каталоге. Сообщения могут формироваться сервером, процессом выполнения пакета или подсистемой выполнения.  
  
 В этом представлении отображаются следующие типы сообщений:  
  
|**message_type** значение|Description|  
|-----------------------------|-----------------|  
|-1|Неизвестно|  
|120|Ошибка|  
|110|Предупреждение|  
|70|Сведения|  
|10|Предварительная проверка|  
|20|Последующая проверка|  
|30|До выполнения|  
|40|После выполнения|  
|60|Ход выполнения|  
|50|StatusChange|  
|100|QueryCancel|  
|130|TaskFailed|  
|90|Диагностика|  
|200|Другой|  
|140|DiagnosticEx<br /><br /> При каждом выполнении дочернего пакета задачей «Выполнение пакета» она заносит в журнал это событие. Сообщение о событии состоит из значений параметров, передаваемых дочерним пакетам.<br /><br /> Значением столбца сообщения для DiagnosticEx является XML-текст.|  
|400|NonDiagnostic|  
|80|VariableValueChanged|  
  
 В этом представлении отображаются следующие типы источников сообщений.  
  
|**message_source_type**|Description|  
|-------------------------------|-----------------|  
|10|Начальные API-интерфейсы, такие как T-SQL и хранимые процедуры CLR|  
|20|Внешний процесс, используемый для запуска пакета (ISServerExec.exe)|  
|30|Объекты уровня пакета|  
|40|Задачи потока управления|  
|50|Контейнеры потока управления|  
|60|Задача потока данных|  
  
## <a name="permissions"></a>Permissions  
 Это представление требует применения одного из следующих разрешений:  
  
-   Разрешение READ по отношению к операции  
  
-   Членство в **ssis_admin** роли базы данных  
  
-   Членство в **sysadmin** роли сервера  
  
> [!NOTE]  
>  Наличие разрешения на выполнение операции на сервере подразумевает наличие разрешения на просмотр сведений об этой операции. Действует защита на уровне строки. Отображаются только строки, на которые у вас имеется разрешение.  
  
  

