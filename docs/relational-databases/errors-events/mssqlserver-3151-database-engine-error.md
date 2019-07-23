---
title: MSSQLSERVER_3151 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 3151 (Database Engine error)
ms.assetid: a8657a91-ec75-4649-a09a-21920e0030ff
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 068f4737a3367acdd01862cc800a4255a472c843
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68001916"
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
Проверьте журналы ошибок для получения дополнительных сведений. Чтобы создать работоспособную базу данных **master**, запустите файл Setup.exe с параметром REBUILDDATABASE. Дополнительные сведения см. в разделе "Как установить SQL Server из командной строки" в электронной документации по SQL Server.  
  
