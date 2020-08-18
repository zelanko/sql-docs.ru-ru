---
description: MSSQLSERVER_1461
title: MSSQLSERVER_1461 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 1461 (Database Engine error)
ms.assetid: fce10907-4753-441b-b624-f28e00ed7520
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4b44f35552063f34daf0a191a40ac274df461348
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88334360"
---
# <a name="mssqlserver_1461"></a>MSSQLSERVER_1461
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Сведения  
  
| attribute | Значение |  
| :-------- | :---- |  
|Название продукта|SQL Server|  
|Идентификатор события|1461|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|DBM_SAFETY_MISMATCH|  
|Текст сообщения|Обнаружены различные уровни безопасности зеркального отображения базы данных «%.*ls» на нескольких серверах. Будет использован уровень безопасности FULL.|  
  
## <a name="explanation"></a>Объяснение  
Соединения зеркального отображения были разорваны при изменении уровня безопасности транзакций, так как параметры безопасности транзакций не совпадали в основной и зеркальной базах данных. Будет использоваться параметр безопасности по умолчанию с полной безопасностью транзакций. Сеанс будет выполняться в режиме высокого уровня безопасности.  
  
## <a name="user-action"></a>Действие пользователя  
Чтобы выключить безопасность транзакций, повторно выполните инструкцию ALTER DATABASE *имя_базы_данных* SET PARTNER SAFETY OFF в основной базе данных.  
  
