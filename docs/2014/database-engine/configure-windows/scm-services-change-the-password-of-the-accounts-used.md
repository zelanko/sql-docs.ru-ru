---
title: Изменение пароля учетных записей, используемых SQL Server (диспетчер конфигурации SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 01/07/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- expired password [SQL Server], SQL Server Agent
- passwords [SQL Server], SQL Server Agent service
- passwords [SQL Server], changing
- expired password [SQL Server], Database Engine
- passwords [SQL Server], SQL Server service
- Database Engine [SQL Server], passwords
- changing passwords used by SQL Server
- modifying passwords
ms.assetid: 5b6dcc03-6cae-45d3-acef-6f85ca6d615f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 1454e29835c0087fb75c93a1680f452dfe0f2c05
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84935091"
---
# <a name="change-the-password-of-the-accounts-used-by-sql-server-sql-server-configuration-manager"></a>Изменение пароля учетных записей, используемых SQL Server (диспетчер конфигурации SQL Server)
  В этом разделе описано, как менять пароль для учетных записей, используемых компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)] и агентом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , с помощью диспетчера конфигурации SQL Server. Компонент [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] и агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] запускаются на компьютере как службы, с заданными при установке учетными данными. Если экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] запускается с учетной записью домена, а пароль для этой учетной записи изменен, то пароль, используемый [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , необходимо обновить. Если этого не сделать, то [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может потерять доступ к некоторым ресурсам домена и, в случае остановки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , служба не перезапустится до тех пор, пока не будет обновлен пароль.  
  
 Сведения об изменении паролей для проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] см. в разделе [Срок действия пароля истек](../password-expired.md).  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] разработан для изменения параметров служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и обладает для этого всеми правами. Редактирование параметров службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в диспетчере управления службами Windows (**services.msc**) не всегда меняет все необходимые параметры, что может привести к неправильной работе службы. Однако в кластерной среде после изменения пароля на активном узле с помощью диспетчера конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] необходимо изменить пароль и на пассивном узле с помощью диспетчера управления службами.  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Для изменения пароля службы необходимо быть администратором компьютера.  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="SSMSProcedure"></a> Использование диспетчера конфигурации SQL Server  
  
#### <a name="to-change-the-password-used-by-the-sql-server-database-engine-service"></a>Изменение пароля службы SQL Server (компонент Database Engine)  
  
1.  Нажмите кнопку **Пуск** , укажите пункты **Все программы**, [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], **Средства настройки**и выберите пункт **Диспетчер конфигурации SQL Server**.  
  
    > [!NOTE]  
    >  Поскольку диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] является оснасткой консоли управления ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] ), а не изолированной программой, при работе в более новых версиях Windows диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не отображается как приложение.  
    >   
    >  -   **Windows 10**:  
    >          Чтобы открыть [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, на **начальной странице**введите SQLServerManager12. msc (для [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] ). Для предыдущих версий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] замените 12 на меньшее число. Если щелкнуть SQLServerManager12.msc, откроется диспетчер конфигурации. Чтобы закрепить Configuration Manager на начальной странице или на панели задач, щелкните правой кнопкой мыши SQLServerManager12. msc и выберите **открыть расположение файла**. В проводнике Windows щелкните правой кнопкой мыши файл SQLServerManager12. msc и выберите пункт **закрепить на** **панели задач или закрепить на**ней.  
    > -   **Windows 8**:  
    >          Чтобы открыть [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, во вложенном поле **Поиск** в разделе **приложения**введите **SQLServerManager \<version> . msc** , например `SQLServerManager12.msc` , и нажмите клавишу **Ввод**.  
  
2.  В диспетчере конфигурации SQL Server выберите пункт **Службы SQL Server**.  
  
3.  В области сведений щелкните правой кнопкой мыши **SQL Server (** \<instancename> **)** и выберите пункт **Свойства**.  
  
4.  В диалоговом окне свойства **SQL Server (** \<instancename> **)** на вкладке Вход в систему для учетной записи, указанной в поле **имя учетной записи** , введите новый пароль в полях **пароль** и **Подтверждение пароля** и нажмите кнопку **ОК**.  
  
     Новый пароль вступает в силу немедленно, без перезагрузки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
#### <a name="to-change-the-password-used-by-the-sql-server-agent-service"></a>Изменение пароля с помощью службы агента SQL Server  
  
1.  Нажмите кнопку **Пуск** , укажите пункты **Все программы**, [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], **Средства настройки**и выберите пункт **Диспетчер конфигурации SQL Server**.  
  
2.  В диспетчере конфигурации SQL Server выберите пункт **Службы SQL Server**.  
  
3.  В области сведений щелкните правой кнопкой мыши **Агент SQL Server (** \<instancename> **)** и выберите пункт **Свойства**.  
  
4.  В диалоговом окне свойства **Агент SQL Server (** \<instancename> **)** на вкладке Вход в систему для учетной записи, указанной в поле **имя учетной записи** , введите новый пароль в полях **пароль** и **Подтверждение пароля** и нажмите кнопку **ОК**.  
  
     На отдельном экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]пароль вступает в силу сразу же, без перезапуска [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. В кластеризованном экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может выключить ресурс [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , после чего потребуется перезапуск.  
  
## <a name="see-also"></a>См. также:  
 [Инструкции по управлению службами (диспетчер конфигурации SQL Server)](../managing-services-how-to-topics-sql-server-configuration-manager.md)  
  
  
