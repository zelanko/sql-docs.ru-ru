---
title: LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: reference
ms.assetid: c178a308-8d99-47fc-8a49-5a480dc592f6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 94439a6981a2cf891a55bcbda7498db83e1fa52e
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2018
ms.locfileid: "52803736"
---
# <a name="localdberrorinstancefolderpathtoolong"></a>LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|260|  
|Источник события|Среда выполнения локальной базы данных SQL Server 12.0|  
|Компонент|API среды выполнения локальной базы данных|  
|Текст сообщения|Длина полного пути к папке экземпляра локальной базы данных превышает MAX_PATH. Экземпляр должен храниться в папке: %%LOCALAPPDATA%%\Microsoft\Microsoft SQL Server локальный DB\Instances\\< имя экземпляра\>.|  
  
## <a name="explanation"></a>Объяснение  
 Длина пути к месту хранения экземпляра больше MAX_PATH.  
  
## <a name="user-action"></a>Действие пользователя  
 Создайте новый путь, длина которого меньше MAX_PATH.  
  
  
