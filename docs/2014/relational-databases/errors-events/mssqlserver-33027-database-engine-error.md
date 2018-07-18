---
title: MSSQLSERVER_33027 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 33027 (Database Engine error)
ms.assetid: bfdc626e-7958-4511-987d-3b687824e8af
caps.latest.revision: 11
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 1f6ba0947d3966295e34c22f7069a1a31b9a6137
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37425363"
---
# <a name="mssqlserver33027"></a>MSSQLSERVER_33027
    
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
  
  
