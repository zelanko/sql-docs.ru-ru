---
description: catalog.operation_messages (база данных SSISDB)
title: catalog.operation_messages (база данных SSISDB) | Документы Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
helpviewer_keywords:
- catalog.operation_messages view [Integration Services]
- operation_messages view [Integration Services]
ms.assetid: 0b3cbe38-ce24-47ca-83ef-6538a5299d1a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c7b15cffb2f04217586e58fd53ff5b5224c66527
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88422028"
---
# <a name="catalogoperation_messages-ssisdb-database"></a>catalog.operation_messages (база данных SSISDB)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Отображает сообщения, которые заносятся в журнал при выполнении операций в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|operation_message_id|**bigint**|Уникальный идентификатор сообщения.|  
|operation_id|**bigint**|Уникальный идентификатор операции.|  
|message_time|**datetimeoffset(7)**|Время создания сообщения.|  
|message_type|**smallint**|Тип отображаемого сообщения.|  
|message_source_type|**smallint**|Идентификатор типа источника сообщения.|  
|сообщение|**nvarchar(max)**|Текст сообщения.|  
|extended_info_id|**bigint**|Идентификатор дополнительных сведений, которые относятся к сообщению об операции и находятся в представлении [extended_operation_info](../../integration-services/system-views/catalog-extended-operation-info-ssisdb-database.md).|  
  
## <a name="remarks"></a>Комментарии  
 В этом представлении отображается по одной строке для каждого из сообщений, которые внесены в журнал во время выполнения операции в каталоге. Сообщения могут формироваться сервером, процессом выполнения пакета или подсистемой выполнения.  
  
 В этом представлении отображаются следующие типы сообщений:  
  
|Значение **message_type**|Описание|  
|-----------------------------|-----------------|  
|-1|Неизвестно|  
|120|Error|  
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
  
|**message_source_type**|Описание|  
|-------------------------------|-----------------|  
|10|Начальные API-интерфейсы, такие как T-SQL и хранимые процедуры CLR|  
|20|Внешний процесс, используемый для запуска пакета (ISServerExec.exe)|  
|30|Объекты уровня пакета|  
|40|Задачи потока управления|  
|50|Контейнеры потока управления|  
|60|Задача потока данных|  
  
## <a name="permissions"></a>Разрешения  
 Это представление требует применения одного из следующих разрешений:  
  
-   Разрешение READ по отношению к операции  
  
-   Членство в роли базы данных **ssis_admin**  
  
-   Членство в роли сервера **sysadmin**  
  
> [!NOTE]  
>  Наличие разрешения на выполнение операции на сервере подразумевает наличие разрешения на просмотр сведений об этой операции. Действует защита на уровне строки. Отображаются только строки, на которые у вас имеется разрешение.  
  
  
