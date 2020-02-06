---
title: MSSQLSERVER_5231 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 5231 (Database Engine error)
ms.assetid: 6954ae84-ed0b-4f4c-9d0a-e73f3d71476c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2cd4a8208925f6e0fe0a0fed4b162b4eb7361009
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "68122956"
---
# <a name="mssqlserver_5231"></a>MSSQLSERVER_5231
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|5231|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|DBCC4_DEADLOCK_SKIPPED_OBJECT|  
|Текст сообщения|Объект с идентификатором O_ID (объект "NAME"): произошла взаимоблокировка при попытке заблокировать данный объект для проверки. Этот объект пропущен и останется необработанным.|  
  
## <a name="explanation"></a>Объяснение  
Произошла взаимоблокировка при попытке команды DBCC заблокировать объект, команда DBCC была выбрана жертвой взаимоблокировки. Объект не будет обработан.  
  
## <a name="user-action"></a>Действие пользователя  
None  
  
