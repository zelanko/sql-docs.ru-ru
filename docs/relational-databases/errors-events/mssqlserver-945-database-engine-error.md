---
title: MSSQLSERVER_945 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 945 (Database Engine error)
ms.assetid: ee501d13-0bd9-4627-896c-ed5b1bdb88b3
caps.latest.revision: 20
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 1670253eab7d92b07d8b5c1681d82c497be483e6
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2018
ms.locfileid: "34326355"
---
# <a name="mssqlserver945"></a>MSSQLSERVER_945
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|945|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|DB_IS_SHUTDOWN|  
|Текст сообщения|Не удалось открыть базу данных «%.*ls» вследствие недоступности файлов, нехватки памяти или места на диске.  Подробности см. в журнале ошибок SQL Server.|  
  
## <a name="explanation"></a>Объяснение  
Не удалось обратиться к базе данных из-за отсутствия файлов или других ресурсов.  
  
## <a name="user-action"></a>Действие пользователя  
Проверьте, нет ли в журнале ошибок дополнительных сведений об ошибках памяти, места на диске или разрешений. Проверьте местоположение MDF- и NDF-файлов этой базы данных и удостоверьтесь, что у учетной записи, используемой компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)], есть разрешения на доступ к этим файлам. После устранения неполадки перезапустите базу данных, установив параметр ONLINE в инструкции ALTER DATABASE.  
  
