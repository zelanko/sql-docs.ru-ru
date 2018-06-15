---
title: MSSQLSERVER_5554 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 5554 (Database Engine error)
ms.assetid: 7134bbe5-d240-4a98-85ce-b13cc8ae9b0e
caps.latest.revision: 12
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 91a7d362d82f7321cfd82046295a855a91ca8a29
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2018
ms.locfileid: "34324465"
---
# <a name="mssqlserver5554"></a>MSSQLSERVER_5554
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|MSSQLSERVER|  
|Идентификатор события|5554|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|FS_MINIVER_OVERFLOW|  
|Текст сообщения|Достигнут максимальный предел общего числа версий одного файла, установленный для файловой системы.|  
  
## <a name="explanation"></a>Объяснение  
В режиме MARS и скриптах триггера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использует мини-версию, указанную операционной системой.  
  
## <a name="user-action"></a>Действие пользователя  
Постарайтесь избежать повторного обновления данных в одной транзакции.  
  
