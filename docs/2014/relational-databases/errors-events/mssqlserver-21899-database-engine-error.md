---
title: MSSQLSERVER_21899 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 21899 (Database Engine error)
ms.assetid: 32b87a7c-5380-4638-b147-dd78618f6625
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d40ee92b98999cd6b88a469a02f290e68ca06559
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62915022"
---
# <a name="mssqlserver_21899"></a>MSSQLSERVER_21899
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|21899|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|SQLErrorNum21899|  
|Текст сообщения|Запрос на перенаправленном издателе "%s", для определения того, имеются ли на нем записи sysserver для подписчиков исходного издателя "%s", завершился с ошибкой "%d"; сообщение об ошибке: "%s".|  
  
## <a name="explanation"></a>Объяснение  
 
  `sp_validate_redirected_publisher` запрашивает таблицы метаданных подписки в базе данных издателя на удаленном сервере, чтобы определить связанных с ним подписчиков. Если выполнить этот запрос не удается, возвращается ошибка 21899. Запросу проверки необходим доступ к опубликованной базе данных на перенаправленном издателе. Если имя входа, указанное при вызове хранимой процедуры `sp_adddistpublisher` для первоначального издателя, не имеет прав на доступ к опубликованной базе данных на перенаправленном издателе, возвращается ошибка 21899.  
  
## <a name="user-action"></a>Действие пользователя  
 Просмотрите приведенное сообщение об ошибке, чтобы определить причину ошибки и предпринять соответствующие действия по ее исправлению  
  
  
