---
title: MSSQLSERVER_3937 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 3937 (Database Engine error)
ms.assetid: 312d5bbe-c8de-42db-af4b-4ccb448ce6ef
caps.latest.revision: 12
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 263747514a29b61f82b308078decbe2967c6fb6b
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2018
---
# <a name="mssqlserver3937"></a>MSSQLSERVER_3937
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
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
