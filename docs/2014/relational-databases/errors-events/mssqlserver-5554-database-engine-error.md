---
title: MSSQLSERVER_5554 | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 5554 (Database Engine error)
ms.assetid: 7134bbe5-d240-4a98-85ce-b13cc8ae9b0e
caps.latest.revision: 11
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 1c7db414ef084b8117b93607e13d76ec128688db
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37423873"
---
# <a name="mssqlserver5554"></a>MSSQLSERVER_5554
    
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
  
  
