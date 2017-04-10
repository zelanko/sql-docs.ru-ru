---
title: "Подключение к удаленному серверу служб Integration Services (службы SSIS Service) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "служба [службы Integration Services], удаленный экземпляр"
  - "службы Integration Services, подключение"
  - "службы Integration Services, удаленный экземпляр"
  - "служба [службы Integration Services], подключение"
ms.assetid: 9487aff1-44d8-42c1-8176-bb9891d4632d
caps.latest.revision: 42
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 40
---
# Подключение к удаленному серверу служб Integration Services (службы SSIS Service)
    
> [!IMPORTANT] В данном разделе описывается компонент [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] — служба Windows для управления пакетами служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] поддерживает эту службу для обеспечения обратной совместимости с более ранними версиями служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], на сервере служб Integration Services можно управлять пакетами.  
  
 Соединение с экземпляром служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] на удаленном сервере из среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или другого управляющего приложения требует определенного набора прав на сервере для пользователей этого приложения.  
  
> [!IMPORTANT] Для соединения непосредственно с экземпляром устаревшей версии службы Integration Service необходимо использовать версию SQL Server Management Studio (SSMS), соответствующую версии SQL Server, где выполняются службы Integration Services. Например, чтобы соединиться с устаревшей версией служб Integration Services, выполняющихся на экземпляре SQL Server 2016, необходимо использовать версию SSMS, выпущенную для SQL Server 2016. [Скачайте SQL Server Management Studio (SSMS)](https://msdn.microsoft.com/library/mt238290.aspx).
>
>  Чтобы управлять пакетами, которые хранятся на удаленном сервере, не нужно соединятся с экземпляром службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] на этом удаленном сервере. Вместо этого измените файл конфигурации для службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] таким образом, чтобы среда [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] отображала пакеты, хранимые на удаленном сервере. Дополнительные сведения см. в разделе [Настройка служб Integration Services (SSIS)](../../integration-services/service/configuring-the-integration-services-service-ssis-service.md).  
  
## Подключение к службам Integration Services на удаленном сервере  
  
#### Подключение к службам Integration Services на удаленном сервере  
  
1.  Откройте среду [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
2.  В меню **Файл**выберите пункт **Подключить к обозревателю объектов** , чтобы вывести диалоговое окно **Подключение к серверу** .  
  
3.  Выберите службы **Integration Services** в списке **Тип сервера** .  
  
4.  В текстовое поле **Имя сервера** введите имя сервера служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
    > [!NOTE]  
    >  Службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] не привязаны к экземпляру. Чтобы подключиться к службам, используется имя компьютера, на котором работают службы Integration Services.  
  
5.  Нажмите кнопку **Соединить**.  
  
> [!NOTE]  
>  В диалоговом окне **Выбор серверов** не отображаются удаленные экземпляры служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Кроме того, параметры, доступные на вкладке **Параметры подключения** диалогового окна **Подключение к серверу** , которое выводится при нажатии кнопки **Параметры** , неприменимо для подключения к службам [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
## Устранение ошибки «Доступ запрещен»  
 Если пользователь без достаточных прав пытается подключиться к экземпляру служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] на удаленном сервере, сервер отвечает сообщением об ошибке «Доступ запрещен». Этого сообщения об ошибке можно избежать, убедившись, что пользователи имеют нужные разрешения DCOM.  
  
#### Настройка прав для удаленных пользователей в Windows Server 2003 или Windows XP  
  
1.  Если пользователь не является членом группы локальных администраторов, добавьте его в группу «Пользователи DCOM». Это можно сделать в оснастке MMC "Управление компьютером" в меню **Администрирование**.  
  
2.  Откройте панель управления, дважды щелкните **Администрирование** и дважды щелкните **Службы компонентов**, чтобы запустить оснастку MMC "Службы компонентов".  
  
