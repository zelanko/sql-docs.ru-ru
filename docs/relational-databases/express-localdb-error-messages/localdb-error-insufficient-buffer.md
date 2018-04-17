---
title: LOCALDB_ERROR_INSUFFICIENT_BUFFER | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: localdb
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: ff67bda8-7e5c-4b06-8d7b-9985b6059a98
caps.latest.revision: 8
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4839c6867b571083e8b88c0bb23c767a61b52a0a
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="localdberrorinsufficientbuffer"></a>LOCALDB_ERROR_INSUFFICIENT_BUFFER
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|276|  
|Источник события|Среда выполнения локальной базы данных SQL Server 12.0|  
|Компонент|API среды выполнения локальной базы данных|  
|Текст сообщения|Буфер, переданный методу API экземпляра локальной базы данных, имеет недостаточный размер.|  
  
## <a name="explanation"></a>Объяснение  
 Размер входного буфера является недостаточным, а усечение не было запрошено.  
  
## <a name="user-action"></a>Действие пользователя  
 Предоставьте буфер указанного размера.  
  
  
