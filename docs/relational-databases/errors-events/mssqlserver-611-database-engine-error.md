---
description: MSSQLSERVER_611
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
ms.openlocfilehash: 33076c77372ac62f154fbe5d3c60273447be99e9
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88470966"
---
# <a name="mssqlserver_611"></a>MSSQLSERVER_611
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Сведения  
  
| attribute | Значение |  
| :-------- | :---- |  
|Название продукта|SQL Server|  
|Идентификатор события|611|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|VAR_SIZE_TOO_BIG|  
|Текст сообщения|Не удается добавить или обновить строку, поскольку суммарный размер переменных столбцов с учетом дополнительной памяти превысил допустимый на %d байт.|  
  
## <a name="explanation"></a>Объяснение  
Максимальный размер переменного столбца превышает размер, определенный схемой. Ошибка 611 возвращается при превышении размера столбца переменной, когда разрешен формат хранения vardecimal, либо если его размер превышает максимально допустимый в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] для записи со сжатием данных.  
  
## <a name="user-action"></a>Действие пользователя  
Уменьшите размер записи.  
  
