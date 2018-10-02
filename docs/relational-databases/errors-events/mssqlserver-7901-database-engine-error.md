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
manager: craigg
ms.openlocfilehash: d3eeee976a45817b155c86ae99bd2cbd229324d5
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47601082"
---
# <a name="mssqlserver7901"></a>MSSQLSERVER_7901
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|7901|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|DBCC2_DATABASE_IN_EMERGENCY_MODE|  
|Текст сообщения|Инструкция восстановления не была обработана. Данный уровень восстановления не поддерживается, если база данных находится в аварийном режиме.|  
  
## <a name="explanation"></a>Объяснение  
База данных находится в аварийном режиме, но был задан уровень восстановления, отличный от REPAIR_ALLOW_DATA_LOSS. Восстановление не может выполняться в аварийном режиме, если не задан уровень REPAIR_ALLOW_DATA_LOSS.  
  
## <a name="user-action"></a>Действие пользователя  
Повторно выполните команду с параметром REPAIR_ALLOW_DATA_LOSS.  
  
