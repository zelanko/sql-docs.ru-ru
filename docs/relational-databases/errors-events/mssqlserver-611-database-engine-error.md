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
ms.openlocfilehash: c54c9e2f5e0e3d0a640935d80f22537a96876903
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67903915"
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
  
