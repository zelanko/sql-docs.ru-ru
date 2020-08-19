---
description: MSSQLSERVER_7915
title: MSSQLSERVER_7915 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 7915 (Database Engine error)
ms.assetid: 63338587-7dd3-40e6-b70e-d8ae18fff47b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6627ee24fc9b5f3e53334c8b085aef2698835e11
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88448736"
---
# <a name="mssqlserver_7915"></a>MSSQLSERVER_7915
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Сведения  
  
| attribute | Значение |  
| :-------- | :---- |  
|Название продукта|SQL Server|  
|Идентификатор события|7915|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|DBCC2_REPAIR_IAM_CHAIN_REBUILT|  
|Текст сообщения|Исправление: последовательность IAM для объекта с идентификатором O_ID, идентификатором индекса I_ID, идентификатором секции PN_ID, идентификатором единицы распределения A_ID (тип TYPE) была усечена до страницы P_ID и будет перестроена.|  
  
## <a name="explanation"></a>Объяснение  
Это информационное сообщение, отправляемое командой REPAIR, указывает на то, что определенная цепочка карты распределения индекса (IAM) была обновлена, поэтому ее можно перестроить. Для этого обновления, возможно, потребуется размещение нового заголовка IAM-цепочки или удаление из цепочки испорченных страниц.  
  
## <a name="user-action"></a>Действие пользователя  
None  
  
