---
title: MSSQLSERVER_3169 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
f1_keywords:
- "3169"
helpviewer_keywords:
- 3169 (Database Engine error)
ms.assetid: 7d4dbed6-bb94-4908-bc03-2040a9cf63bc
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e5423db9123c3ffd991d5044de24208d4406ca95
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47682182"
---
# <a name="mssqlserver3169"></a>MSSQLSERVER_3169
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|3169|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|Н/Д|  
|Текст сообщения|Резервная копия базы данных создана на сервере, на котором выполняется версия %ls. Эта версия несовместима с данным сервером, на котором работает версия %ls. Необходимо восстановить базу данных на сервере, который поддерживает эту резервную копию, либо использовать резервную копию, совместимую с данным сервером.|  
  
## <a name="explanation"></a>Объяснение  
Некоторые особенности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] влияют на структуру файлов базы данных. При восстановлении базы данных на другом экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] файл форматирования может оказаться несовместимым с другой версией компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].  
  
Например, эта ошибка может возникнуть при использовании формата хранения vardecimal в более поздней версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с последующей попыткой восстановить файлы базы данных в более ранней версии, чем [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] с пакетом обновления 2 (SP2).  
  
## <a name="user-action"></a>Действие пользователя  
Определите версию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], запущенную на исходном сервере. В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] щелкните сервер правой кнопкой мыши и выберите **Свойства** либо введите **SELECT @@VERSION** в окне запроса. Откройте базу данных с помощью исходной версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Изучите функции, которые включены в исходной базе данных экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Измените параметры для работы с версией [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], в которой будет выполняться восстановление базы данных.  
  
