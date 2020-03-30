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
ms.openlocfilehash: 3bb511fcfc62d2175721b68cf0c8bf554f1b54b7
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "68056593"
---
# <a name="mssqlserver_21899"></a>MSSQLSERVER_21899
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
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
**sp_validate_redirected_publisher** запрашивает таблицы метаданных подписки в базе данных издателя на удаленном сервере, чтобы определить связанных с ним подписчиков. Если выполнить этот запрос не удается, возвращается ошибка 21899. Запросу проверки необходим доступ к опубликованной базе данных на перенаправленном издателе. Если имя входа, указанное при вызове хранимой процедуры **sp_adddistpublisher** для первоначального издателя, не имеет прав на доступ к опубликованной базе данных на перенаправленном издателе, возвращается ошибка 21899.  
  
## <a name="user-action"></a>Действие пользователя  
Просмотрите приведенное сообщение об ошибке, чтобы определить причину ошибки и предпринять соответствующие действия по ее исправлению  
  
