---
title: MSSQLSERVER_3937 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 3937 (Database Engine error)
ms.assetid: 312d5bbe-c8de-42db-af4b-4ccb448ce6ef
caps.latest.revision: 12
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 90e446493651140fff2fa670847e0a25d588f381
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36194940"
---
# <a name="mssqlserver3937"></a>MSSQLSERVER_3937
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|MSSQLSERVER|  
|Идентификатор события|3937|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|XACT_FILESTREAM_ROLLBACK_ERROR|  
|Текст сообщения|При уведомлении драйвера фильтра FILESTREAM об откате транзакции произошла ошибка. Код ошибки: 0x%0x.|  
  
## <a name="explanation"></a>Объяснение  
 Драйвер RsFx возвратил ошибку при выдаче уведомления об откате транзакции. Возможно, это вызвано недостатком ресурсов. Это может привести к небольшой утечке памяти в драйвере фильтра RsFx, но память будет освобождена, когда завершится процесс sqlservr.exe, создавший транзакцию.  
  
## <a name="user-action"></a>Действие пользователя  
  