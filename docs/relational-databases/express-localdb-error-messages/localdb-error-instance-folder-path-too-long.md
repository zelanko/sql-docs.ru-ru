---
title: LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG | Документы Microsoft
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: localdb
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: c178a308-8d99-47fc-8a49-5a480dc592f6
caps.latest.revision: 10
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 8272aa1c8b4c2b395b7e14f990e7916f376f378f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="localdberrorinstancefolderpathtoolong"></a>LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|260|  
|Источник события|Среда выполнения локальной базы данных SQL Server 12.0|  
|Компонент|API среды выполнения локальной базы данных|  
|Текст сообщения|Длина полного пути к папке экземпляра локальной базы данных превышает MAX_PATH. Экземпляр должен храниться в папке: %%LOCALAPPDATA%%\Microsoft\Microsoft SQL Server локального DB\Instances\\< имя экземпляра\>.|  
  
## <a name="explanation"></a>Объяснение  
 Длина пути к месту хранения экземпляра больше MAX_PATH.  
  
## <a name="user-action"></a>Действие пользователя  
 Создайте новый путь, длина которого меньше MAX_PATH.  
  
  
