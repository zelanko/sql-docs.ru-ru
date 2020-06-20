---
title: MSSQLSERVER_3937 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3937 (Database Engine error)
ms.assetid: 312d5bbe-c8de-42db-af4b-4ccb448ce6ef
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: cac466e6eb50ad4b7a8848a1159963cb0fd35e22
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85033297"
---
# <a name="mssqlserver_3937"></a>MSSQLSERVER_3937
    
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
  
