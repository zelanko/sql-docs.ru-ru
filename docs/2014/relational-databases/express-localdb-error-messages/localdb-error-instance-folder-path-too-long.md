---
title: LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: c178a308-8d99-47fc-8a49-5a480dc592f6
caps.latest.revision: 8
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 68e4599f184ce388d1f295e44ff8f570186cd280
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36192255"
---
# <a name="localdberrorinstancefolderpathtoolong"></a>LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG
    
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
  
  