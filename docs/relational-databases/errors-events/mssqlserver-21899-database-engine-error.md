---
title: MSSQLSERVER_21899 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 21899 (Database Engine error)
ms.assetid: 32b87a7c-5380-4638-b147-dd78618f6625
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5a45061cc2618407f375150cda4afe744f491c4e
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85780476"
---
# <a name="mssqlserver_21899"></a>MSSQLSERVER_21899
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Сведения  
  
| attribute | Значение |  
| :-------- | :---- |  
|Название продукта|SQL Server|  
|Идентификатор события|21899|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|SQLErrorNum21899|  
|Текст сообщения|Запрос на перенаправленном издателе "%s", для определения того, имеются ли на нем записи sysserver для подписчиков исходного издателя "%s", завершился с ошибкой "%d"; сообщение об ошибке: "%s".|  
  
## <a name="explanation"></a>Объяснение  
**sp_validate_redirected_publisher** запрашивает таблицы метаданных подписки в базе данных издателя на удаленном сервере, чтобы определить связанных с ним подписчиков. Если выполнить этот запрос не удается, возвращается ошибка 21899. Запросу проверки необходим доступ к опубликованной базе данных на перенаправленном издателе. Если имя входа, указанное при вызове хранимой процедуры **sp_adddistpublisher** для первоначального издателя, не имеет прав на доступ к опубликованной базе данных на перенаправленном издателе, возвращается ошибка 21899.  
  
## <a name="user-action"></a>Действие пользователя  
Просмотрите приведенное сообщение об ошибке, чтобы определить причину ошибки и предпринять соответствующие действия по ее исправлению  
  
