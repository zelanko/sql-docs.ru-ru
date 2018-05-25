---
title: LOCALDB_ERROR_INSTANCE_ALREADY_SHARED | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: performance
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 35b4d6fa-ebb9-49d3-aaab-d4e37b6f3760
caps.latest.revision: 7
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: fdc357ad5d54ebd8710b52e824ee1c5b4d2a5e0d
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2018
---
# <a name="localdberrorinstancealreadyshared"></a>LOCALDB_ERROR_INSTANCE_ALREADY_SHARED
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|284|  
|Источник события|Среда выполнения локальной базы данных SQL Server 12.0|  
|Компонент|API среды выполнения локальной базы данных|  
|Текст сообщения|Указанный экземпляр локальной базы данных уже используется совместно.|  
  
## <a name="explanation"></a>Объяснение  
 Указанный экземпляр локальной базы данных уже используется совместно под другим общим именем.  
  
## <a name="user-action"></a>Действие пользователя  
 Отключить включенный совместный доступ к экземпляру, прежде чем снова предоставлять его в совместный доступ под другим общим именем.  
  
  
