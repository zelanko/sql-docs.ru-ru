---
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
ms.openlocfilehash: 1a10e03f2dc09bb53078faaaaea36c60e313e0eb
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "67951561"
---
# <a name="mssqlserver_7901"></a>MSSQLSERVER_7901
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
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
  
