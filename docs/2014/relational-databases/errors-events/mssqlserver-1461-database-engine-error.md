---
title: MSSQLSERVER_1461 | Документация Майкрософт
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
- 1461 (Database Engine error)
ms.assetid: fce10907-4753-441b-b624-f28e00ed7520
caps.latest.revision: 15
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 663aeec8ff61ce1717392c32d4f97e71403d1b5c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36099281"
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
  
  