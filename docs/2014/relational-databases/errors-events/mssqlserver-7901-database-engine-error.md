---
title: MSSQLSERVER_7901 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7901 (Database Engine error)
ms.assetid: 2d0d19b9-947b-4474-9ff8-7e03019ab93d
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: faf43de11a0c1779f043c6dd854e361c0396dc6e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62913572"
---
# <a name="mssqlserver_7901"></a>MSSQLSERVER_7901
    
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
  
  
