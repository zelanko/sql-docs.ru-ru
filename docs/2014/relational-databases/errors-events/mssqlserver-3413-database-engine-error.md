---
title: MSSQLSERVER_3413 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 3413 (Database Engine error)
ms.assetid: 3fa07637-ba93-4633-aaf2-ade7d18bc487
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2af9a604c511c50b542fbacd547afb3e09d7ea54
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62868374"
---
# <a name="mssqlserver3413"></a>MSSQLSERVER_3413
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|3413|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|MARKDB|  
|Текст сообщения|Идентификатор базы данных %d. Не удалось пометить базу данных как подозрительную. Не удалось выполнить просмотр Getnext NC по sys.databases.database_id. Просмотрите предыдущие ошибки в журнале ошибок для определения причины и устраните выявленные проблемы.|  
  
## <a name="explanation"></a>Объяснение  
При попытке пометить в каталоге пользовательскую базу данных признаком SUSPECT произошел непредвиденный сбой. Состояние SUSPECT установлено не будет.  
  
## <a name="user-action"></a>Действие пользователя  
Для исправления этой неполадки см. предыдущие ошибки.  
  
