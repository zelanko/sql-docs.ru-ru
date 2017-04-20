---
title: "Соединение с сервером (страница &quot;Имя входа&quot;) службы Integration Services | Документация Майкрософт"
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
- sql13.swb.connecttodts.login.f1
- sql13.swb.connecttodtsserver.login.f1
ms.assetid: 402c2de4-f4ea-40b0-909f-3ddf3bd59950
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 18699131b8268dedfb0e47f05ec4032d81b498ef
ms.lasthandoff: 04/11/2017

---
# <a name="connect-to-server-login-page-integration-services"></a>Соединение с сервером (страница «Имя входа») службы Integration Services
Используйте эту вкладку для просмотра или задания следующих параметров при соединении со службами [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion_md.md)].  
  
## <a name="options"></a>Параметры  
**Тип сервера**  
При регистрации сервера из обозревателя объектов выберите тип сервера для подключения: [!INCLUDE[ssDE](../../includes/ssde_md.md)], службы Analysis Services, службы Reporting Services или службы Integration Services. В остальной части диалогового окна показаны параметры, которые применяются только к выбранному типу сервера. При регистрации сервера c панели "Зарегистрированные серверы" поле **Тип сервера** не может быть изменено и совпадает с типом сервера, показанного в компоненте "Зарегистрированные серверы". Чтобы зарегистрировать другой тип сервера, выберите компонент [!INCLUDE[ssDE](../../includes/ssde_md.md)], службы Analysis Services, службы Reporting Services или службы Integration Services на панели инструментов «Зарегистрированные серверы», прежде чем начать регистрацию нового сервера.  
  
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
  
**Запомнить пароль**  
Этот параметр недоступен, поскольку для служб [!INCLUDE[ssIS](../../includes/ssis_md.md)]возможен только режим проверки подлинности Windows.  
  
**Connect**  
Подключиться к выбранному выше серверу.  
  
**Параметры**  
Выберите этот пункт, чтобы изменить диалоговое окно и скрыть такие дополнительные параметры соединения сервера, как запоминание пароля.  
  

