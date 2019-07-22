---
title: Использование мастера добавления реплики Azure (SQL Server) | Документы Майкрософт
ms.custom: ''
ms.date: 05/17/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql13.swb.addreplicawizard.azurereplica.f1
ms.assetid: b89cc41b-07b4-49f3-82cc-bc42b2e793ae
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 88a5a995449e04d4d3dc78ca6b16b1fed007b140
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68013592"
---
# <a name="use-the-add-azure-replica-wizard-sql-server"></a>Использование мастера добавления реплики Azure (SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Использование мастера добавления реплики Azure для создания новой виртуальной машины Microsoft Azure в гибридной ИТ-среде и настройки ее в качестве вторичной реплики для новой или существующей группы доступности AlwaysOn.  
  

##  <a name="BeforeYouBegin"></a> Перед началом  
 Если вам еще не приходилось добавлять реплики доступности в группу доступности, см. подразделы "Экземпляры сервера" и "Группы доступности и реплики" в разделе [Предварительные требования, ограничения и рекомендации для групп доступности AlwaysOn (SQL Server)](../../../database-engine/availability-groups/windows/prereqs-restrictions-recommendations-always-on-availability.md).  
  
##  <a name="Prerequisites"></a> Предварительные требования  
  
-   Необходимо подключиться к экземпляру сервера, на котором размещена текущая первичная реплика.  
  
-   Необходимо установить гибридную ИТ-среду, в которой локальная подсеть напрямую связана через виртуальную частную сеть с Windows Azure. Дополнительные сведения см. в разделе [Настройка виртуальной частной сети между площадками через портал управления](https://azure.microsoft.com/documentation/articles/vpn-gateway-site-to-site-create).  
  
-   Группа доступности должна содержать реплики доступности локально.  
  
-   Клиенты прослушивателя группы доступности должны иметь подключение к Интернету, если им нужно поддерживать соединение с прослушивателем при переключении группы доступности на реплику Windows Azure.  
  
-   **Предварительные условия для использования полной начальной синхронизации данных** Необходимо указать сетевой ресурс, чтобы мастер мог создавать и получать доступ к резервным копиям. Для каждой первичной реплики учетная запись, используемая для запуска [!INCLUDE[ssDE](../../../includes/ssde-md.md)] , должна иметь разрешения в файловой системе на чтение и запись в общей сетевой папке. Для вторичных реплик учетная запись должна иметь разрешение на чтение в сетевой папке.  
  
     Если нет возможности воспользоваться мастером для выполнения полной первоначальной синхронизации данных, то базы данных-получатели нужно подготовить вручную. Это можно сделать до или после запуска мастера. Дополнительные сведения см. в статье [Ручная подготовка базы данных-получателя для присоединения к группе доступности (SQL Server)](../../../database-engine/availability-groups/windows/manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md).  
  
##  <a name="Permissions"></a> Permissions  
 Необходимо разрешение ALTER AVAILABILITY GROUP для группы доступности, разрешение CONTROL AVAILABILITY GROUP, разрешение ALTER ANY AVAILABILITY GROUP или разрешение CONTROL SERVER.  
  
 Кроме того, требуется разрешение CONTROL ON ENDPOINT, если мастер добавления реплики в группу доступности должен иметь возможность управлять конечной точкой зеркального отображения базы данных.  
  
##  <a name="SSMSProcedure"></a> Работа с мастером добавления реплики Azure (SQL Server Management Studio)  
 Мастер добавления реплики Azure можно запустить на странице [Выбор реплик](../../../database-engine/availability-groups/windows/specify-replicas-page-new-availability-group-wizard-add-replica-wizard.md). На эту страницу можно перейти двумя способами.  
  
-   [Использование мастера групп доступности (среда SQL Server Management Studio)](../../../database-engine/availability-groups/windows/use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   [Использование мастера добавления реплики в группу доступности (среда SQL Server Management Studio)](../../../database-engine/availability-groups/windows/use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)  
  
 После того как был запущен мастер добавления реплики Azure, выполните следующие шаги.  
  
1.  Сначала загрузите сертификат управления для подписки Windows Azure. Нажмите кнопку **Загрузить** , чтобы открыть страницу входа.  
  
2.  Войдите в Microsoft Azure, используя учетную запись Майкрософт или учетную запись вашей организации. Учетная запись Майкрософт или организации имеет формат адреса электронной почты, например "mailto:patc@contoso.com" patc@contoso.com. Дополнительные сведения об учетных данных Azure см. в разделах [Часто задаваемые вопросы об учетной записи Майкрософт для организаций](https://technet.microsoft.com/jj592903) и [Устранение проблем с входом при использовании учетной записи организации](https://support.microsoft.com/kb/2756852).  
  
3.  Затем подключитесь к подписке, нажав кнопку **Подключиться**. После подключения раскрывающиеся списки заполняются параметрами Microsoft Azure, такими как **Виртуальная сеть** и **Подсеть виртуальной сети**.  
  
4.  Укажите параметры для виртуальной машины Windows Azure, в которой будет размещена новая вторичная реплика.  
  
     image  
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
  
## <a name="see-also"></a>См. также:  
 [Обзор групп доступности AlwaysOn (SQL Server)](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Предварительные требования, ограничения и рекомендации для групп доступности AlwaysOn (SQL Server)](../../../database-engine/availability-groups/windows/prereqs-restrictions-recommendations-always-on-availability.md)   
 [Добавление вторичной реплики к группе доступности (SQL Server)](../../../database-engine/availability-groups/windows/add-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
  
