---
title: Соединение с сервером, вкладка "Имя входа" (Oracle) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.rep.oracleconnection.login.f1
helpviewer_keywords:
- Connect to Server dialog box, replication
ms.assetid: 86ed91a1-a07c-46f2-a913-67317ef2255e
caps.latest.revision: 20
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 161d787ca55a949be2733223964c15754e157f90
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32954239"
---
# <a name="connect-to-server-oracle-login"></a>Диалоговое окно «Соединение с сервером (Oracle)», вкладка «Имя входа»
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Вкладка **Имя входа** диалогового окна **Соединение с сервером** используется для задания учетной записи, под которой будут осуществляться подключения распространителя [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] к издателю Oracle. Должна использоваться та же учетная запись, что и заданная для схемы пользователя-администратора репликации в процессе настройки издателя. Дополнительные сведения см. в статье [Настройка издателя Oracle](../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md).  
  
## <a name="options"></a>Параметры  
 **Экземпляр сервера**  
 Имя TNS (Transparent Network Substrate) издателя Oracle, заданное в процессе настройки клиентского программного обеспечения Oracle, установленного у распространителя.  
  
 **Проверка подлинности**  
 Для выбора доступны **Стандартная проверка подлинности Oracle** (рекомендуется) или **Проверка подлинности Windows**. Если выбрана **Проверка подлинности Windows**:  
  
-   Сервер Oracle должен быть настроен таким образом, чтобы принимать соединения, использующие учетные данные Windows. Дополнительные сведения см. в документации Oracle.  
  
-   Необходимо в данный момент находиться в системе под той же учетной записью [!INCLUDE[msCoName](../../includes/msconame-md.md)] , что и заданная в схеме пользователя-администратора репликации.  
  
 **Имя** и **Пароль**  
 Если выбрана **Стандартная проверка подлинности Oracle** в качестве параметра **Проверка подлинности** , необходимо задать имя и пароль, которые должны совпадать с заданными в схеме пользователя-администратора репликациями.  
  
## <a name="see-also"></a>См. также:  
 [Glossary of Terms for Oracle Publishing](../../relational-databases/replication/non-sql/glossary-of-terms-for-oracle-publishing.md)  
  
  
