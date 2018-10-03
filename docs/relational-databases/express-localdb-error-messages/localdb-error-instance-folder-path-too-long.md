---
title: LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: reference
ms.assetid: c178a308-8d99-47fc-8a49-5a480dc592f6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6d4053fd7633d642c0cc139826ca8e30ed3fa3fa
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47777792"
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
|Текст сообщения|Длина полного пути к папке экземпляра локальной базы данных превышает MAX_PATH. Экземпляр должен храниться в папке: %%LOCALAPPDATA%%\Microsoft\Microsoft SQL Server локальный DB\Instances\\< имя экземпляра\>.|  
  
## <a name="explanation"></a>Объяснение  
 Длина пути к месту хранения экземпляра больше MAX_PATH.  
  
## <a name="user-action"></a>Действие пользователя  
 Создайте новый путь, длина которого меньше MAX_PATH.  
  
  
