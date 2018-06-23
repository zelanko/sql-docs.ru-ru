---
title: Соединение с сервером, вкладка "Имя входа" (Oracle) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.rep.oracleconnection.login.f1
helpviewer_keywords:
- Connect to Server dialog box, replication
ms.assetid: 86ed91a1-a07c-46f2-a913-67317ef2255e
caps.latest.revision: 19
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: e5170f517b3ae8e16103e8b0fa6ccbea5505c078
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36180245"
---
# <a name="connect-to-server-oracle-login"></a>Диалоговое окно «Соединение с сервером (Oracle)», вкладка «Имя входа»
  Вкладка **Имя входа** диалогового окна **Соединение с сервером** используется для задания учетной записи, под которой будут осуществляться подключения распространителя [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] к издателю Oracle. Должна использоваться та же учетная запись, что и заданная для схемы пользователя-администратора репликации в процессе настройки издателя. Дополнительные сведения см. в статье [Настройка издателя Oracle](non-sql/configure-an-oracle-publisher.md).  
  
## <a name="options"></a>Параметры  
 **Экземпляр сервера**  
 Имя TNS (Transparent Network Substrate) издателя Oracle, заданное в процессе настройки клиентского программного обеспечения Oracle, установленного у распространителя.  
  
 **Проверка подлинности**  
 Для выбора доступны **Стандартная проверка подлинности Oracle** (рекомендуется) или **Проверка подлинности Windows**. Если выбрана **Проверка подлинности Windows**:  
  
-   Сервер Oracle должен быть настроен таким образом, чтобы принимать соединения, использующие учетные данные Windows. Дополнительные сведения см. в документации Oracle.  
  
-   Необходимо в данный момент находиться в системе под той же учетной записью [!INCLUDE[msCoName](../../includes/msconame-md.md)] , что и заданная в схеме пользователя-администратора репликации.  
  
 **Имя** и **Пароль**  
 Если выбрана **Стандартная проверка подлинности Oracle** в качестве параметра **Проверка подлинности** , необходимо задать имя и пароль, которые должны совпадать с заданными в схеме пользователя-администратора репликациями.  
  
## <a name="see-also"></a>См. также  
 [Glossary of Terms for Oracle Publishing](non-sql/glossary-of-terms-for-oracle-publishing.md)  
  
  