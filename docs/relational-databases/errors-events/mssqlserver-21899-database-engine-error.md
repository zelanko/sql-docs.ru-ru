---
title: MSSQLSERVER_21899 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 21899 (Database Engine error)
ms.assetid: 32b87a7c-5380-4638-b147-dd78618f6625
caps.latest.revision: 6
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0d84ae2c0694616e9600dca72075dba6a0a8467c
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver21899"></a>MSSQLSERVER_21899
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|21899|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|SQLErrorNum21899|  
|Текст сообщения|Запрос на перенаправленном издателе "%s", для определения того, имеются ли на нем записи sysserver для подписчиков исходного издателя "%s", завершился с ошибкой "%d"; сообщение об ошибке: "%s".|  
  
## <a name="explanation"></a>Объяснение  
**sp_validate_redirected_publisher** запрашивает таблицы метаданных подписки в базе данных издателя на удаленном сервере, чтобы определить связанных с ним подписчиков. Если выполнить этот запрос не удается, возвращается ошибка 21899. Запросу проверки необходим доступ к опубликованной базе данных на перенаправленном издателе. Если имя входа, указанное при вызове хранимой процедуры **sp_adddistpublisher** для первоначального издателя, не имеет прав на доступ к опубликованной базе данных на перенаправленном издателе, возвращается ошибка 21899.  
  
## <a name="user-action"></a>Действие пользователя  
Просмотрите приведенное сообщение об ошибке, чтобы определить причину ошибки и предпринять соответствующие действия по ее исправлению  
  
