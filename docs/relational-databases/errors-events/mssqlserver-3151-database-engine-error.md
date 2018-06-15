---
title: MSSQLSERVER_3151 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 3151 (Database Engine error)
ms.assetid: a8657a91-ec75-4649-a09a-21920e0030ff
caps.latest.revision: 17
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: fd312044fc5695818702f3c29bbfc77a46726a62
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2018
ms.locfileid: "34319676"
---
# <a name="mssqlserver3151"></a>MSSQLSERVER_3151
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|3151|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|LDDB_MASTER_LOAD_FAILED|  
|Текст сообщения|Ошибка при восстановлении базы данных master. Завершение работы SQL Server. Проверьте журналы ошибок и перестройте базу данных master. Дополнительные сведения о перестроении базы данных master см. в электронной документации по SQL Server.|  
  
## <a name="explanation"></a>Объяснение  
Это общее сообщение об ошибке, которое может означать разные проблемы с базой данных **master**.  
  
## <a name="user-action"></a>Действие пользователя  
Проверьте журналы ошибок для получения дополнительных сведений. Чтобы создать работоспособную базу данных **master**, запустите файл Setup.exe с параметром REBUILDDATABASE. Дополнительные сведения см. в статье электронной документации по SQL Server, посвященной установке SQL Server из командной строки.  
  