3.  Разверните узел **Службы компонентов** в левой части панели консоли. Разверните узел **Компьютеры** , разверните узел **Мой компьютер**и щелкните узел **Настройка DCOM** .  
  
4.  Выберите узел **Настройка DCOM** и в списке приложений, которые можно настроить, выберите SQL Server Integration Services 11.0.  
  
5.  Щелкните правой кнопкой мыши SQL Server Integration Services 11.0, а затем выберите пункт **Свойства**.  
  
6.  В диалоговом окне **Свойства SQL Server Integration Services 11.0** перейдите на вкладку **Безопасность** .  
  
7.  В разделе **Разрешения на запуск и активацию**выберите **Настройка**и щелкните **Изменить** , чтобы открыть диалоговое окно **Запуск разрешений** .  
  
8.  В диалоговом окне **Запуск разрешений** добавьте или удалите пользователей и присвойте соответствующие разрешения нужным пользователям и группам. Доступные разрешения: «Локальный запуск», «Удаленный запуск», «Локальная активация» и «Удаленная активация». Права запуска предоставляют или отказывают в разрешении запускать и останавливать службы, права активации предоставляют или отказывают в разрешении подключаться к службе.  
  
9. Нажмите кнопку «OК», чтобы закрыть диалоговое окно.  
  
10. В разделе **Разрешения доступа**повторите шаги 7 и 8, чтобы назначить соответствующие разрешения пользователям и группам.  
  
11. Закройте оснастку MMC.  
  
12. Перезапустите службу [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
#### Настройка прав для удаленных пользователей в Windows 2000 с последними пакетами обновления  
  
1.  Запустите программу **dcomcnfg.exe** из командной строки.  
  
2.  На странице **Приложения** диалогового окна **Свойства конфигурации DCOM** выберите приложение SQL Server Integration Services 11.0 и щелкните **Свойства**.  
  
3.  Перейдите на страницу **Безопасность** .  
  
4.  В двух разных диалоговых окнах настройте **Разрешения на доступ** и **Разрешения на запуск**. Нельзя различить удаленный и локальный доступ: права на доступ включают локальный и удаленный доступ, а права на запуск включают локальный и удаленный запуск.  
  
5.  Закройте диалоговые окна и программу **dcomcnfg.exe**.  
  
6.  Перезапустите службу [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
## Подключение с использованием локальной учетной записи  
 При работе с локальной учетной записью Windows на клиентском компьютере можно подключиться к службе [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] на удаленном компьютере, только если локальная учетная запись имеет то же самое имя пользователя и пароль, а на удаленном компьютере имеются соответствующие права.  
  
## По умолчанию службы SSIS не поддерживают делегирование  
Службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] не поддерживают делегирование учетных данных, которое иногда называют двойным прыжком. В этом сценарии вы работаете на клиентском компьютере, службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] выполняются на втором компьютере, а [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] запущен на третьем. Сначала среда [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] успешно отправляет учетные записи с клиентского компьютера на второй компьютер, где запущены службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Однако затем службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] не могут передать учетные данные со второго компьютера на третий, где работает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].

Можно включить делегирование учетных данных, предоставив право **Доверять этому пользователю делегирование служб (только Kerberos)** учетной записи службы SQL Server, которая запускает службы Integration Services (ISServerExec.exe) в качестве дочернего процесса. Прежде чем предоставить это право, определите, соответствует ли это требованиям безопасности организации.

Дополнительные сведения см. в разделе [Getting Cross Domain Kerberos and Delegation working with SSIS Package](https://blogs.msdn.microsoft.com/psssql/2014/06/26/getting-cross-domain-kerberos-and-delegation-working-with-ssis-package/) (Обеспечение междоменной работы Kerberos и делегирования с помощью пакета SSIS).
  
## См. также  
 [Настройка параметров брандмауэра Windows для доступа к службам SSIS](../../integration-services/service/configure-a-windows-firewall-for-access-to-the-ssis-service.md)  
  
  