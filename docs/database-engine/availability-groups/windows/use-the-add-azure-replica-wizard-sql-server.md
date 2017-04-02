---
title: "Использование мастера добавления реплики Azure (SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "05/17/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.swb.addreplicawizard.azurereplica.f1"
ms.assetid: b89cc41b-07b4-49f3-82cc-bc42b2e793ae
caps.latest.revision: 12
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 12
---
# Использование мастера добавления реплики Azure (SQL Server)
  Использование мастера добавления реплики Azure для создания новой виртуальной машины Microsoft Azure в гибридной ИТ-среде и настройки ее в качестве вторичной реплики для новой или существующей группы доступности AlwaysOn.  
  
-   **Перед началом работы выполните следующие действия.**  
  
     [Предварительные требования](#Prerequisites)  
  
     [Безопасность](#Security)  
  
-   **Для добавления реплики воспользуйтесь инструкциями из раздела** [Мастер добавления реплики Azure (среда SQL Server Management Studio)](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
 Если вам еще не приходилось добавлять реплики доступности в группу доступности, см. подразделы "Экземпляры сервера" и "Группы доступности и реплики" в разделе [Предварительные требования, ограничения и рекомендации для групп доступности AlwaysOn (SQL Server)](../../../database-engine/availability-groups/windows/prereqs, restrictions, recommendations - always on availability.md).  
  
###  <a name="Prerequisites"></a> Предварительные требования  
  
-   Необходимо подключиться к экземпляру сервера, на котором размещена текущая первичная реплика.  
  
-   Необходимо установить гибридную ИТ-среду, в которой локальная подсеть напрямую связана через виртуальную частную сеть с Windows Azure. Дополнительные сведения см. в разделе [Настройка виртуальной частной сети между площадками через портал управления](https://azure.microsoft.com/en-us/documentation/articles/vpn-gateway-site-to-site-create).  
  
-   Группа доступности должна содержать реплики доступности локально.  
  
-   Клиенты прослушивателя группы доступности должны иметь подключение к Интернету, если им нужно поддерживать соединение с прослушивателем при переключении группы доступности на реплику Windows Azure.  
  
-   **Предварительные условия для использования полной начальной синхронизации данных** Необходимо указать сетевой ресурс, чтобы мастер мог создавать и получать доступ к резервным копиям. Для каждой первичной реплики учетная запись, используемая для запуска [!INCLUDE[ssDE](../../../includes/ssde-md.md)], должна иметь разрешения в файловой системе на чтение и запись в общей сетевой папке. Для вторичных реплик учетная запись должна иметь разрешение на чтение в сетевой папке.  
  
     Если нет возможности воспользоваться мастером для выполнения полной первоначальной синхронизации данных, то базы данных-получатели нужно подготовить вручную. Это можно сделать до или после запуска мастера. Дополнительные сведения см. в статье [Ручная подготовка базы данных-получателя для присоединения к группе доступности (SQL Server)](../../../database-engine/availability-groups/windows/manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md).  
  
###  <a name="Security"></a> Безопасность  
  
####  <a name="Permissions"></a> Разрешения  
 См. раздел [Security](../../../database-engine/availability-groups/windows/use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md#Security)  
  
##  <a name="SSMSProcedure"></a> Работа с мастером добавления реплики Azure (SQL Server Management Studio)  
 Мастер добавления реплики Azure можно запустить на странице [Выбор реплик](../../../database-engine/availability-groups/windows/specify-replicas-page-new-availability-group-wizard-add-replica-wizard.md). На эту страницу можно перейти двумя способами.  
  
-   [Использование мастера групп доступности (среда SQL Server Management Studio)](../../../database-engine/availability-groups/windows/use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   [Использование мастера добавления реплики в группу доступности (среда SQL Server Management Studio)](../../../database-engine/availability-groups/windows/use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)  
  
 После того как был запущен мастер добавления реплики Azure, выполните следующие шаги.  
  
1.  Сначала загрузите сертификат управления для подписки Windows Azure. Нажмите кнопку **Загрузить**, чтобы открыть страницу входа.  
  
2.  Войдите в Microsoft Azure, используя учетную запись Майкрософт или учетную запись вашей организации. Учетная запись Майкрософт или организации выглядит как адрес электронной почты в формате HYPERLINK "mailto:patc@contoso.com" patc@contoso.com. Дополнительные сведения об учетных данных Azure см. в разделах [Часто задаваемые вопросы об учетной записи Майкрософт для организаций](http://technet.microsoft.com/jj592903) и [Устранение проблем с входом при использовании учетной записи организации](https://support.microsoft.com/kb/2756852).  
  
3.  Затем подключитесь к подписке, нажав кнопку **Подключиться**. После подключения раскрывающиеся списки заполняются параметрами Microsoft Azure, такими как **Виртуальная сеть** и **Подсеть виртуальной сети**.  
  
4.  Укажите параметры для виртуальной машины Windows Azure, в которой будет размещена новая вторичная реплика.  
  
     Изображение  
     Имя образа SQL Server, которое будет использоваться для виртуальной машины Windows Azure  
  
     Размер виртуальной машины  
     Размер виртуальной машины Windows Azure  
  
     Имя виртуальной машины  
     Имя DNS виртуальной машины Windows Azure  
  
     Имя пользователя виртуальной машины  
     Имя входа администратора системы по умолчанию для виртуальной машины Windows Azure  
  
     Пароль администратора виртуальной машины (и подтверждение пароля)  
     Пароль для администратора по умолчанию для виртуальной машины Windows Azure  
  
     Виртуальная сеть  
     Виртуальная сеть, в которой будет размещена виртуальная машина Windows Azure  
  
     Подсеть виртуальной сети  
     Подсеть виртуальной сети, в которой будет размещена виртуальная машина Windows Azure  
  
     Домен  
     Домен Active Directory (AD), к которому будет присоединена виртуальная машина Windows Azure  
  
     Имя пользователя домена  
     Имя пользователя AD, используемое для присоединения виртуальной машины Windows Azure к домену  
  
     Пароль  
     Пароль, используемый для присоединения виртуальной машины Windows Azure к домену  
  
5.  Нажмите кнопку **ОК** , чтобы зафиксировать ваши параметры, и выйдите из мастера добавления реплики Azure.  
  
6.  Продолжайте выполнять остальные шаги конфигурации на странице [Выбор реплик](../../../database-engine/availability-groups/windows/specify-replicas-page-new-availability-group-wizard-add-replica-wizard.md) так же, как и для любых новых реплик.  
  
     После завершения работы с мастером группы доступности или с мастером добавления реплики в группу доступности процесс конфигурации выполняет все операции в Microsoft Azure, необходимые для создания новой виртуальной машины, присоединения ее к домену AD, добавлению в кластер Windows, включению высокой доступности AlwaysOn и добавлению новой реплики в группу доступности.  
  
##  <a name="RelatedTasks"></a> Связанные задачи  
  
-   [Добавление вторичной реплики к группе доступности (SQL Server)](../../../database-engine/availability-groups/windows/add-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
## См. также:  
 [Обзор групп доступности AlwaysOn (SQL Server)](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Предварительные требования, ограничения и рекомендации для групп доступности AlwaysOn (SQL Server)](../../../database-engine/availability-groups/windows/prereqs, restrictions, recommendations - always on availability.md)   
 [Добавление вторичной реплики к группе доступности (SQL Server)](../../../database-engine/availability-groups/windows/add-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
  