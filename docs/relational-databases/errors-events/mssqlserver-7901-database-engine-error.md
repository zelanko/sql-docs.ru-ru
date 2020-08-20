---
description: MSSQLSERVER_7901
title: MSSQLSERVER_7901 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 7901 (Database Engine error)
ms.assetid: 2d0d19b9-947b-4474-9ff8-7e03019ab93d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b07f78159cc9f525255f28bdc2b9854dc0f41244
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88460930"
---
# <a name="mssqlserver_7901"></a>MSSQLSERVER_7901
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Сведения  
  
| attribute | Значение |  
| :-------- | :---- |  
|Название продукта|SQL Server|  
|Идентификатор события|7901|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|DBCC2_DATABASE_IN_EMERGENCY_MODE|  
|Текст сообщения|Инструкция восстановления не была обработана. Данный уровень восстановления не поддерживается, если база данных находится в аварийном режиме.|  
  
## <a name="explanation"></a>Объяснение  
База данных находится в аварийном режиме, но был задан уровень восстановления, отличный от REPAIR_ALLOW_DATA_LOSS. Восстановление не может выполняться в аварийном режиме, если не задан уровень REPAIR_ALLOW_DATA_LOSS.  
  
## <a name="user-action"></a>Действие пользователя  
Повторно выполните команду с параметром REPAIR_ALLOW_DATA_LOSS.  
  
