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
ms.openlocfilehash: d0d4c51bd7f4e1eca3bf57fbcfa89aec93357fb0
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85723740"
---
# <a name="mssqlserver_3151"></a>MSSQLSERVER_3151
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Сведения  
  
| attribute | Значение |  
| :-------- | :---- |  
|Название продукта|SQL Server|  
|Идентификатор события|3151|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|LDDB_MASTER_LOAD_FAILED|  
|Текст сообщения|Ошибка при восстановлении базы данных master. Завершение работы SQL Server. Проверьте журналы ошибок и перестройте базу данных master. Дополнительные сведения о перестроении базы данных master см. в электронной документации по SQL Server.|  
  
## <a name="explanation"></a>Объяснение  
Это общее сообщение об ошибке, которое может означать разные проблемы с базой данных **master**.  
  
## <a name="user-action"></a>Действие пользователя  
Проверьте журналы ошибок для получения дополнительных сведений. Чтобы создать работоспособную базу данных **master**, запустите файл Setup.exe с параметром REBUILDDATABASE. Дополнительные сведения см. в разделе "Как установить SQL Server из командной строки" в электронной документации по SQL Server.  
  
