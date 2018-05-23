---
title: MSSQLSERVER_1461 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 1461 (Database Engine error)
ms.assetid: fce10907-4753-441b-b624-f28e00ed7520
caps.latest.revision: 14
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 17c5d9e85013e7e977f07e9000c896d46d1b26c0
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2018
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
  
