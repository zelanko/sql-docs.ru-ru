---
title: "Соединение с сервером (службы Integration Services) | Документация Майкрософт"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.connection.login.dtsserver.f1
ms.assetid: 5be897bd-f36c-4c6a-a91a-13d0d016f8b6
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 4d7f292d113fb3d9bc8197f7be3134524e8116af
ms.contentlocale: ru-ru
ms.lasthandoff: 04/11/2017

---
# <a name="connect-to-server-integration-services"></a>Соединение с сервером (службы Integration Services)
Используйте это диалоговое окно для просмотра или задания параметров при соединении со службами [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion_md.md)].  
  
## <a name="options"></a>Параметры  
**Тип сервера**  
При регистрации сервера из обозревателя объектов выберите тип сервера для подключения: [!INCLUDE[ssDE](../../includes/ssde_md.md)], службы Analysis Services, службы Reporting Services или службы Integration Services. В остальной части диалогового окна показаны параметры, которые применяются только к выбранному типу сервера. При регистрации сервера в окне «Зарегистрированные серверы» поле «Тип сервера» доступно только для чтения и соответствует типу сервера, который выводится в компоненте «Зарегистрированные серверы». Чтобы зарегистрировать другой тип сервера, выберите компонент [!INCLUDE[ssDE](../../includes/ssde_md.md)], службы Analysis Services, службы Reporting Services или службы Integration Services на панели инструментов «Зарегистрированные серверы», прежде чем начать регистрацию нового сервера.  
  
**Имя сервера**  
Выберите имя сервера для подключения. По умолчанию выводится экземпляр сервера, к которому подключение выполнялось в последний раз.  
  
> [!NOTE]  
> Не используйте синтаксис *<servername>*\\*<instancename>*, потому что службы [!INCLUDE[ssIS](../../includes/ssis_md.md)] не поддерживают работу с несколькими экземплярами на одном компьютере.  
  
**Проверка подлинности**  
Для служб [!INCLUDE[msCoName](../../includes/msconame_md.md)] доступна только проверка подлинности [!INCLUDE[ssIS](../../includes/ssis_md.md)]Windows. Режим проверки подлинности Windows позволяет подключаться с учетной записью Windows.  
  
**Имя пользователя**  
Этот параметр недоступен, поскольку для служб [!INCLUDE[ssIS](../../includes/ssis_md.md)]возможен только режим проверки подлинности Windows.  
  
**Пароль**  
Этот параметр недоступен, поскольку для служб [!INCLUDE[ssIS](../../includes/ssis_md.md)]возможен только режим проверки подлинности Windows.  
  
**Connect**  
Нажмите, чтобы подключиться к выбранному выше серверу.  
  
**Параметры**  
Нажмите, чтобы вывести дополнительные параметры соединения с сервером, такие как регистрация сервера и запоминание пароля.  
  

