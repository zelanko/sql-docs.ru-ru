---
title: "MSSQLSERVER_18452 | Документация Майкрософт"
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 18456 (Database Engine error)
- 18452 (Database Engine error)
ms.assetid: 21da332c-e81d-4dee-a9d2-95598911b3be
caps.latest.revision: 9
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 7e08452accd39507cc3124ff4a1dc22a073c01dd
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver18452"></a>MSSQLSERVER_18452
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|18452|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|LOGON_INVALID_CONNECT|  
|Текст сообщения|Ошибка входа пользователя «%.*ls». Данное имя входа является именем входа SQL Server и не может использоваться для аутентификации Windows.%.\*ls|  
  
## <a name="explanation"></a>Объяснение  
Пользователь попытался выполнить вход с учетными данными, правильность которых нельзя проверить. Возможные причины.  
  
-   Имя входа может быть именем входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], но сервер допускает только проверку подлинности Windows.  
  
-   Попытка подключения с использованием проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], но использованное имя входа не существует в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Процедура входа может использовать проверку подлинности Windows, но имя входа — неопознанный участник Windows. Неопознанный участник Windows означает, что имя входа не может быть проверено Windows. Причина может быть в том, что имя входа Windows принадлежит домену, который не является доверенным.  
  
Аналогичные неполадки могут вызвать менее определенную ошибку 18456.  
  
## <a name="user-action"></a>Действие пользователя  
При попытке подключения с использованием проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] убедитесь, что [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] настроен в режиме смешанной проверки подлинности.  
  
При попытке подключения с использованием проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] убедитесь, что имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] существует.  
  
При попытке подключения с использованием проверки подлинности Windows убедитесь, что выполнен правильный вход в нужный домен.  
  

