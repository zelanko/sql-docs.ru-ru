---
description: MSSQLSERVER_5231
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
ms.openlocfilehash: 634b525a3daa2b5ac83a759c89c8edd52eb5ca6d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88471050"
---
# <a name="mssqlserver_5231"></a>MSSQLSERVER_5231
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Сведения  
  
| attribute | Значение |  
| :-------- | :---- |  
|Название продукта|SQL Server|  
|Идентификатор события|5231|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|DBCC4_DEADLOCK_SKIPPED_OBJECT|  
|Текст сообщения|Объект с идентификатором O_ID (объект "имя_объекта"): произошла взаимоблокировка при попытке заблокировать данный объект для проверки. Этот объект пропущен и останется необработанным.|  
  
## <a name="explanation"></a>Объяснение  
Произошла взаимоблокировка при попытке команды DBCC заблокировать объект, команда DBCC была выбрана жертвой взаимоблокировки. Объект не будет обработан.  
  
## <a name="user-action"></a>Действие пользователя  
None  
  
