---
title: "Служба системы отслеживания измененных данных для Oracle компании Attunity | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 22ec8a5c-9550-4d38-8a4a-485ec3e53ea8
caps.latest.revision: 21
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 21
---
# Служба системы отслеживания измененных данных для Oracle компании Attunity
  Служба CDC Service для Oracle ― это служба Windows, которая просматривает журналы транзакций Oracle и регистрирует изменения выбранных таблиц Oracle в таблицах изменений [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Таблицы изменений SQL, где хранятся отслеженные изменения из базы данных Oracle, принадлежат к тому же типу, что и таблицы изменений, используемые в собственной системе отслеживания изменений [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Поэтому использовать эти изменения так же легко, как и изменения баз данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## Установка  
 Конструктор и служба системы отслеживания измененных данных Microsoft® для Oracle от Attunity для Microsoft SQL Server® 2016 находятся в составе пакета дополнительных компонентов SQL Server 2016. Скачать компоненты пакета дополнительных компонентов можно со страницы [Microsoft® SQL Server® 2016 Feature Pack](http://go.microsoft.com/fwlink/?LinkId=746297)(Пакет дополнительных компонентов Microsoft® SQL Server® 2016).  
  
 Службу CDC Service для Oracle можно установить на любой поддерживаемый компьютер с ОС Windows с доступом к исходным базам данных Oracle, изменения в которых отслеживаются, и к целевому экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], где находится целевая база данных CDC. Службе CDC Service не нужны локально установленные базы данных Oracle или [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , а только их поддерживаемые клиенты. Сведения о месте установки необходимых компонентов базы данных см. в подразделе **Предварительные требования базы данных** в этом разделе.  
  
 Установка службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CDC Service для Oracle помещает в выбранном месте графический интерфейс пользователя для настройки службы и служебную программу. Служба CDC Service для Oracle настраивается отдельно с помощью консоли конфигурации службы Oracle CDC. Дополнительные сведения о настройке службы Oracle CDC Service см. в разделе [Change Data Capture Service for Oracle by Attunity F1 Help](../../integration-services/change-data-capture/change-data-capture-service-for-oracle-by-attunity-f1-help.md).  
  
 Службу CDC Service для Oracle можно установить на любой поддерживаемый компьютер с ОС Windows, на котором установлен собственный клиент Native Client [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ; он не обязательно должен быть установлен на том же компьютере, что и целевая база данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## Поддерживаемые среды Windows  
 Служба системы отслеживания измененных данных для Oracle от Attunity может работать в следующих средах Windows:  
  
-   Windows Vista с пакетом обновления 2 (SP2)  
  
-   Windows 7  
  
-   Windows 8 и 8.1  
  
-   Windows 10  
  
-   Windows Server 2008 R2  
  
-   Windows Server 2008 с пакетом обновления 2 (SP2)  
  
-   Windows Server 2012  
  
## Предварительные условия базы данных  
 Для работы со службой CDC Service для Oracle следует установить программное обеспечения собственного клиента Native Client Oracle [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] . Это обязательный компонент, который нужно получить у Oracle и установить до установки службы Oracle CDC Service. Кроме того, необходимо установить клиент ODBC для SQL Server, используя процесс установки SQL Server.  
  
 Служба CDC для Oracle поддерживает следующие версии:  
  
### Исходная база данных Oracle  
  
-   База данных Oracle 11x, любая версия  
  
-   База данных Oracle 10x, любая версия  
  
-   База данных Oracle 10g, выпуск 2: 10.2.0.1-10.2.0.5 (пакет обновлений за апрель 2010 г.)  
  
-   База данных Oracle 11g, выпуск 1: 11.1.0.6-11.1.0.7 (пакет обновлений за сентябрь 2008 г.)  
  
-   База данных Oracle 11g, выпуск 2: 11.2.0.1-11.2.0.3 (пакет обновлений за сентябрь 2011 г.)  

-   База данных Oracle 12c в классической установке. (Многоклиентская установка не поддерживается.)  
  
### Целевая база данных SQL Server  
 Сведения о функциях, поддерживаемых различными выпусками [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], см. в статье [Возможности, поддерживаемые выпусками SQL Server 2016](../Topic/Features%20Supported%20by%20the%20Editions%20of%20SQL%20Server%202016.md).  
  
## Запуск программы установки  
 Чтобы установить службу CDC Service для Oracle, откройте мастер установки для используемой платформы Windows (32-/64-разрядной) и следуйте инструкциям на экране.  
  
## Удаление службы системы отслеживания измененных данных для Oracle от Attunity  
 Служба CDC Service для Oracle удаляется с помощью пункта панели управления «Программы и компоненты».  
  
 При удалении службы CDC Service созданные базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не удаляются. Для полного удаления этого средства нужно удалить базу данных MSXDBCDC и конкретные базы данных CDC, созданные в целевом экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , с которым производилась работа.  
  
 Если программное обеспечение службы CDC Service удаляется с одного компьютера и устанавливается на другой, нужно задать только следующие данные:  
  
-   Учетная запись службы  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и учетные данные  
  
-   Главный пароль  
  
 Все прочие определения хранятся в базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и доступны из предыдущей установки на другом компьютере.  
  
## В этой документации  
  
-   [Архитектура службы системы отслеживания измененных данных для Oracle компании Attunity](../../integration-services/change-data-capture/change-data-capture-service-for-oracle-by-attunity-system-architecture.md)  
  
-   [Служба CDC Oracle](../../integration-services/change-data-capture/the-oracle-cdc-service.md)  
  
-   [Справка F1 службы системы отслеживания измененных данных для Oracle компании Attunity](../../integration-services/change-data-capture/change-data-capture-service-for-oracle-by-attunity-f1-help.md)  
  
-   [Руководство по службе системы отслеживания измененных данных для Oracle компании Attunity](../../integration-services/change-data-capture/change-data-capture-service-for-oracle-by-attunity-how-to-guide.md)  
  
## См. также раздел  
 [Работа со службой CDC Oracle](../../integration-services/change-data-capture/working-with-the-oracle-cdc-service.md)  
  
  