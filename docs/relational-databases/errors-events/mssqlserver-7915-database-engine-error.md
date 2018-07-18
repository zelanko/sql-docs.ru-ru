---
title: MSSQLSERVER_7915 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 7915 (Database Engine error)
ms.assetid: 63338587-7dd3-40e6-b70e-d8ae18fff47b
caps.latest.revision: 16
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 21c43e914c933463028e6815f698ee6c1c71a5de
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2018
ms.locfileid: "34324945"
---
# <a name="mssqlserver7915"></a>MSSQLSERVER_7915
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|7915|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|DBCC2_REPAIR_IAM_CHAIN_REBUILT|  
|Текст сообщения|Исправление: последовательность IAM для объекта с идентификатором O_ID, идентификатором индекса I_ID, идентификатором секции PN_ID, идентификатором единицы распределения A_ID (тип TYPE) была усечена до страницы P_ID и будет перестроена.|  
  
## <a name="explanation"></a>Объяснение  
Это информационное сообщение, отправляемое командой REPAIR, указывает на то, что определенная цепочка карты распределения индекса (IAM) была обновлена, поэтому ее можно перестроить. Для этого обновления, возможно, потребуется размещение нового заголовка IAM-цепочки или удаление из цепочки испорченных страниц.  
  
## <a name="user-action"></a>Действие пользователя  
None  
  
