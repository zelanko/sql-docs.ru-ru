---
title: "Соединение с сервером (службы Analysis Services) | Документация Майкрософт"
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
- sql13.swb.connection.login.analysisserver.f1
ms.assetid: 7e277d22-8d4b-422e-8882-7c5dd7a6d915
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 73451189bc401a4167c65261f3adcc5aabb6627c
ms.contentlocale: ru-ru
ms.lasthandoff: 04/11/2017

---
# <a name="connect-to-server-analysis-services"></a>Соединение с сервером (службы Analysis Services)
Используйте это диалоговое окно для просмотра или задания параметров при соединении со службами [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion_md.md)].  
  
## <a name="options"></a>Параметры  
**Тип сервера**  
При регистрации сервера из обозревателя объектов выберите тип сервера для подключения: [!INCLUDE[ssDE](../../includes/ssde_md.md)], службы Analysis Services, службы Reporting Services или службы Integration Services. В остальной части диалогового окна показаны параметры, которые применяются только к выбранному типу сервера. При регистрации сервера c панели "Зарегистрированные серверы" поле **Тип сервера** не может быть изменено и совпадает с типом сервера, показанного в компоненте "Зарегистрированные серверы". Чтобы зарегистрировать другой тип сервера, выберите компонент [!INCLUDE[ssDE](../../includes/ssde_md.md)], службы Analysis Services, службы Reporting Services или службы Integration Services на панели инструментов «Зарегистрированные серверы», прежде чем начать регистрацию нового сервера.  
  
**Имя сервера**  
Выберите экземпляр сервера для подключения. По умолчанию выводится экземпляр сервера, к которому подключение выполнялось в последний раз.  
  
**Проверка подлинности**  
При подключении к экземпляру службы Analysis Services поддерживаются следующие режимы проверки подлинности: проверка подлинности [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows.  
  
**Режим проверки подлинности Windows (проверка подлинности Windows)**  
Режим**Проверка подлинности Windows** позволяет пользователю подключиться посредством учетной записи пользователя Windows.  
  
**Имя пользователя**  
Этот параметр недоступен в данном выпуске. Введите имя пользователя для соединения. Этот параметр доступен только в случае выбора режима **Проверка подлинности Windows**для подключения.  
  
**Пароль**  
Этот параметр недоступен в данном выпуске. Введите пароль для этого имени входа. Этот параметр доступен для редактирования только при подключении с проверкой подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] .  
  
**Connect**  
Нажмите, чтобы подключиться к выбранному выше серверу.  
  
**Параметры**  
Нажмите, чтобы вывести дополнительные параметры соединения с сервером, такие как регистрация сервера и запоминание пароля.  
  

