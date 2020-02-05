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
ms.openlocfilehash: 84f983c9b450e625fdca08c46720a1cf22e8b84c
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "68098316"
---
# <a name="mssqlserver_3413"></a>MSSQLSERVER_3413
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|3413|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|MARKDB|  
|Текст сообщения|Идентификатор базы данных %d. Не удалось пометить базу данных как подозрительную. Не удалось выполнить просмотр Getnext NC по sys.databases.database_id. Просмотрите предыдущие ошибки в журнале ошибок для определения причины и устраните выявленные проблемы.|  
  
## <a name="explanation"></a>Объяснение  
При попытке пометить в каталоге пользовательскую базу данных признаком SUSPECT произошел непредвиденный сбой. Состояние SUSPECT установлено не будет.  
  
## <a name="user-action"></a>Действие пользователя  
Для исправления этой неполадки см. предыдущие ошибки.  
  
