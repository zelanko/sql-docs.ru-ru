---
title: MSSQLSERVER_5231 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 5231 (Database Engine error)
ms.assetid: 6954ae84-ed0b-4f4c-9d0a-e73f3d71476c
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 6c57150dd8fac6dab1c2c9cf6fdf7cefbdb1b5f8
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "62913592"
---
# <a name="mssqlserver_5231"></a>MSSQLSERVER_5231
    
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
  
  
