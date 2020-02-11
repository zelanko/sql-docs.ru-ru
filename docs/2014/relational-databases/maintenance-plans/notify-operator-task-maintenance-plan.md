---
title: Задача уведомления оператора (план обслуживания) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.notifyoperator.f1
helpviewer_keywords:
- Notify Operator Task dialog box
ms.assetid: 39c0797c-ad2b-4591-85c9-a23a7f902895
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 0ef94ed9e296c588b70789ace0bbbbe79bc8008f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68205963"
---
# <a name="notify-operator-task-maintenance-plan"></a>Задача уведомления оператора (план обслуживания)
  Диалоговое окно **Задача уведомления оператора** используется для добавления автоматического уведомления к данному плану обслуживания. Для использования этой задачи необходимо, чтобы Database Mail включены и правильно настроены с msdb в качестве базы данных обслуживания почты, а [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] также иметь оператор агента с допустимым адресом электронной почты.  
  
 Данная задача использует хранимую процедуру sp_notify_operator.  
  
## <a name="options"></a>Параметры  
 **Соединен**  
 Выберите соединение с сервером, которое будет использоваться для выполнения этой задачи.  
  
 **Создать**  
 Создать новое соединение с сервером для его использования при выполнении этой задачи. Диалоговое окно **Создание соединения** описано ниже.  
  
 **Уведомления операторов**  
 Указать получателя электронного письма.  
  
 **Тема сообщения уведомления**  
 Укажите текст для строки темы в сообщении уведомления.  
  
 **Текст сообщения уведомления**  
 Укажите текст сообщения уведомления.  
  
 **Просмотреть T-SQL**  
 Просмотрите инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] , выполняемые для данной задачи по отношению к серверу, на основе выбранных параметров.  
  
> [!NOTE]  
>  Если количество затронутых объектов велико, построение этого отображения может занять значительное время.  
  
## <a name="new-connection-dialog-box"></a>Диалоговое окно «Создание соединения»  
 **Имя подключения**  
 Введите имя нового соединения.  
  
 **Выберите или введите имя сервера**  
 Выберите сервер для подключения при выполнении этой задачи.  
  
 **Обновить**  
 Обновите список доступных серверов.  
  
 **Введите данные для входа на сервер**  
 Укажите способ проверки подлинности на сервере.  
  
 **Использовать встроенную безопасность Windows**  
 Подключитесь к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] с использованием [!INCLUDE[msCoName](../../includes/msconame-md.md)] проверки подлинности Windows.  
  
 **Использовать указанные имя пользователя и пароль**  
 Соединение с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] компонента с использованием [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверки подлинности. Этот параметр недоступен.  
  
 **User name**  
 Укажите имя входа, используемое при проверке подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Этот параметр недоступен.  
  
 **Пароль**  
 Укажите используемый при проверке подлинности пароль. Этот параметр недоступен.  
  
## <a name="see-also"></a>См. также:  
 [Database Mail](../database-mail/database-mail.md)   
 [sp_notify_operator &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-notify-operator-transact-sql)  
  
  
