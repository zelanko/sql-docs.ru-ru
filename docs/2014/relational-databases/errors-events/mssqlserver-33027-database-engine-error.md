---
title: MSSQLSERVER_33027 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 33027 (Database Engine error)
ms.assetid: bfdc626e-7958-4511-987d-3b687824e8af
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b117743265ba0f993abfde19abaf873eb13ad8f5
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/21/2020
ms.locfileid: "86551719"
---
# <a name="mssqlserver_33027"></a>MSSQLSERVER_33027
    
## <a name="details"></a>Сведения  
  
|attribute|Значение|  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|33027|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|SEC_CRYPTOPROV_CANTLOADDLL|  
|Текст сообщения|Не удалось загрузить поставщик служб шифрования "%.*ls" из-за недействительной подписи Authenticode или недействительного пути к файлу. Проверьте наличие других ошибок в предыдущих сообщениях.|  
  
## <a name="explanation"></a>Объяснение  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не смог использовать поставщик служб шифрования, указанный в сообщении об ошибке, так как [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не смог загрузить DLL-библиотеку. Недействительное имя или подпись Authenticode.  
  
## <a name="user-action"></a>Действие пользователя  
 Проверьте, что файл присутствует, а [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имеет разрешение на доступ к местоположению файла. Проверьте дополнительные связанные сообщения в журнале ошибок. Или обратитесь к поставщику служб шифрования за дополнительными сведениями.  
  
  
