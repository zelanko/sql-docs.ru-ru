---
title: MSSQLSERVER_33027 | Документация Майкрософт
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
- 33027 (Database Engine error)
ms.assetid: bfdc626e-7958-4511-987d-3b687824e8af
caps.latest.revision: 11
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 71600394f3d89883414dd6ae8f7a34494ad3d173
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver33027"></a>MSSQLSERVER_33027
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|33027|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|SEC_CRYPTOPROV_CANTLOADDLL|  
|Текст сообщения|Не удалось загрузить поставщик служб шифрования "%.*ls" из-за недействительной подписи Authenticode или недействительного пути к файлу. Проверьте наличие других ошибок в предыдущих сообщениях.|  
  
## <a name="explanation"></a>Объяснение  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не смог использовать поставщик служб шифрования, указанный в сообщении об ошибке, так как [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не смог загрузить DLL-библиотеку. Недействительное имя или подпись Authenticode.  
  
## <a name="user-action"></a>Действие пользователя  
Проверьте, что файл присутствует, а [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имеет разрешение на доступ к местоположению файла. Проверьте дополнительные связанные сообщения в журнале ошибок. Или обратитесь к поставщику служб шифрования за дополнительными сведениями.  
  
