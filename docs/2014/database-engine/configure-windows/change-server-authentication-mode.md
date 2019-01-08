---
title: Изменение режима проверки подлинности сервера | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- sa account
- authentication [SQL Server], changing modes
- server authentication mode [SQL Server]
- modifying server authentication mode
ms.assetid: 79babcf8-19fd-4495-b8eb-453dc575cac0
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 43919e335700a23a4174eb1bdf42c36c0c08fe2f
ms.sourcegitcommit: 04dd0620202287869b23cc2fde998a18d3200c66
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/30/2018
ms.locfileid: "52641171"
---
# <a name="change-server-authentication-mode"></a>Изменение режима проверки подлинности сервера
  В этом разделе описывается, как изменить режим проверки подлинности сервера в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]. В процессе установки компонент [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] настраивается на использование **режима проверки подлинности Windows** или **режима проверки подлинности SQL Server и Windows**. После установки вы можете изменить режим проверки подлинности в любое время.  
  
 Если во время установки был выбран **Режим проверки подлинности Windows** , то имя входа sa отключено, а пароль присваивается программой установки. Если впоследствии изменить режим проверки подлинности на **проверку подлинности SQL Server и Windows**, то имя входа sa останется отключенным. Чтобы можно было пользоваться именем входа sa, включите его и присвойте ему новый пароль с помощью инструкции ALTER LOGIN. Имя входа sa может подключаться к серверу только с использованием проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [безопасность](#Security)  
  
-   **Изменение режима проверки подлинности сервера с помощью:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Security"></a> безопасность  
 Учетная запись sa — хорошо известная учетная запись [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и часто становится мишенью злоумышленников. Не включайте учетную запись sa, если это не требуется для работы приложения. Для имени входа sa очень важно использовать надежный пароль.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-change-security-authentication-mode"></a>Изменение режима проверки подлинности в целях безопасности  
  
1.  В обозревателе объектов среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] щелкните правой кнопкой мыши сервер и выберите пункт **Свойства**.  
  
2.  На странице **Безопасность** , в разделе **Серверная проверка подлинности**выберите новый режим проверки подлинности сервера, а затем нажмите кнопку **ОК**.  
  
3.  В диалоговом окне среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] нажмите кнопку **ОК** , чтобы подтвердить необходимость перезапуска [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
4.  В обозревателе объектов щелкните правой кнопкой мыши сервер и выберите пункт **Перезапустить**. Если работает агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , он тоже должен быть перезапущен.  
  
#### <a name="to-enable-the-sa-login"></a>Включение имени входа sa  
  
1.  В обозревателе объектов разверните **безопасности**, имена входа, щелкните правой кнопкой мыши `sa`, а затем нажмите кнопку **свойства**.  
  
2.  На странице **Общие** , возможно, придется создать и подтвердить пароль для имени входа.  
  
3.  На странице **Состояние** в разделе **Имя входа** щелкните **Включить**и нажмите кнопку **ОК**.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 **Включение имени входа sa**  
  
1.  В обозревателе объектов установите соединение с экземпляром компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В следующем примере включается имя входа sa и устанавливается новый пароль.  
  
    ```  
    ALTER LOGIN sa ENABLE ;  
    GO  
    ALTER LOGIN sa WITH PASSWORD = '<enterStrongPasswordHere>' ;  
    GO  
  
    ```  
  
## <a name="see-also"></a>См. также  
 [Надежные пароли](../../relational-databases/security/strong-passwords.md)   
 [Вопросы безопасности при установке SQL Server](../../sql-server/install/security-considerations-for-a-sql-server-installation.md)   
 [ALTER LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-login-transact-sql)   
 [Подключение к SQL Server в случае, если доступ системных администраторов заблокирован](connect-to-sql-server-when-system-administrators-are-locked-out.md)  
  
  
