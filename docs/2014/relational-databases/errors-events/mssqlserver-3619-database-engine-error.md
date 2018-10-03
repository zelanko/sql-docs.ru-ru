---
title: MSSQLSERVER_3619 | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3619 (Database Engine error)
ms.assetid: 7d94f8d9-65ca-4fde-9c17-7b83e94a3779
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 6a82902d69a1d5214b29f43d19ded58c76293ec4
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48047385"
---
# <a name="mssqlserver3619"></a>MSSQLSERVER_3619
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|3619|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|SYS_NOLOG|  
|Текст сообщения|Нельзя сделать запись о контрольной точке в базе данных с идентификатором ID %d, поскольку закончилось место в журнале. Свяжитесь с администратором базы данных, чтобы он очистил журнал или выделил больше места для файлов журнала базы данных.|  
  
## <a name="explanation"></a>Объяснение  
 Не хватает места на диске для журнала транзакций.  
  
## <a name="user-action"></a>Действие пользователя  
 Выполните усечение журнала для освобождения места на диске или выделите дополнительное место для журнала. Дополнительные сведения см. в разделе «Устранение неполадок в полном журнале транзакций (ошибка 9002)» электронной документации по SQL Server 2005.  
  
  
