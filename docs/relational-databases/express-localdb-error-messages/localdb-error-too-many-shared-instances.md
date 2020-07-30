---
title: LOCALDB_ERROR_TOO_MANY_SHARED_INSTANCES | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: reference
ms.assetid: c1595263-6264-4a43-9535-5eb76ece3a57
author: stevestein
ms.author: sstein
ms.openlocfilehash: 48308ffe551f55b5526fccc634ad84747b9bc976
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/28/2020
ms.locfileid: "87245988"
---
# <a name="localdb_error_too_many_shared_instances"></a>LOCALDB_ERROR_TOO_MANY_SHARED_INSTANCES
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
    
## <a name="details"></a>Сведения  
  
| attribute | Значение |
| --------- | ----- |
|Название продукта|SQL Server|  
|Идентификатор события|287|  
|Источник события|Среда выполнения локальной базы данных SQL Server 12.0|  
|Компонент|API среды выполнения локальной базы данных|  
|Текст сообщения|Общих экземпляров слишком много, и создать уникальное имя пользовательского экземпляра не удается. Отключите совместный доступ к некоторым из существующих общих экземпляров.|  
  
## <a name="explanation"></a>Объяснение  
 Общих экземпляров слишком много, и создать уникальное имя пользовательского экземпляра не удается.  
  
## <a name="user-action"></a>Действие пользователя  
 Отключите совместный доступ к одному или нескольким общим экземплярам среды выполнения локальной базы данных и повторите попытку.  
  
  
