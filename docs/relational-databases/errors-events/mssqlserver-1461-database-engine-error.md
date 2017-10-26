---
title: "MSSQLSERVER_1461 | Документация Майкрософт"
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 1461 (Database Engine error)
ms.assetid: fce10907-4753-441b-b624-f28e00ed7520
caps.latest.revision: 14
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 77d6dc184ece81e27083635c9cf049fd079d3e33
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver1461"></a>MSSQLSERVER_1461
  
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
  

