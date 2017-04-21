---
title: "Выбор режима аутентификации | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.ins.instwizard.authenticationmode.f1
helpviewer_keywords:
- sa account
- authentication modes
- trusted connection
- SQL Server Installation Wizard, Authentication Mode page
- choose authentication mode
- authentication [SQL Server], choosing a mode
- Windows authentication [SQL Server]
- mixed mode authentication
- mixed authentication mode
- SQL authentication mode
ms.assetid: ff7a6a48-3d38-4209-aa0f-7d6c0a8c64ef
caps.latest.revision: 45
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 0c13fbf9ffbe2337c1766d7a089c1d8072a17f77
ms.lasthandoff: 04/11/2017

---
# <a name="choose-an-authentication-mode"></a>Выбор режима проверки подлинности
  Во время процесса установки следует выбрать режим проверки подлинности для компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Существует два возможных режима: проверка подлинности Windows и смешанный режим. Режим проверки подлинности Windows включает проверку подлинности Windows и отключает проверку подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . В смешанном режиме включены как проверка подлинности Windows, так и проверка подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Проверка подлинности Windows доступна всегда, и отключить ее нельзя.  
  
## <a name="configuring-the-authentication-mode"></a>Настройка режима проверки подлинности  
 Если во время установки был выбран смешанный режим проверки подлинности, необходимо задать и подтвердить надежный пароль для встроенной учетной записи системного администратора [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с именем sa. Учетная запись sa устанавливает соединения с помощью проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Если во время установки была выбрана проверка подлинности Windows, программа установки создаст учетную запись sa для проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , но она будет отключена. Если позже переключиться на смешанный режим проверки подлинности и потребуется учетная запись sa, ее будет нужно включить. Любая учетная запись Windows или [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может быть настроена в качестве системного администратора. Поскольку учетная запись sa широко известна и часто является целью злонамеренных пользователей, ее не рекомендуется включать (за исключением тех случаев, когда это необходимо приложению). Никогда не указывайте пустой или простой пароль для учетной записи sa. Сведения о переключении проверки подлинности Windows на смешанный режим проверки подлинности и использовании проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] см. в статье [Изменение режима проверки подлинности сервера](../../database-engine/configure-windows/change-server-authentication-mode.md).  
  
## <a name="connecting-through-windows-authentication"></a>Соединение с использованием проверки подлинности Windows  
 Когда пользователь выполняет подключение под пользовательской учетной записью Windows, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверяет имя учетной записи и пароль с помощью токена участника Windows в операционной системе. Это означает, что удостоверение пользователя было подтверждено Windows. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не запрашивает пароль и не выполняет проверку удостоверения. Проверка подлинности Windows является проверкой подлинности по умолчанию; она обеспечивает более высокий уровень безопасности, чем проверка подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Режим проверки подлинности Windows использует протокол безопасности Kerberos, реализует политику паролей в отношении проверки сложности надежных паролей, поддерживает блокировку учетных записей и истечение срока пароля. Соединение, установленное с помощью проверки подлинности Windows, иногда называется доверительным соединением, поскольку [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] доверяет учетным данным, предоставляемым Windows.  
  
 С помощью проверки подлинности Windows можно создать группы Windows на уровне домена, а имя входа можно создать на уровне [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для всей группы. Управление доступом на уровне домена позволяет упростить администрирование учетных записей.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
## <a name="connecting-through-sql-server-authentication"></a>Соединение с использованием проверки подлинности SQL Server  
 Если используется проверка подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] создаются имена входа, которые не основаны на учетных записях пользователей Windows. И имя пользователя, и пароль создаются с помощью [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и хранятся в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Пользователи, подключающиеся с помощью проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , должны предоставлять свои учетные данные (имя входа и пароль) каждый раз при установке соединения. При использовании проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] необходимо задавать надежные пароли для всех учетных записей [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Рекомендации по выбору надежного пароля см. в разделе [Strong Passwords](../../relational-databases/security/strong-passwords.md).  
  
 Для имен входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] доступны три дополнительные политики паролей.  
  
-   Пользователь должен сменить пароль при следующем входе  
  
     Требует, чтобы пользователь сменил пароль при следующем подключении. Сменить пароль можно с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Если используется этот режим, сторонние разработчики программного обеспечения должны предоставлять данную функцию.  
  
-   Задать срок окончания действия пароля  
  
     Для имен входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] будет принудительно реализовываться политика максимального возраста паролей.  
  
-   Требовать использование политики паролей  
  
     Для имен входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] будут принудительно реализовываться политики паролей Windows. Это включает длину и сложность паролей. Эта возможность обеспечивается API `NetValidatePasswordPolicy` , который доступен только в [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] и более поздних версиях.  
  
#### <a name="to-determine-the-password-policies-of-the-local-computer"></a>Определение политик паролей на локальном компьютере  
  
1.  В меню **Пуск** выберите команду **Выполнить**.  
  
2.  В диалоговом окне **Выполнить** введите **secpol.msc**, а затем нажмите кнопку **ОК**.  
  
3.  В приложении **Локальная политика безопасности** разверните узлы **Настройки безопасности**и **Политики учетных записей**, затем щелкните **Политика паролей**.  
  
     Политики паролей будут описаны в панели результатов.  
  
### <a name="disadvantages-of-sql-server-authentication"></a>Недостатки проверки подлинности SQL Server  
  
-   Если пользователь является пользователем домена Windows, имеющим имя входа и пароль Windows, то для подключения он все равно должен предоставить другое имя входа и пароль ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]). Многим пользователям сложно помнить несколько имен входа и паролей. Необходимость предоставлять учетные данные [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] при каждом подключении к базе данных может раздражать.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не может использоваться протокол безопасности Kerberos.  
  
-   ОС Windows предоставляет дополнительные политики паролей, недоступные для имен входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Зашифрованный пароль имени входа для проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] необходимо передавать по сети во время установления соединения. Некоторые приложения, которые устанавливают соединение автоматически, сохраняют пароль на клиенте. Эти дополнительные точки, на которые может быть направлена атака.  
  
### <a name="advantages-of-sql-server-authentication"></a>Преимущества проверки подлинности SQL Server  
  
-   Позволяет [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживать более старые приложения и приложения, поставляемые сторонними производителями, для которых необходима проверка подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Позволяет [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживать среды с несколькими операционными системами, в которых пользователи не проходят проверку подлинности домена Windows.  
  
-   Позволяет пользователям устанавливать соединения из неизвестных или ненадежных доменов. Например, в приложении, в котором клиенты подключаются с выделенными именами входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , чтобы получить состояние их заказов.  
  
-   Позволяет [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживать веб-приложения, в которых пользователи сами создают собственные удостоверения.  
  
-   Позволяет разработчикам программного обеспечения распространять свои приложения с помощью сложной иерархии разрешений, основанной на известных, заранее установленных именах входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
    > [!NOTE]  
    >  Использование проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не ограничивает разрешения локальных администраторов на компьютере, на котором установлен [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="see-also"></a>См. также:  
 [Вопросы безопасности при установке SQL Server](../../sql-server/install/security-considerations-for-a-sql-server-installation.md)  
  
  
