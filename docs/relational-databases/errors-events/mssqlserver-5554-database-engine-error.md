---
title: MSSQLSERVER_5554 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 5554 (Database Engine error)
ms.assetid: 7134bbe5-d240-4a98-85ce-b13cc8ae9b0e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 20bfb8f859cbb6bfd1ca6a113556ff1f5902977a
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85728358"
---
# <a name="mssqlserver_5554"></a>MSSQLSERVER_5554
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Сведения  
  
| attribute | Значение |  
| :-------- | :---- |  
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
  
