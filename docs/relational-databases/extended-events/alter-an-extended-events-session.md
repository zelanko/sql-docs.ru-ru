---
title: Изменение сеанса расширенных событий | Документация Майкрософт
ms.custom: ''
ms.date: 05/24/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xevents
ms.topic: tutorial
ms.assetid: 114ec05b-7eca-4c87-b276-25e37b84be39
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: cedb0addec5d6164b418b6bec0458de429dd6a82
ms.sourcegitcommit: 209fa6dafe324f606c60dda3bb8df93bcf7af167
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2019
ms.locfileid: "66198201"
---
# <a name="alter-an-extended-events-session"></a>Изменение сеанса расширенных событий

[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  После того как создан сеанс расширенных событий, его можно изменить необходимым образом с помощью **Мастера расширенных событий SQL Server**.  
  
## <a name="before-you-begin"></a>Перед началом работы  
 Нельзя изменять целевой объект для активных или неактивных сеансов, нельзя изменять настройки расширенных свойств для активного сеанса.  
  
 Можно вносить следующие изменения как в активные, так и в неактивные сеансы событий.  
  
-   Добавлять или удалять события, изменять настройки событий, например поля событий, фильтры и действия.  
  
-   Добавьте или удалите целевой объект из сеанса событий.  
  
-   Включите параметр **Запускать сеанс событий при запуске сервера** .  
  
 Можно вносить в неактивный сеанс событий следующие изменения.  
  
-   Включать параметр **Отслеживать связь между событиями** .  
  
-   Изменять конфигурацию расширенных свойств.  
  
> [!NOTE]  
>  В **мастере расширенных событий SQL Server** не поддерживается изменение сеансов событий.  
  
## <a name="how-to-alter-an-extended-events-session-using-the-sql-server-extended-events-wizard"></a>Как изменить сеанс расширенных событий с помощью мастера расширенных событий SQL Server  
  
-   В обозревателе объектов разверните **Управление**, **Расширенные события** и затем **Сеансы**.  
  
-   Щелкните правой кнопкой мыши сеанс, который нужно изменить, и выберите **Свойства**.  
  
-   В диалоговом окне **Свойства** внесите соответствующие изменения и нажмите кнопку **ОК**.  
  
## <a name="see-also"></a>См. также:  
 [ALTER EVENT SESSION (Transact-SQL)](../../t-sql/statements/alter-event-session-transact-sql.md)   
 [Создание сеанса расширенных событий с помощью редактора запросов](quick-start-extended-events-in-sql-server.md)  
  
  
