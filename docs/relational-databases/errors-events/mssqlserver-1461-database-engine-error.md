---
title: "MSSQLSERVER_1461 | Документация Майкрософт"
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 1461 (Database Engine error)
ms.assetid: fce10907-4753-441b-b624-f28e00ed7520
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 47dcf5e0a055e6decd359ffc9479387194776428
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver1461"></a>MSSQLSERVER_1461
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|1461|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|DBM_SAFETY_MISMATCH|  
|Текст сообщения|Обнаружены различные уровни безопасности зеркального отображения базы данных «%.*ls» на нескольких серверах. Будет использован уровень безопасности FULL.|  
  
## <a name="explanation"></a>Объяснение  
Соединения зеркального отображения были разорваны при изменении уровня безопасности транзакций, так как параметры безопасности транзакций не совпадали в основной и зеркальной базах данных. Будет использоваться параметр безопасности по умолчанию с полной безопасностью транзакций. Сеанс будет выполняться в режиме высокого уровня безопасности.  
  
## <a name="user-action"></a>Действие пользователя  
Чтобы выключить безопасность транзакций, повторно выполните инструкцию ALTER DATABASE *имя_базы_данных* SET PARTNER SAFETY OFF в основной базе данных.  
  
