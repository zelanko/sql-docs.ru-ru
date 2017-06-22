---
title: "Защита агента распространителя | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.rep.security.DA.f1
helpviewer_keywords:
- Distribution Agent Security dialog box
ms.assetid: de40cc21-2e58-4464-9be7-b5b90c925e9b
caps.latest.revision: 25
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 44bbfd608ad2511c95a872f07eac657ae7616e6d
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="distribution-agent-security"></a>Безопасность агента распространителя
  В диалоговом окне **Безопасность агента распространителя** можно указать учетную запись Windows, с которой будет работать агент распространителя. Агент распространителя работает на распространителе для принудительных подписок и на подписчике для подписок по запросу. Учетная запись [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows также называется *учетной записью процесса*, так как с этой учетной записью работает процесс агента. Дополнительные параметры в этом диалоговом окне зависят от метода доступа к нему.  
  
-   Если диалоговое окно открыто из мастера создания подписки, можно указать контекст, в котором агент распространителя устанавливает соединения с подписчиком (для принудительных подписок) или с распространителем (для подписок по запросу). Соединение может быть установлено путем олицетворения учетной записи Windows либо в контексте указанной учетной записи [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Если диалоговое окно открыто из диалогового окна **Свойства подписки** , то, чтобы определить контекст, в котором агент распространителя будет устанавливать соединение, нажмите кнопку свойств (**...**) в строке **Соединение с подписчиком** или **Соединение с распространителем** в этом диалоговом окне. Дополнительные сведения о доступе к диалоговому окну **Свойства подписки** см. в статьях [Просмотр и изменение свойств принудительной подписки](../../relational-databases/replication/view-and-modify-push-subscription-properties.md) и [Просмотр и изменение свойств подписки по запросу](../../relational-databases/replication/view-and-modify-pull-subscription-properties.md).  
  
 Все учетные записи должны быть допустимыми, а для каждой учетной записи должен быть указан правильный пароль. Учетные записи и пароли могут быть проверены только после запуска агента.  
  
## <a name="options"></a>Параметры  
 **Process Account**  
 Введите учетную запись Windows, с которой будет запускаться агент распространителя.  
  
-   Для принудительных подписок учетная запись должна удовлетворять следующим условиям:  
  
    -   Она должна быть как минимум членом предопределенной роли базы данных **db_owner** в базе данных распространителя.  
  
    -   Она должна входить в список доступа публикации (PAL).  
  
    -   Она должна иметь разрешение на чтение хранилища моментальных снимков.  
  
    -   Она должна иметь разрешение на чтение каталога, в который был установлен поставщик OLE DB для подписчика, если подписка предназначена для подписчика, не являющегося[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Для принудительных подписок эта учетная запись должна как минимум быть членом предопределенной роли базы данных **db_owner** в базе данных подписки.  
  
 Если при установке соединений производится олицетворение учетной записи процесса, требуются дополнительные разрешения. См. далее разделы **Соединение с распространителем** и **Соединение с подписчиком** .  
  
 Для подписок по запросу**** нельзя указать [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], because the Distribution Agent does not run on instances of [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)].  
  
 **Пароль** и **Подтверждение пароля**  
 Введите пароль для учетной записи Windows.  
  
 **Соединение с распространителем**  
 Для принудительных подписок соединение с распространителем всегда устанавливается путем олицетворения учетной записи, указанной в текстовом поле **Учетная запись процесса** .  
  
 Для подписок по запросу необходимо выбрать способ установки соединения между агентом распространителя и распространителем: путем олицетворения учетной записи, указанной в текстовом поле **Учетная запись процесса** , либо при помощи учетной записи [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Если выбрано использование учетной записи [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , введите имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и пароль.  
  
> [!NOTE]  
>  Рекомендуется использовать олицетворение учетной записи Windows вместо учетной записи [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Учетная запись Windows или учетная запись [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , которые используются для соединения, должны удовлетворять следующим условиям.  
  
-   Она должна входить в список доступа к публикации.  
  
-   Она должна иметь разрешение на чтение хранилища моментальных снимков.  
  
 **Соединение с подписчиком**  
 Для подписок по запросу соединения с подписчиком всегда устанавливаются с помощью олицетворения учетной записи, указанной в текстовом поле **Учетная запись процесса** .  
  
 Для подписок по запросу параметры для подписчиков [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и для подписчиков, не являющихся[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , отличаются.  
  
-   Для подписчиков [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] необходимо выбрать способ соединения агента распространения и подписчика путем олицетворения учетной записи, указанной в текстовом поле **Учетная запись процесса** , либо при помощи учетной записи [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Если выбрано использование учетной записи [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , введите имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и пароль.  
  
    > [!NOTE]  
    >  Рекомендуется использовать олицетворение учетной записи Windows вместо учетной записи [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
     Учетная запись Windows или учетная запись [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , которые используются для соединения с подписчиком, должны по меньшей мере быть членами предопределенной роли базы данных **db_owner** в базе данных подписки.  
  
-   Для подписчиков, не являющихся[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , на подписчике указывается имя входа в базу данных, используемое для соединения агента распространителя с подписчиком. Имя входа должно иметь необходимые разрешения для создания объектов в базе данных подписки. Дополнительные сведения о настройке подписчиков, отличных от подписчиков [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], см. в [этой статье](../../relational-databases/replication/create-a-subscription-for-a-non-sql-server-subscriber.md).  
  
 **Дополнительные параметры соединения**  
 Только для подписчиков, не являющихся[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Укажите любые параметры соединения для подписчика в виде строки соединения (для Oracle дополнительные параметры не нужны). Параметры разделяются точками с запятой. Ниже приведен пример строки соединения IBM DB2 (переносы строк использованы для удобства чтения):  
  
```  
Provider=DB2OLEDB;Initial Catalog=MY_SUBSCRIBER_DB;Network Transport Library=TCP;Host CCSID=1252;  
PC Code Page=1252;Network Address=MY_SUBSCRIBER;Network Port=50000;Package Collection=MY_PKGCOL;  
Default Schema=MY_SCHEMA;Process Binary as Character=False;Units of Work=RUW;DBMS Platform=DB2/NT;  
Persist Security Info=False;Connection Pooling=True;  
```  
  
 Большая часть параметров в строке зависят от настраиваемого сервера DB2, но параметр **Обрабатывать двоичное значение как символ** всегда должен иметь значение **False**. Параметр **Исходный каталог** должен иметь значение для идентификации базы данных подписки. Дополнительные сведения см. в статье [IBM DB2 Subscribers](../../relational-databases/replication/non-sql/ibm-db2-subscribers.md).  
  
## <a name="see-also"></a>См. также:  
 [Управление именами для входа и паролями при репликации](../../relational-databases/replication/security/manage-logins-and-passwords-in-replication.md)   
 [Модель безопасности агента репликации](../../relational-databases/replication/security/replication-agent-security-model.md)   
 [Обзор агентов репликации](../../relational-databases/replication/agents/replication-agents-overview.md)   
 [Рекомендации по защите репликации](../../relational-databases/replication/security/replication-security-best-practices.md)   
 [Подписка на публикации](../../relational-databases/replication/subscribe-to-publications.md)  
  
  
