---
title: MSSQLSERVER_611 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 611 (Database Engine error)
ms.assetid: ac6a213f-5c38-44ad-bc85-a62863786614
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 16f0a8de9e55759e78c8fd2cd136ff4db3a677a8
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62734988"
---
# <a name="mssqlserver611"></a>MSSQLSERVER_611
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|611|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|VAR_SIZE_TOO_BIG|  
|Текст сообщения|Не удается добавить или обновить строку, поскольку суммарный размер переменных столбцов с учетом дополнительной памяти превысил допустимый на %d байт.|  
  
## <a name="explanation"></a>Объяснение  
Максимальный размер переменного столбца превышает размер, определенный схемой. Ошибка 611 возвращается при превышении размера столбца переменной, когда разрешен формат хранения vardecimal, либо если его размер превышает максимально допустимый в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] для записи со сжатием данных.  
  
## <a name="user-action"></a>Действие пользователя  
Уменьшите размер записи.  
  
